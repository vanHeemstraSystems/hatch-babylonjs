Building Our Application
========================

Based on "Building React Apps in an Nx Monorepo <https://nx.dev/getting-started/tutorials/react-monorepo-tutorial>"_.

In this tutorial you'll learn how to use React with Nx in a monorepo setup.

What will you learn?

- how to create a new React application
- how to run a single task (i.e. serve your app) or run multiple tasks in parallel
- how to leverage code generators to scaffold components
- how to modularize your codebase and impose architectural constraints for better maintainability
- "how to speed up CI with Nx Cloud ⚡ <https://nx.dev/getting-started/tutorials/react-monorepo-tutorial#fast-ci>"_
- how to add BabylonJS to the monorepo

**Note**:  this tutorial sets up a repo with applications and libraries in their own subfolders. If you are looking for a React standalone app setup then check out our [React standalone app tutorial](https://nx.dev/getting-started/tutorials/react-standalone-tutorial).

Goal 
****

A BabylonJS project within a Python Hatch monorepo using Nx Cloud. This setup will separate scenes, models, and core framework components modularly while maintaining a clean organization.

Here's a complete file directory structure for your project, including a "Stand-up Room" scene and a "Scrum Master" character:


hatch-project/

├── pyproject.toml                  # Hatch project configuration

├── nx.json                         # Nx Cloud configuration

├── .nxignore                       # Nx ignore patterns

├── README.md

├── apps/                           # Applications directory for Nx Cloud

│   ├── babylon-viewer/             # Main application that renders scenes

│   │   ├── package.json

│   │   ├── tsconfig.json

│   │   ├── webpack.config.js

│   │   ├── index.html

│   │   ├── src/

│   │   │   ├── main.ts             # Entry point

│   │   │   ├── app.ts              # App configuration

│   │   │   ├── sceneLoader.ts      # Dynamic scene loader

│   │   │   └── styles.css

│   │   └── public/                 # Static assets

│   │       └── assets/

│   │           └── textures/

│   ├── scene-editor/               # Optional: Tool for editing scenes

│   │   └── ...                     # Similar structure as babylon-viewer

│   └── model-viewer/               # Optional: Tool for viewing models

│       └── ...                     # Similar structure as babylon-viewer

├── libs/                           # Shared libraries

│   ├── babylon-core/               # Core BabylonJS framework abstractions

│   │   ├── package.json

│   │   ├── tsconfig.json

│   │   └── src/

│   │       ├── index.ts            # Public API exports

│   │       ├── engine/             # Core engine components

│   │       │   └── engineFactory.ts

│   │       ├── scene/              # Base scene abstractions

│   │       │   ├── baseScene.ts    # Base scene class

│   │       │   └── sceneManager.ts # Manager for scenes

│   │       └── utils/              # Utility functions

│   │           └── ...

│   ├── babylon-scenes/             # Scene definitions

│   │   ├── package.json

│   │   ├── tsconfig.json

│   │   └── src/

│   │       ├── index.ts            # Public API exports

│   │       ├── stand-up-room/      # "Stand-up Room" scene

│   │       │   ├── index.ts        # Scene export

│   │       │   ├── standUpRoom.ts  # Scene implementation

│   │       │   ├── standUpRoom.metadata.json # Scene metadata

│   │       │   └── assets/         # Scene-specific assets

│   │       │       ├── textures/   # Textures for this scene

│   │       │       └── meshes/     # Scene-specific meshes

│   │       └── other-scenes/       # Other scenes...

│   │           └── ...

│   ├── babylon-models/             # Model definitions

│   │   ├── package.json

│   │   ├── tsconfig.json

│   │   └── src/

│   │       ├── index.ts            # Public API exports

│   │       ├── characters/

│   │       │   ├── scrum-master/   # "Scrum Master" character

│   │       │   │   ├── index.ts    # Character export

│   │       │   │   ├── scrumMaster.ts # Character implementation

│   │       │   │   ├── scrumMaster.metadata.json # Character metadata

│   │       │   │   └── assets/     # Character-specific assets

│   │       │   │       ├── textures/ # Textures for this character

│   │       │   │       └── meshes/ # 3D models for this character

│   │       │   └── other-characters/ # Other characters

│   │       │       └── ...

│   │       ├── props/              # Interactive props

│   │       └── environment/        # Environment objects

│   └── babylon-ui/                 # UI components

│       ├── package.json

│       ├── tsconfig.json

│       └── src/

│           ├── index.ts            # Public API exports

│           ├── components/         # UI components

│           │   ├── button.ts

│           │   └── ...

│           └── dialogs/            # Dialog UIs

│               └── ...

├── python/                         # Python packages for project

│   ├── babylon_bridge/             # Python-JS bridge for BabylonJS

│   │   ├── __init__.py

│   │   ├── py.typed

│   │   └── bridge.py               # Bridge implementation

│   ├── asset_pipeline/             # Asset processing pipeline

│   │   ├── __init__.py

│   │   ├── py.typed

│   │   ├── processors/             # Asset processors

│   │   │   ├── __init__.py

│   │   │   ├── texture_processor.py

│   │   │   └── mesh_processor.py

│   │   └── cli.py                  # Command-line tools

│   └── scene_generator/            # Optional: Scene generation tools

│       ├── __init__.py

│       ├── py.typed

│       └── generators/

│           ├── __init__.py

│           └── room_generator.py

├── scripts/                        # Build and utility scripts

│   ├── build.py                    # Build script

│   └── dev.py                      # Development script

└── assets/                         # Raw source assets

    ├── models/                     # 3D models (before processing)

    │   ├── characters/

    │   │   └── scrum-master/

    │   │       ├── scrum-master.blend  # Source file (Blender)

    │   │       └── textures/       # Source textures

    │   └── environments/

    │       └── stand-up-room/

    │           ├── stand-up-room.blend # Source file (Blender)

    │           └── textures/       # Source textures

    └── textures/                   # Raw textures

        └── ...


.. toctree::
   :maxdepth: 1
   :caption: Contents

   100/index
   200/index