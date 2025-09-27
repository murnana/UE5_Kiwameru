# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

PaperNinja is a learning repository following the book "Unreal Engine 5で極めるゲーム開発".
https://www.borndigital.co.jp/book/30360/

## Project Architecture

### Content Structure
- **Ai/**: AI behavior trees, blackboards, AI controller blueprints
- **Blueprints/**: Core game logic organized by type
  - `Components/`: Reusable blueprint components
  - `Gimmicks/`: Interactive game objects and mechanics
  - `Interfaces/`: Blueprint interfaces for communication
  - `Libraries/`: Function libraries and utilities
  - `Pawns/`: Player and NPC pawn blueprints
  - `Pickups/`: Collectible items (coins, power-ups)
  - `Structures/`: Data structures and custom types
- **Characters/**: Character assets (skeletons, physics assets, materials)
- **Environment/**: Environment assets and materials
- **Inputs/**: Enhanced Input System configuration
- **Maps/**: Level maps organized by stage
  - `Stage01/`: Multi-layer level design
    - `Stage01_Background`: Visual background layer
    - `Stage01_Graybox`: Gameplay geometry layer
    - `Stage01_Lighting`: Lighting setup layer
    - `Stage01_Top`: Main gameplay layer
    - `Stage02_Background`: Stage02 background layer (WIP)
    - `Sequence/`: Level sequence assets (LS_Stage01_*)
  - `Test/`: Development and test levels
    - `Test_HelloWorld`: Basic test level
    - `Test_Basic`: Foundation functionality test
    - `Test_Instance`: Instance test
    - `Test_Template`: Template test
    - `Test_Actor_Movement`: Actor movement test
    - `Test_Bug_Switch`: Switch bug test
    - `Test_Event`: Event system test
    - `Test_Navigation`: Navigation test
    - `Test_Turret`: Turret system test
    - `Test_Trigger`: Trigger system test
- **Materials/**: Shared material assets
- **Props/**: Static mesh props and decoration

### Key Blueprints

#### Game Core
- `BP_GameMode`: Main game mode controller
- `BP_PlayerController`: Player input and camera management
- `BP_PlayerCameraManager`: Camera system management
- `BP_PlayerState` & `BP_GameState`: Game state management

#### Characters & Pawns
- `BP_Ninja`: Main player character (in Pawns/ folder)
- `BP_Enemy`: AI-integrated enemy character (in Pawns/ folder)
- `BP_Rabbit`: Additional pawn type (in Pawns/ folder)
- `BP_Pawn`: Base pawn class (in Pawns/ folder)

#### Gimmicks & Objects
- `BP_Gate`: Level transition mechanics (in Gimmicks/ folder)
- `BP_JumpCube`: Platform mechanics (in Gimmicks/ folder)
- `BP_Bullet`: Projectile system (in Gimmicks/ folder)
- `BP_Turret`: Turret system (in Gimmicks/ folder)
- `BP_Switch`: Switch gimmick (in Gimmicks/ folder)
- `BP_Spikes`: Spike trap (in Gimmicks/ folder)

#### Collectibles
- `BP_Coin`: Collectible coin system (in Pickups/ folder)
- `BP_Scroll`: Scroll item (in Pickups/ folder)
- `BP_Chest`: Chest system (in Pickups/ folder)
- `BP_Pickup`: Pickup item base class (in Pickups/ folder)

#### Components
- `AC_Sensor`: Sensor component (in Components/ folder)
- `AC_SineCurveMovement`: Sine curve movement component (in Components/ folder)

#### Libraries & Utilities
- `BP_FuncLibrary`: Function library (in Libraries/ folder)
- `BP_ActorMacroLibrary`: Actor macro library (in Libraries/ folder)
- `BP_ObjectMacroLibrary`: Object macro library (in Libraries/ folder)

#### Interfaces
- `BI_DayNightSystem`: Day/night system interface (in Interfaces/ folder)
- `BI_Floor`: Floor interface (in Interfaces/ folder)

#### Data Structures
- `PatrolPoint`: Patrol point structure (in Structures/ folder)

**Note**: Some blueprints exist in both root and category folders. Use appropriate folder versions during development.

### AI System
- **Behavior Tree**: Core enemy AI logic system
  - `BT_Patrol`: Main patrol behavior tree
- **Blackboard**: AI data sharing system
  - `BB_Enemy`: Enemy AI blackboard
- **AI Controller**: AI control system
  - `BP_AIController`: Main AI controller
- **Custom Tasks (BTT_*)**:
  - `BTT_AICommand`: AI command execution task
  - `BTT_GetPatrolPoint`: Patrol point retrieval task
  - `BTT_GotoPatrol`: Patrol movement task
  - `BTT_Melee`: Melee attack task
  - `BTT_PopPatrolPoint`: Patrol point removal task
- **Custom Services (BTS_*)**:
  - `BTS_EnemySensor`: Enemy detection service
- **Decorators (BTD_*)**:
  - `BTD_ChaseTimeLimit`: Chase time limit decorator
- **Enums & Data Types**:
  - `E_AICommand`: AI command enumeration
- **AI Sensing & Patrol System**: Controls enemy detection and patrol behavior

### Input System
- Uses Enhanced Input System (UE5's latest input)
- Input Actions (IA_*): Move, Jump, Look, Sprint, ForceKill
- Input Mapping Context (IMC_Default): Centralized input configuration

## Development Workflow

### Blueprint Development Guidelines
- **Folder Structure Compliance**: Follow existing categorization in Content/Blueprints/
  - Place new blueprints in appropriate subfolders
  - Avoid dual placement in both root and category folders
- **Communication Patterns**: Use blueprint interfaces (BI_*) for inter-system communication
- **Component Design**: Implement reusable functionality as actor components (AC_*)
- **Data Structures**: Define complex data as custom structs in Structures folder
- **Naming Convention Adherence**: Follow naming conventions when creating assets
- **AI Implementation**: Continue behavior tree-based AI design
  - Properly utilize custom tasks (BTT_*), services (BTS_*), decorators (BTD_*)

### Level Design
- **Multi-Layer Approach**: Layer separation design adopted in Stage01
  - **Background Layer**: Visual background elements (Stage01_Background)
  - **Graybox Layer**: Gameplay collision/geometry (Stage01_Graybox)
  - **Lighting Layer**: Environment lighting setup (Stage01_Lighting)
  - **Top Layer**: Main gameplay elements (Stage01_Top)
- **Stage Progression**: Supports progressive development of multiple stages
  - Stage01: Fully implemented
  - Stage02: Background layer in preparation (Stage02_Background exists)
- **Level Sequences**: Cinematic sequence assets
  - Crane shots, sliding floors, shell effects and other cinematic elements
- **Test Levels**: Systematically placed in Maps/Test/
  - Function-specific test levels for system verification

### Asset Management & Naming Conventions
- **Folder Structure**: Organized by function/system
- **Blueprint Naming Conventions**:
  - `BP_*`: Regular blueprints (e.g., BP_GameMode, BP_Enemy)
  - `AC_*`: Actor components (e.g., AC_Sensor, AC_SineCurveMovement)
  - `BI_*`: Blueprint interfaces (e.g., BI_DayNightSystem, BI_Floor)
  - `BTT_*`: Behavior tree tasks (e.g., BTT_AICommand, BTT_Melee)
  - `BTS_*`: Behavior tree services (e.g., BTS_EnemySensor)
  - `BTD_*`: Behavior tree decorators (e.g., BTD_ChaseTimeLimit)
  - `BT_*`: Behavior trees (e.g., BT_Patrol)
  - `BB_*`: Blackboards (e.g., BB_Enemy)
  - `E_*`: Enumerations (e.g., E_AICommand)
- **Asset Naming Conventions**:
  - `M_*`: Materials (e.g., M_Basic_Floor, M_Metal_Steel)
  - `SKEL_*`: Skeleton assets
  - `PHYS_*`: Physics assets
  - `LS_*`: Level sequences (e.g., LS_Stage01_Crane)
  - `IA_*`: Input actions (e.g., IA_Move, IA_Jump)
  - `IMC_*`: Input mapping contexts (e.g., IMC_Default)
- **Level Naming Conventions**:
  - `Stage##_LayerName`: Stage and layer combination
  - `Test_FunctionName`: Test levels

### Special Features & Systems
- **DragMe Content**: Training/demo content pack for level editing learning
  - `Content/DragMe/Training/`: Interface, manipulation, parenting, viewport operation learning
  - `Content/DragMe/Demo/`: Constraint, debug draw, physics simulation demos
  - `Content/DragMe/Samples/`: Event, navigation, turret system samples
- **Multi-Layer Level Design**: 4-layer structure implemented in Stage01
  - Separated design for improved development efficiency and maintainability
- **Enhanced Input System**: UE5's latest input processing system
  - Rebindable control configuration
  - Combination of input actions (IA_*) and input mapping contexts (IMC_*)

## Development Environment

### System Requirements
- **OS**: Windows 10/11 (64-bit)
- **Unreal Engine**: 5.1
- **IDE**: Unreal Editor 5.1 or higher
- **Memory**: Minimum 8GB RAM (16GB recommended)
- **Storage**: ~5GB free space

### Setup Instructions
1. Install Unreal Engine 5.1 from Epic Games Launcher
2. Clone repository: `git clone <repository-url>`
3. Double-click `PaperNinja.uproject` file to open project
4. Shader compilation will run on first startup (takes several minutes)

### Recommended Settings
- **Editor Settings**:
  - Blueprint Compilation: 'Fast' mode (during development)
  - Auto Save: 5-minute intervals
  - Source Control: Enable Git integration
- **Project Settings**:
  - Target Hardware: Desktop
  - Quality Preset: Scalable
  - Startup Level: `/Game/Maps/Stage01/Stage01_Top`

### Debug & Testing
- **PIE (Play In Editor)**: F11 or Alt+P for quick testing
- **Standalone Game**: Alt+S for standalone execution
- **Blueprint Debugger**: Utilize breakpoints and watch variables
- **Log Categories**: Use `LogPaperNinja`, `LogAI`, `LogGameplay`

### Common Issues
- **Shader Compile Errors**: Restart project and clear cache
- **Blueprint Compile Errors**: Check dependencies, recompile from parent classes
- **Performance Issues**: Profile with Stat FPS, Stat Unit commands

### Project Configuration
- **Engine Version**: 5.1
- **Default Game Mode**: `/Game/Blueprints/BP_GameMode`
- **Editor Startup Map**: `/Game/Maps/Stage01/Stage01_Top`
- **Platform Target**: Windows Desktop (DirectX 12)
- **Content Packs**: Uses StarterContent pack
- **Active Plugins**:
  - ModelingToolsEditorMode (Editor-only)