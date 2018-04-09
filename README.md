# A simple demonstration of the 'An item with the same key has already been added' nuget error

To recreate open nuget-error.sln

When restoring packages should return this message `Error occurred while restoring NuGet packages: An item with the same key has already been added.`

You may need to ensure that the LocalNugetFeed folder is correctly set up as a nuget feed, although the Nuget.Config in this repository should do it.

The problem occurs when `Source` has:
- ProjectReference to project `Intermediate`
- ProjectReference to project `DoublyReferencedTarget`

And 'Intermediate' has 
- PackageReference to project `DoublyReferencedTarget`. 

Thus project DoublyReferencedTarget is referenced twice in two different ways, which creates this error.
