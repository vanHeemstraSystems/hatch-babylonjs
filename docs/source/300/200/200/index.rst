Feature 2: Python Package Foundation (1 hour)
=============================================

**README.md:**
```markdown
# Python Package Foundation

Set up the core Python packages that will support our BabylonJS integration.

## Tasks
- Create babylon_bridge package structure with proper typing support
- Create asset_pipeline package with basic processors
- Set up basic Python test harness

## Verification
- Run `pytest python/babylon_bridge/tests/`
- Run `hatch run lint:style` to verify code style
```

**Tests:**
- Basic bridge import test: Test importing the bridge module
- Asset pipeline command test: Verify CLI commands register correctly