# 200. Xcode's JSON project format, no project generator

- Status: Accepted
- Date: 2026-10-29
- Deciders: You Made It engineering

## Context

An iOS app needs an Xcode project, and most of this client's code is written by agents (ADR-0015). The classic `project.pbxproj` is hard to review and hard for an agent to edit, which is why projects usually generate it with XcodeGen or Tuist. Xcode 27 adds a JSON project file, `project.xcproj`, which Apple describes as readable, less prone to merge conflicts and editable by coding agents. It becomes Xcode's default only in 27.2.

## Decision

The app uses Xcode's own project in the JSON `project.xcproj` format, with synchronized folders, so adding or removing a source file never touches the project file. Build settings live in the project file, not in `.xcconfig` files. No project generator. This needs Xcode 27 or later, which `.xcode-version` pins.

## Considered options

- **XcodeGen.** Rejected: Xcode 27.2 can't open some generated projects (XcodeGen#1651), and it has no answer yet on the JSON format (XcodeGen#1655).
- **Tuist.** Rejected: a build system of its own to learn, with open Xcode 27 issues, for one app target.
- **`.xcconfig` files for build settings.** Rejected: settings in the project file override them, so there would be two places to look, and the JSON project file is already reviewable.
