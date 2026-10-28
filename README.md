# CSharpSchema_Test

C# object model (oM) classes used to test the loop between this repository and
[BHoM_PythonSchema](https://github.com/BHoM/BHoM_PythonSchema): the C# is the source of truth, the Python classes are
generated from it, and a change to the Python raises a linked C# pull request here.

This is a test repository. It is laid out like a BHoM toolkit, but nothing in it is part of the BHoM.

| Project | Namespace | What it is for |
|---|---|---|
| `FixtureAlpha_oM` | `BH.oM.FixtureAlpha` | One class for every situation the converters must handle: enums (including a member named `None`), interface chains, generics with constraints, defaults, collections, quantities, cycles, immutable classes |
| `FixtureBeta_oM` | `BH.oM.FixtureBeta` | A second assembly: a class with the same simple name as one in Alpha, and a class that uses both |

The folders do not always follow the namespaces, on purpose (for example `AdministrativeInformation/ProjectLike.cs`), like in
many real BHoM repositories.

## Build

Needs the .NET SDK, and `BHoM.dll` and `Quantities_oM.dll` in `%ProgramData%\BHoM\Assemblies` (build
[BHoM/BHoM](https://github.com/BHoM/BHoM) first).

```powershell
dotnet build CSharpSchema_Test.sln -c Release
```

As in every BHoM repository, the build copies each assembly to `%ProgramData%\BHoM\Assemblies`. To build without that, add
`-p:SkipAssemblyCopy=true`.

The assemblies carry this repository's URL in their description. The BHoM_PythonSchema generator only reads assemblies whose
organisation it is told about, so run it with `--org BHoM,BuroHappoldEngineering` (BHoM for the base classes, the other for these).
