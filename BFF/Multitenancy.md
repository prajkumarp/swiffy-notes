I'll help you create a multi-tenant Backend-for-Frontend (BFF) using NestJS and TypeScript.



```typescript
// tenant.interface.ts
interface Tenant {
  id: string;
  name: string;
  database: string;
  apiKey?: string;
}

// tenant.context.ts
import { AsyncLocalStorage } from 'async_hooks';

export class TenantContext {
  private static context = new AsyncLocalStorage<Tenant>();

  static getCurrentTenant(): Tenant | undefined {
    return this.context.getStore();
  }

  static run(tenant: Tenant, next: () => Promise<any>) {
    return this.context.run(tenant, next);
  }
}

// tenant.middleware.ts
import { Injectable, NestMiddleware } from '@nestjs/common';
import { Request, Response, NextFunction } from 'express';
import { TenantService } from './tenant.service';
import { TenantContext } from './tenant.context';

@Injectable()
export class TenantMiddleware implements NestMiddleware {
  constructor(private readonly tenantService: TenantService) {}

  async use(req: Request, res: Response, next: NextFunction) {
    const tenantId = req.headers['x-tenant-id'] as string;
    
    if (!tenantId) {
      throw new Error('Tenant ID not provided');
    }

    const tenant = await this.tenantService.getTenantById(tenantId);
    
    if (!tenant) {
      throw new Error('Tenant not found');
    }

    await TenantContext.run(tenant, () => new Promise((resolve) => next(resolve)));
  }
}

// tenant.service.ts
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { Tenant } from './tenant.interface';

@Injectable()
export class TenantService {
  private tenants: Map<string, Tenant> = new Map();

  constructor(
    @InjectRepository(TenantEntity)
    private tenantRepository: Repository<TenantEntity>
  ) {
    // Initialize tenants from database or configuration
    this.loadTenants();
  }

  private async loadTenants() {
    const tenants = await this.tenantRepository.find();
    tenants.forEach(tenant => {
      this.tenants.set(tenant.id, tenant);
    });
  }

  async getTenantById(id: string): Promise<Tenant | undefined> {
    return this.tenants.get(id);
  }
}

// database.config.ts
import { Injectable } from '@nestjs/common';
import { TypeOrmModuleOptions, TypeOrmOptionsFactory } from '@nestjs/typeorm';
import { TenantContext } from './tenant.context';

@Injectable()
export class TypeOrmConfigService implements TypeOrmOptionsFactory {
  createTypeOrmOptions(): TypeOrmModuleOptions {
    const tenant = TenantContext.getCurrentTenant();
    
    return {
      type: 'postgres',
      host: process.env.DB_HOST,
      port: parseInt(process.env.DB_PORT),
      username: process.env.DB_USERNAME,
      password: process.env.DB_PASSWORD,
      database: tenant?.database || process.env.DB_DEFAULT_DATABASE,
      entities: ['dist/**/*.entity{.ts,.js}'],
      synchronize: false,
    };
  }
}

// app.module.ts
import { Module, MiddlewareConsumer, RequestMethod } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';
import { TenantMiddleware } from './tenant.middleware';
import { TenantService } from './tenant.service';
import { TypeOrmConfigService } from './database.config';

@Module({
  imports: [
    TypeOrmModule.forRootAsync({
      useClass: TypeOrmConfigService,
    }),
  ],
  providers: [TenantService],
})
export class AppModule {
  configure(consumer: MiddlewareConsumer) {
    consumer
      .apply(TenantMiddleware)
      .forRoutes({ path: '*', method: RequestMethod.ALL });
  }
}

```

This implementation provides a robust multi-tenant BFF architecture. Here's how it works:

1. **Tenant Context Management**:
   - Uses AsyncLocalStorage to maintain tenant context throughout the request lifecycle
   - Stores tenant information in a request-scoped context
   - Prevents tenant data leakage between requests

2. **Middleware**:
   - Extracts tenant ID from request headers (`x-tenant-id`)
   - Validates tenant existence
   - Sets up tenant context for the request

3. **Database Configuration**:
   - Dynamic database connection based on tenant
   - Uses TypeORM for database operations
   - Supports different databases per tenant

4. **Tenant Service**:
   - Manages tenant information
   - Caches tenant data for better performance
   - Provides tenant lookup functionality

To use this implementation:

1. Send requests with the `x-tenant-id` header
2. Configure tenant-specific databases in your environment
3. Implement tenant-specific repositories as needed

Key benefits:

- Complete isolation between tenants
- Request-scoped tenant context
- Type-safe implementation
- Easy to extend and customize

Would you like me to:
4. Add authentication/authorization for tenants?
5. Show how to implement tenant-specific caching?
6. Add example API endpoints that use the tenant context?