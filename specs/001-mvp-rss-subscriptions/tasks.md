# Tasks: MVP RSS Subscriptions

**Input**: Design documents from `/specs/001-mvp-rss-subscriptions/`

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Initialize the backend/frontend structure and ensure the project layout matches the implementation plan.

- [ ] T001 Create the backend project skeleton in `backend/RSSFeedReader.Api/` with `Program.cs`, `Controllers/`, and `Models/`
- [ ] T002 Create the frontend Blazor WebAssembly project skeleton in `frontend/RSSFeedReader.UI/` with `Program.cs`, `Pages/`, and `wwwroot/appsettings.json`
- [ ] T003 [P] Add `specs/001-mvp-rss-subscriptions/quickstart.md` verification notes and ensure the quickstart commands match the generated project layout
- [ ] T004 [P] Add `.gitignore` or project-level ignore entries for build outputs in `backend/RSSFeedReader.Api/` and `frontend/RSSFeedReader.UI/`

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Build the core backend API contract and frontend connectivity that every user story depends on.

- [ ] T005 Create `backend/RSSFeedReader.Api/Models/Subscription.cs` defining `id` and `url`
- [ ] T006 [P] Implement in-memory subscription storage in `backend/RSSFeedReader.Api/Services/SubscriptionRepository.cs`
- [ ] T007 [P] Implement `backend/RSSFeedReader.Api/Controllers/SubscriptionsController.cs` with `GET /api/subscriptions`, `POST /api/subscriptions`, and optional `DELETE /api/subscriptions/{id}`
- [ ] T008 Configure backend CORS and HTTP routing in `backend/RSSFeedReader.Api/Program.cs` to allow the frontend origin
- [ ] T009 Create `frontend/RSSFeedReader.UI/wwwroot/appsettings.json` and configure `HttpClient` in `frontend/RSSFeedReader.UI/Program.cs` with the backend API base URL

---

## Phase 3: User Story 1 - Add subscription (Priority: P1) 🎯 MVP

**Goal**: Let a user submit a new RSS/Atom feed URL and add it to the current session's subscription list.

**Independent Test**: Run the app, enter a feed URL in the subscription input field, click add, and verify the new subscription appears immediately.

- [ ] T010 [US1] Create the subscription entry page in `frontend/RSSFeedReader.UI/Pages/Subscriptions.razor`
- [ ] T011 [US1] Add the subscription form and submit handler to `frontend/RSSFeedReader.UI/Pages/Subscriptions.razor`
- [ ] T012 [US1] Implement non-empty URL validation in `frontend/RSSFeedReader.UI/Pages/Subscriptions.razor` and show an inline error message for blank input
- [ ] T013 [US1] Implement the frontend POST call to `backend/RSSFeedReader.Api/Controllers/SubscriptionsController.cs`
- [ ] T014 [US1] Update the frontend state so the subscription list refreshes immediately after a successful add

---

## Phase 4: User Story 2 - View subscriptions (Priority: P2)

**Goal**: Let a user view the in-memory subscription list created during the current session.

**Independent Test**: After adding subscriptions, refresh or revisit the page and confirm the list shows the current session subscriptions.

- [ ] T015 [US2] Implement `GET /api/subscriptions` in `backend/RSSFeedReader.Api/Controllers/SubscriptionsController.cs`
- [ ] T016 [US2] Create frontend list rendering in `frontend/RSSFeedReader.UI/Pages/Subscriptions.razor`
- [ ] T017 [US2] Implement the frontend call to fetch subscriptions in `frontend/RSSFeedReader.UI/Pages/Subscriptions.razor`
- [ ] T018 [US2] Add session list display markup for each subscription URL in `frontend/RSSFeedReader.UI/Pages/Subscriptions.razor`
- [ ] T019 [US2] Ensure the frontend list updates when the user adds a subscription and when the page reloads during the current session

---

## Phase 5: Polish & Cross-Cutting Concerns

**Purpose**: Clean up the implementation, verify the MVP flow, and ensure the project is ready to demo.

- [ ] T020 [P] Remove any Blazor starter template demo pages or placeholder content that conflicts with the MVP subscription page
- [ ] T021 [P] Verify the `quickstart.md` commands against the actual project layout and update them if needed
- [ ] T022 [P] Add a minimal README note or doc comment explaining the in-memory storage behavior for the MVP
- [ ] T023 [P] Run the app and manually verify the primary flow: add subscription → view subscription list

---

## Dependencies & Execution Order

- **Phase 1** must complete before Phase 2 begins.
- **Phase 2** blocks all user stories until the backend API contract and frontend connectivity are ready.
- **Phase 3** and **Phase 4** can be implemented in priority order once foundational work is complete.
- **Phase 5** is final polish after the user stories are functional.

## Parallel Opportunities

- `T003`, `T004`, `T006`, `T007`, `T020`, `T021`, `T022`, and `T023` are safe to run in parallel where different files are touched.
- User Story tasks within `frontend/RSSFeedReader.UI/Pages/Subscriptions.razor` should be sequenced to avoid conflicts in the same page file.
- Backend model/repository setup (`T005`, `T006`) can run in parallel with frontend project initialization (`T002`).
