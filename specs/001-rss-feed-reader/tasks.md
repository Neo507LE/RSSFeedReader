# Tasks: RSS Feed Reader

**Input**: Design documents from `/specs/001-rss-feed-reader/`

**Prerequisites**: plan.md (required), spec.md (required for user stories)

**Organization**: Tasks are grouped by user story so each story can be implemented and validated independently.

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Create the initial application structure and baseline tooling for the RSS feed reader.

- [ ] T001 Create the initial repository structure under src/models/, src/services/, src/ui/, tests/unit/, and tests/integration/
- [ ] T002 Initialize the runtime dependency manifest and baseline application entry points for the selected stack
- [ ] T003 [P] Configure linting, formatting, and test-runner baseline settings

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Build the shared feed parsing, persistence, and error-handling foundation required before any story can be completed.

- [ ] T004 Create shared feed and article data models in src/models/feed_source.py and src/models/article.py
- [ ] T005 Implement feed parsing and validation logic in src/services/feed_service.py
- [ ] T006 Implement local subscription persistence and refresh orchestration in src/services/persistence_service.py
- [ ] T007 Add shared error handling, loading states, and user feedback helpers in src/ui/error_state.py

**Checkpoint**: The foundational feed parsing, persistence, and error-handling layer is ready for story implementation.

---

## Phase 3: User Story 1 - Browse and open articles from subscribed feeds (Priority: P1) 🎯 MVP

**Goal**: Enable users to see the latest articles from subscribed feeds and open them for reading.

**Independent Test**: A user can add one feed, view its article list, and open an article without extra setup.

### Implementation for User Story 1

- [ ] T008 [P] [US1] Implement the article list view in src/ui/article_list.py
- [ ] T009 [US1] Implement feed refresh and article loading flow in src/services/feed_refresh.py
- [ ] T010 [US1] Implement the article reader/detail view in src/ui/article_reader.py
- [ ] T011 [US1] Wire article selection and loading states into the main reader flow in src/ui/app_shell.py

**Checkpoint**: User Story 1 is independently functional and testable.

---

## Phase 4: User Story 2 - Manage personal feed subscriptions (Priority: P1)

**Goal**: Allow users to add and remove feeds from their subscription collection.

**Independent Test**: A user can add a valid feed, confirm it appears in the subscription list, and remove it again.

### Implementation for User Story 2

- [ ] T012 [P] [US2] Implement add/remove subscription logic in src/services/subscription_service.py
- [ ] T013 [US2] Build the subscription management UI in src/ui/subscription_panel.py
- [ ] T014 [US2] Persist subscription changes and prevent duplicate feed entries in src/services/persistence_service.py
- [ ] T015 [US2] Connect subscription actions to the main reader view in src/ui/app_shell.py

**Checkpoint**: User Story 2 is independently functional and testable.

---

## Phase 5: User Story 3 - Recover from feed and content issues gracefully (Priority: P2)

**Goal**: Provide clear feedback and safe fallbacks when feeds or articles fail to load.

**Independent Test**: A user receives a clear error when a feed cannot be fetched or an article cannot be opened.

### Implementation for User Story 3

- [ ] T016 [P] [US3] Add invalid URL and unreachable-feed validation in src/services/feed_service.py
- [ ] T017 [US3] Add error, empty-state, and retry messaging in src/ui/error_state.py
- [ ] T018 [US3] Add fallback handling for malformed or missing article content in src/ui/article_reader.py
- [ ] T019 [US3] Ensure refresh and open actions fail gracefully without crashing the reader flow

**Checkpoint**: User Story 3 is independently functional and testable.

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Improve quality, maintainability, and usability across the whole feature.

- [ ] T020 [P] Update project documentation and usage notes in README.md
- [ ] T021 [P] Refactor shared feed and article logic for maintainability across src/services/ and src/ui/
- [ ] T022 Validate the main feed-reading and subscription workflows against the feature spec and success criteria

---

## Dependencies & Execution Order

### Phase Dependencies

- Setup (Phase 1) must complete first.
- Foundational (Phase 2) must complete before any user story work begins.
- User Story 1 is the MVP path and should be validated before expanding to Stories 2 and 3.
- Polish (Phase 6) depends on all desired user stories being complete.

### User Story Dependencies

- User Story 1: No dependency on other stories beyond the foundational layer.
- User Story 2: Can be implemented after the foundational layer and may integrate with US1.
- User Story 3: Can be implemented after the foundational layer and should improve the reliability of US1/US2.

### Parallel Opportunities

- T001 and T002 can start in parallel after planning.
- T004, T005, and T006 are strong candidates for parallel work once the foundation phase begins.
- User Story 1, Story 2, and Story 3 can be implemented in parallel by separate developers once the foundational layer is ready.

### MVP Scope

- The smallest shippable scope is User Story 1 plus the foundational tasks needed to support it.
