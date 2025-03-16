Feature 3: Core BabylonJS Library Setup (1 hour)
================================================

README.md:

``
# Core BabylonJS Library

Establish the TypeScript library for BabylonJS core functionality.

## Tasks
- Create babylon-core package with TypeScript configuration
- Implement engineFactory for BabylonJS engine initialization
- Create basic scene abstractions and utilities

## Verification
- Run `npx nx test babylon-core` to execute unit tests
- Verify TypeScript compilation with `npx nx build babylon-core`
``

Tests:
- Engine initialization test: Verify engine factory creates a valid BabylonJS engine
- Scene creation test: Verify base scene class extensions work properly