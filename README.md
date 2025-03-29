# OmsFrontend

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 16.2.16.

Angular Module Structure (Modular Design):

src/app/
│
├── core/                   # Singleton services, auth guards, interceptors
│   ├── auth/               # Auth guards, JWT service
│   ├── interceptors/       # HTTP interceptors (e.g., JWT injection)
│   └── services/           # Global services (e.g., API service)
│
├── shared/                 # Reusable components, pipes, directives
│   ├── components/         # Dumb UI components (e.g., tables, modals)
│   ├── pipes/              # Custom pipes (e.g., `currencyFormat`)
│   └── directives/         # Custom directives (e.g., `roleBasedAccess`)
│
├── modules/                # Feature modules (lazy-loaded)
│   ├── orders/             # Order management
│   │   ├── components/     # Order list, detail, create
│   │   ├── services/       # Order API calls
│   │   ├── store/          # NgRx state (actions, reducers, effects)
│   │   └── orders.module.ts
│   │
│   ├── inventory/          # Inventory dashboard
│   ├── admin/              # Admin panel (RBAC)
│   ├── reporting/          # Analytics dashboards
│   └── payment/            # Payment processing
│
├── assets/                 # Static files (images, fonts)
├── environments/           # Dev/Prod configs
└── app.module.ts           # Root module (imports CoreModule)

Key Modules Explained:

1. CoreModule
    Purpose: Houses singleton services and global configurations.

    What it includes:

    Authentication guards (AuthGuard, RoleGuard).

    HTTP interceptors (JWT injection, error handling).

    Logger service (centralized logging).

    Registration: Imported once in AppModule (uses providedIn: 'root' for services).

2. SharedModule
    Purpose: Contains reusable, stateless components/directives/pipes.

    What it includes:

    UI components (e.g., DataTableComponent, SpinnerComponent).

    Pipes (e.g., dateFormat, currencySymbol).

    Directives (e.g., HasPermissionDirective for RBAC).

    Registration: Exports components to be used across feature modules.

3. Feature Modules (Lazy-Loaded)
    Each feature module corresponds to a major app functionality (e.g., orders, inventory).
    
    Components:
    OrderListComponent: Displays orders with sorting/filtering.

    OrderDetailComponent: Shows order details/edit form.

    Services: OrderService (API calls to /api/orders).

    State Management: NgRx store for orders (actions, reducers, effects).

State Management (NgRx)
For large-scale apps, NgRx provides predictable state management:

orders/
├── store/
│   ├── actions/            # e.g., `loadOrders`, `updateOrder`
│   ├── reducers/           # State updates
│   ├── effects/            # Side effects (API calls)
│   ├── selectors/          # State queries
│   └── models/             # Interfaces (e.g., `Order`)


## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
