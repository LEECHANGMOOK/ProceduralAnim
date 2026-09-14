# ProceduralAnim

A custom procedural animation AnimNode plugin for Unreal Engine 5.7.

ProceduralAnim applies procedural rotational motion across a bone chain and updates the chain in parent-to-child order so that each child bone is evaluated from the modified transform of its parent.

## Demo


https://github.com/user-attachments/assets/da6490dd-b497-4243-9239-115563ce6c08




## Features

* Custom Unreal Engine AnimNode
* Procedural motion across a bone chain
* Adjustable rotation parameters
* Parent-to-child transform propagation
* Component Space bone processing
* Runtime and Editor module structure
* Designed for secondary procedural motion such as tails, spines, neck chains, and similar bone structures

## How It Works

The node processes a selected bone chain sequentially.

Instead of treating each bone independently, the modified transform of the parent bone is propagated to the next child bone.

This is important when modifying bones in Component Space, because changing a parent's Component Space transform does not automatically rebuild already calculated child transforms.

The node therefore evaluates the chain in parent-to-child order and reconstructs each child transform using the updated parent transform.

## Technical Notes

An earlier implementation rotated child locations directly in Component Space.

Because those locations were absolute Component Space coordinates, applying rotation directly caused the child bones to rotate around the component origin rather than around their parent bone.

The current implementation calculates the child offset relative to its parent and applies the procedural rotation to that relative offset before reconstructing the final Component Space transform.

## Installation

1. Download the plugin from **Releases**.
2. Copy the plugin folder into your project's `Plugins` directory.
3. Regenerate project files if required.
4. Build the project.
5. Enable the plugin in Unreal Engine.

## Compatibility

* Unreal Engine 5.7
* C++ project / plugin build required

## Source

The Runtime and Editor source code is included in this repository.

## Related Technical Breakdown

A detailed breakdown of the Component Space transform issue and the implementation process is available on my technical blog.
https://uforider.tistory.com/13
## Author

**Changmook Lee**
Technical Animator
















