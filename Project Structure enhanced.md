---
mindmap-plugin: basic
---

# my-nx-monorepo

## apps/ # Application-specific code
- admin-app/ # Admin-facing app
	- src/
		- app/
			- main.tsx # Main app entry point
			- App.tsx # App component
		- routes.tsx # App routing setup
	- project.json # Nx project config
	- tsconfig.json # TypeScript config
	- jest.config.ts # Jest config
- customer-app/ # Customer-facing app
	- src/
		- app/
			- App.tsx
		- routes.tsx
	- project.json
	- tsconfig.json
	- jest.config.ts

## libs/ # Domain-based shared libraries
- user/ # "User" domain
	- data-access/ # Data access logic for users
		- src/
			- lib/
				- hooks/ # Hooks Folder
					- userUser.ts # API calls for user management
				- i18n/ # Language config
				- providers/ # Providers Folder
				- constants/ # Constants Folder
				- types/ # Types Folder
				- parsers/ # Data Parsers Folder
			- project.json
			- tsconfig.json
			- jest.config.ts
	- feature/ # Features related to users
		- src/
			- lib/
				- assets/ # Assets Folder
				- pages/ # Feature-specific pages
					- UserProfile.tsx # User profile feature
				- hooks/ # Feature-specific hooks
				- i18n/ # Language config
				- providers/ # Providers Folder
				- constants/ # Constants Folder
				- types/ # Types Folder
				- parsers/ # Page Data Parsers Folder
				- mocks/ # Mocks Folder
			- index.ts
		- project.json
		- tsconfig.json
		- jest.config.ts
	- ui/ # UI components for users
		- src/
			- lib/
				- assets/ # Assets Folder
				- components/ # Component Folder
					- UserCard.tsx # User card UI component
				- i18n/ # Language config
				- index.ts
			- project.json
			- tsconfig.json
			- jest.config.ts
	- utils/ # Utilities related to users
		- src/
			- lib/
				- user-validator.ts # Validation logic for users
			- index.ts
		- project.json
		- tsconfig.json
		- jest.config.ts
- product/ # "Product" domain
	- data-access/
	- feature/
	- ui/
	- utils/
- order/ # "Order" domain
	- data-access/
	- feature/
	- ui/
	- utils/

## tools/ # Custom scripts or tools

## nx.json # Nx workspace configuration

## package.json # Workspace dependencies

## tsconfig.base.json # Base TypeScript configuration

## workspace.json # Nx projects configuration

## .eslintrc.json # Linting rules

## .prettierrc # Prettier configuration

## README.md # Monorepo documentation