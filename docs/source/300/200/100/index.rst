Feature 1: Project Scaffold Setup (1 hour)
==========================================

README.md:

``
# Project Scaffold Setup

This feature establishes the basic project structure for our BabylonJS-Python Hatch monorepo using Nx Cloud.

## Tasks
- Set up core directory structure
- Create initial pyproject.toml with Hatch configuration
- Configure Nx Cloud with nx.json
- Create README.md with project overview

## Verification
- Run `hatch env show` to verify Hatch environment setup
- Run `npx nx graph` to verify Nx workspace recognition
``

Tests:
- Verify Hatch recognizes the project: ``hatch env list``
- Verify Nx Cloud configuration: ``npx nx graph --file=nx-report.html``