
# DigiHunt

A sleek and reactive iOS app for exploring Digimon, built using modern Swift paradigms like **SwiftUI**, **Combine**, and **MVVM** architecture. This project is test-driven, highly modular, and made for scale.

> Think of DigiHunt as a clean sandbox to demonstrate real-world Swift skills: async data flow, UI state management, mocking, and more.

---

## Tech Stack Breakdown

| Layer       | Tools / Frameworks         | Description |
|-------------|----------------------------|-------------|
| UI          | **SwiftUI**                | Declarative UI with Views and Modifiers |
| Architecture| **MVVM**                   | Separation of concerns — clear, testable logic |
| Reactive    | **Combine**                | Publishers & Subscribers to manage async data flow |
| Networking  | Digimon API service     | Mocked for tests using testable abstraction |
| Testing     | **XCTest**                 | Full coverage with both unit and UI tests |
| Mocking     | Custom JSON + Fake Services| Used for simulating real-world API responses |

---

## Key Features (In-Depth)

### Reactive Digimon Fetching with Combine
- `DigimonViewModel` uses `@Published` properties to automatically update the UI.
- API calls are wrapped with `Combine` publishers.
- On success, decoded Digimon list updates the UI via SwiftUI bindings.
- Error handling? Cleanly handled with `sink(receiveCompletion:)`.

### Unit Testing with Fake Services
- **Dependency Injection** used to inject a `FakeAPIServiceManager`.
- Test JSON files simulate both **valid** and **invalid** API responses.
- Includes tests for:
  - ViewModel logic
  - Error conditions
  - UI state updates

### Clean SwiftUI Architecture
- Single-responsibility `ViewModel`
- SwiftUI views consume only `@Published` state
- All updates to the UI are reactive and driven by Combine

---

## Project Structure (Extended)

```
DigiHunt/
├── DigiHuntApp.swift              # SwiftUI App Entry Point
├── ContentView.swift              # Main UI
├── Model/
│   └── Digimon.swift              # Codable Digimon model
├── ViewModel/
│   └── DigimonViewModel.swift     # Business logic, Combine, and state mgmt
├── DigiHuntTests/
│   ├── FakeAPIServiceManager.swift   # Mocked service using testable protocol
│   ├── DigimonViewModelTests.swift  # Unit tests for Combine + ViewModel
│   ├── ValidDigimonTest.json
│   └── ValidDigimonInvalidTest.json
└── DigiHuntUITests/
    └── DigiHuntUITests.swift      # Automated UI Tests
```

---

## Setup Instructions

1. Clone the project:

```bash
git clone https://github.com/your-username/DigiHunt.git
```

2. Open with Xcode 14+:

```bash
open DigiHunt/DigiHunt.xcodeproj
```

3. Run on simulator or real device — smooth out of the box.

---

## Running Tests

- Use Xcode’s test navigator (`⌘ + U`)
- All logic in `DigimonViewModelTests.swift` and `DigiHuntUITests.swift`
- ViewModel tests mock Combine’s data flow + error conditions

---

