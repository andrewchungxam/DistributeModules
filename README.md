Notes from talk by @colbylwilliams and Nate Williams reposted here:

# Distribute Modules

## Intro

- Now modularizing code... how do we distribute?

## Distribution Approach: Copy/pasting code/projects

- **Most common**
- Example

> **Pros:** [color=green]
> - Simple
> - Easy to change

> **Cons:** [color=red]
> - Only code **YOU** know
> - Version?
> - Permutations (defeating the purpose)



## Distribution Approach: Versioned/Tagged project/repo in source control

> **Pros:** [color=green]
> - Version (tags), and continue development
> - Debug/Step through source

> **Cons:** [color=red]
> - Updating is manual
> - Dependency issues
> - **Onboarding**
> - Get latest (out of sync)
> - Relative paths



## Distribution Approach: Commit DLLs to source control

> **Pros:** [color=green]
> - Simple
> - "Real" versioning

> **Cons:** [color=red]
> - Updating is manual
> - Dependency issues



## Distribution Approach: Git Submodules

> **Pros:** [color=green]
> - Simple, good for Shared projects
> - **Third-party**
> - "Versioning" commits 
> - Continue to develop module 
> - Debug/Step through module's source

> **Cons:** [color=red]
> - Clone is manual
> - Updating is problematic 
> - Versioning issues

:::danger
Still with me?
:::


## Distribution Approach: NuGet

- Flavors of NuGet:
    - MyGet (private NuGet service)
    - Internal NuGet server(s) (TeamCity, etc.)

:::success
**QUESTION**: Anyone doing this now?
:::

> **Pros:** [color=green]
> - Auto Dependency management
> - Dependency chaining
> - Multiple versions handled

> **Cons:** [color=red]
> - Additional work involved in packaging
    > Ideally in **CI system**
> - NuGet server needed
> - Organizational buy-in


:::info
This is the **ideal solution** and what we should strive for.
:::

:::danger
**[Decouple Dependencies ->][10]**
[_(edit)_][11]
:::



[0]:https://github.com/xamarin/XamarinComponents
[10]:https://hackmd.io/s/rJtF2ep8e
[11]:https://hackmd.io/KzCGEYAYDMDYGYC0AOARpALIjz6ReqIgJwCm08sATMeBsBqkA===?both "edit"


###### tags: `Partner Summit` `Presenters Notes`
