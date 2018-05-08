Notes from talk by @colbylwilliams and @NateRickard reposted here:

# Distribute Modules

## Intro

- Now modularizing code... how do we distribute?

## Distribution Approach: Copy/pasting code/projects

- **Most common**
- Example

> **Pros:** 
> - Simple
> - Easy to change

> **Cons:** 
> - Only code **YOU** know
> - Version?
> - Permutations (defeating the purpose)



## Distribution Approach: Versioned/Tagged project/repo in source control

> **Pros:** 
> - Version (tags), and continue development
> - Debug/Step through source

> **Cons:** 
> - Updating is manual
> - Dependency issues
> - **Onboarding**
> - Get latest (out of sync)
> - Relative paths

Helpful link:
https://stackoverflow.com/questions/35979642/how-to-checkout-remote-git-tag/35979751

## Distribution Approach: Commit DLLs to source control

> **Pros:** 
> - Simple
> - "Real" versioning

> **Cons:** 
> - Updating is manual
> - Dependency issues



## Distribution Approach: Git Submodules

> **Pros:** 
> - Simple, good for Shared projects
> - **Third-party**
> - "Versioning" commits 
> - Continue to develop module 
> - Debug/Step through module's source

> **Cons:** 
> - Clone is manual
> - Updating is problematic 
> - Versioning issues

Helpful links:
https://www.benday.com/2016/11/04/one-tfs-build-multiple-git-repositories-with-submodules/
https://stackoverflow.com/questions/47618465/git-submodules-in-vsts-online
https://github.com/blog/2104-working-with-submodules

## Distribution Approach: NuGet

- Flavors of NuGet:
    - MyGet (private NuGet service)
    - Internal NuGet server(s) (TeamCity, etc.)


> **Pros:** 
> - Auto Dependency management
> - Dependency chaining
> - Multiple versions handled

> **Cons:** 
> - Additional work involved in packaging
    > Ideally in **CI system**
> - NuGet server needed
> - Organizational buy-in


:::info
This is the **ideal solution** and what we should strive for.
:::

Helpful links:
https://docs.microsoft.com/en-us/vsts/package/get-started-nuget

However will reqiure decoupling dependencies
## Intro To Decoupling Dependencies

:::info
Most of what we've been doing is in Shared projects which allows us to worry less about dependencies.
If NuGet is the ideal way to modularize/distribute, we're going to have to start worrying.
:::


## Why?

- _Always_ dependency on Xamarin.iOS / Xamarin.Android for platform-specific code
- To package into NuGet, must produce a DLL, can't use Shared Projects
- The only way some libraries can be modularized, is if we can separate dependencies (platform specific)


## Inversion of Control (IoC)
IoC is probably the most common approach in achieving this

## Design Patterns (to achieve IoC)

:::info
We won't go into any of these in depth, but let's quickly review design patterns that can be used to achieve IoC
:::

### Dependency Injection

- Define an **interface or abstract** class
- Supply the implementation at runtime
- Constructor injection
- Property injection


### Factory pattern (static delegate initializers)
- SQLite.Net platform init (e.g.)


### Service location
- Forms dependency service
- Some consider this an anti-pattern...and fight!
    - http://blog.ploeh.dk/2010/02/03/ServiceLocatorisanAnti-Pattern/ - Mark Seemann


### DI with IoC Container (usually with a built-in service locator)
- TinyIoC, Ninject, Autofac, etc.
- Pros and Cons

- Increased testability (unit tests)
- Mock test data!
	
Factory pattern and service location have their place, e.g. something like a plugin/singleton
...

## Bait-and-switch (advanced PCLs) 


- **EXAMPLE**: Possibly a bait and switch example
    - Version tracking?
    - Tie in to `AudioRecorderService` if possible
- Motz's Plugin template (now integrated into XS/VS.Mac!)
- "Nugetizer 3000" now in XS
    - Define NuGet package properties via project settings

:::info
**Bait & Switch** in conjunction with **bindings** will allow you to do this with _native_ (indigenous) libraries

- _(often requires some extra work to unify the APIs)_

- You consume these all the time with Xamarin Components/packages!\


[0]:https://github.com/xamarin/XamarinComponents
[10]:https://hackmd.io/s/rJtF2ep8e
[11]:https://hackmd.io/KzCGEYAYDMDYGYC0AOARpALIjz6ReqIgJwCm08sATMeBsBqkA===?both "edit"


