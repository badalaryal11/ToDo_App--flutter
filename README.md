# Flutter TODO Application

A simple yet robust TODO mobile application built with Flutter. This project allows users to manage their daily tasks with features like adding, editing, deleting, marking tasks as complete, setting priorities, and filtering.

The application is built following Clean Architecture principles and modern Flutter best practices, making it scalable, maintainable, and testable.

---

## 📸 Screenshots

*(This is where you would place screenshots or a GIF/video demo of the application in action.)*

| Task List (Light) | Add/Edit Task | Task List (Dark) |
| :---------------: | :-------------: | :--------------: |
|   ![image](https://placehold.co/300x600/FFFFFF/000000?text=Task+List+Screen)    |   ![image](https://placehold.co/300x600/FFFFFF/000000?text=Add/Edit+Screen)    |  ![image](https://placehold.co/300x600/1a1a1a/FFFFFF?text=Task+List+Dark)  |

---

## ✨ Features

- **View Tasks**: See a clean list of all your tasks.
- **Add & Edit Tasks**: Easily create new tasks or modify existing ones.
- **Delete Tasks**: Remove tasks you no longer need.
- **Mark as Complete**: Toggle the completion status of any task.
- **Task Filtering**: Filter the task list to see `All`, `Active`, or `Completed` tasks.
- **Task Priority**: Assign a `High`, `Medium`, or `Low` priority to each task.
- **Due Dates**: Set a due date for tasks.
- **Date Sorting**: Sort tasks based on their due date.
- **Local Persistence**: Tasks are saved locally on your device using Hive, so your data is safe even after restarting the app.
- **Responsive UI**: The interface adapts smoothly to different screen sizes and orientations.
- **(Optional) Dark Mode**: Includes a dark theme for comfortable viewing in low-light environments.

---

## 🏗️ Technical Stack & Architecture

This project is built using **Clean Architecture** to ensure a clear separation of concerns, making the codebase modular, scalable, and easy to test.

### Architecture Layers

1.  **Presentation Layer**: Handles all UI and user interaction.
    -   **State Management**: `flutter_bloc` is used to manage the application's state, reacting to user events and updating the UI accordingly.
    -   **UI**: Built with Flutter's declarative widget system.

2.  **Domain Layer**: Contains the core business logic and rules of the application.
    -   **Entities**: Plain Dart objects representing the core business models (e.g., `Task`).
    -   **Repositories (Abstract)**: Defines the contracts for the data layer.
    -   **Use Cases**: Encapsulates a single, specific business operation (e.g., `AddTask`, `GetTasks`).

3.  **Data Layer**: Responsible for all data operations.
    -   **Repositories (Implementation)**: Implements the repository contracts from the domain layer.
    -   **Data Sources**: Fetches data from a local database.
    -   **Local Storage**: `Hive` is used for fast and efficient local data persistence.
    -   **Models**: Data Transfer Objects (DTOs) that are compatible with the data source (e.g., Hive models).

### Key Packages
- **State Management**: `flutter_bloc`
- **Local Database**: `hive`, `hive_flutter`
- **Value Equality**: `equatable`
- **Code Generation**: `hive_generator`, `build_runner`
- **Dependency Injection**: `get_it` (for service location)
- **Path Provider**: `path_provider` (for finding the correct local path to store the database)

---

## 📂 Project Structure

The project follows a feature-first folder structure, which keeps all the code related to a specific feature in one place.

lib/├── core/│   ├── usecase/│   └── theme/│├── features/│   └── todo/│       ├── data/│       │   ├── datasources/│       │   ├── models/│       │   └── repositories/│       ││       ├── domain/│       │   ├── entities/│       │   ├── repositories/│       │   └── usecases/│       ││       └── presentation/│           ├── bloc/│           ├── pages/│           └── widgets/│├── injection_container.dart└── main.dart
---

## 💡 Notable Design Decisions

-   **Clean Architecture**: This pattern was chosen to create a decoupled, testable, and maintainable codebase. It separates business logic from UI and data concerns, allowing each part to be developed and modified independently.
-   **Repository & Use Case Patterns**: The Repository pattern abstracts the data source from the rest of the app, making it easy to swap out the database (e.g., from Hive to SQLite) without changing business logic. Use Cases encapsulate individual business rules, making the logic clearer and more reusable.
-   **Immutability**: All domain entities and BLoC states are immutable. This ensures a predictable state flow, prevents side effects, and makes debugging easier. The `equatable` package is used to simplify value comparisons.
-   **Dependency Injection**: A service locator (`get_it`) is used to manage dependencies. This inverts the control of object creation, promotes loose coupling between layers, and simplifies testing by allowing for easy mocking of dependencies.

---

## 🚀 How to Run the App

Follow these instructions to get the project up and running on your local machine.

### Prerequisites
-   Flutter SDK (stable channel)
-   Xcode (for macOS) or Android Studio
-   A code editor like VS Code or Android Studio

### Steps

1.  **Clone the Repository**
    ```sh
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    cd your-repo-name
    ```

2.  **Install Dependencies**
    ```sh
    flutter pub get
    ```

3.  **Run Code Generation**
    This project uses code generation for Hive models. Run the following command to generate the necessary files (`.g.dart`):
    ```sh
    flutter pub run build_runner build --delete-conflicting-outputs
    ```
    *Note: If you modify any models, you will need to run this command again.*

4.  **Run the Application**
    Open an iOS Simulator or an Android Emulator, then run the app from your terminal:
    ```sh
    flutter run
    ```

---

## ✅ Evaluation Checklist

| Category                  | Description                                                               | Status |
| ------------------------- | ------------------------------------------------------------------------- | :----: |
| **Architecture & Structure** | Proper use of Clean Architecture, separation of concerns, organized folders. |   ✅   |
| **Design Patterns** | Use of Repository, Use Case, and BLoC patterns.                           |   ✅   |
| **State Management** | Proper use of `flutter_bloc`, events, states, and a reactive UI.          |   ✅   |
| **Code Quality** | Clean, readable code with good naming, formatting, and comments.          |   ✅   |
| **Persistence** | Proper use of Hive for local data storage.                                |   ✅   |
| **Responsiveness** | UI scales well across different device sizes.                             |   ✅   |
| **Performance** | Use of `const` constructors, efficient rebuilds, and optimized updates.   |   ✅   |
| **Testing (Optional)** | Unit tests for BLoC, repository, or use cases.                            |   🚧   |
| **Bonus Features (Optional)** | Dark mode, animations, due date sorting, custom theming.                  |   ✅   |

---
**Author:** Badal Aryal
