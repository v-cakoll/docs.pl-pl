---
title: Tworzenie aplikacji platformy .NET Core za pomocą wtyczek
description: Dowiedz się, jak utworzyć aplikację platformy .NET Core, która obsługuje wtyczki.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: e8b02d9b2175b4663e665db1a5a40a9bf3c44d10
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216256"
---
# <a name="create-a-net-core-application-with-plugins"></a>Tworzenie aplikacji platformy .NET Core za pomocą wtyczek

W tym samouczku pokazano, jak:

- Tworzenie struktury projektu do obsługi wtyczek.
- Utwórz niestandardową <xref:System.Runtime.Loader.AssemblyLoadContext> , aby załadować każdą wtyczkę.
- Użyj typu `System.Runtime.Loader.AssemblyDependencyResolver` , aby zezwolić na wtyczki.
- Tworzenie wtyczek, które można łatwo wdrożyć przez Kopiowanie artefaktów kompilacji.

## <a name="prerequisites"></a>Wymagania wstępne

- Zainstaluj program [.NET Core 3,0](https://dotnet.microsoft.com/download) lub nowszą wersję.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie aplikacji:

1. Utwórz nowy folder, a w tym folderze Uruchom następujące polecenie:

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. Aby ułatwić Kompilowanie projektu, Utwórz plik rozwiązania programu Visual Studio przy użyciu. Uruchom następujące polecenie w tym samym folderze:

    ```dotnetcli
    dotnet new sln
    ```

3. Uruchom następujące polecenie, aby dodać projekt aplikacji do rozwiązania:

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

Teraz możemy wypełnić szkielet naszej aplikacji. Zastąp kod w pliku *AppWithPlugin/program. cs* następującym kodem:

```csharp
using PluginBase;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;

namespace AppWithPlugin
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length == 1 && args[0] == "/d")
                {
                    Console.WriteLine("Waiting for any key...");
                    Console.ReadLine();
                }

                // Load commands from plugins.

                if (args.Length == 0)
                {
                    Console.WriteLine("Commands: ");
                    // Output the loaded commands.
                }
                else
                {
                    foreach (string commandName in args)
                    {
                        Console.WriteLine($"-- {commandName} --");

                        // Execute the command with the name passed as an argument.

                        Console.WriteLine();
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
        }
    }
}

```

## <a name="create-the-plugin-interfaces"></a>Tworzenie interfejsów wtyczek

Następnym krokiem tworzenia aplikacji z wtyczkami jest zdefiniowanie interfejsu, do którego wtyczki wymagają wdrożenia. Sugerujemy, aby utworzyć bibliotekę klas, która zawiera wszystkie typy, które mają być używane do komunikacji między aplikacją i wtyczkami. Ten oddział umożliwia opublikowanie interfejsu wtyczki jako pakietu bez konieczności dostarczania kompletnej aplikacji.

W folderze głównym projektu uruchom `dotnet new classlib -o PluginBase`polecenie. Ponadto Uruchom `dotnet sln add PluginBase/PluginBase.csproj` polecenie, aby dodać projekt do pliku rozwiązania. Usuń plik i Utwórz nowy plik `PluginBase` w folderze o nazwie `ICommand.cs` przy użyciu następującej definicji interfejsu: `PluginBase/Class1.cs`

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

Ten `ICommand` interfejs jest interfejsem, który implementuje wszystkie wtyczki.

Teraz, gdy interfejs jest zdefiniowany, projekt aplikacji może być wypełniony nieco więcej. `ICommand` Dodaj odwołanie z `AppWithPlugin` projektu `PluginBase` do projektu za pomocą `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` polecenia z folderu głównego.

Zastąp `// Load commands from plugins` komentarz następującym fragmentem kodu, aby umożliwić mu ładowanie wtyczek z danych ścieżek plików:

```csharp
string[] pluginPaths = new string[]
{
    // Paths to plugins to load.
};

IEnumerable<ICommand> commands = pluginPaths.SelectMany(pluginPath =>
{
    Assembly pluginAssembly = LoadPlugin(pluginPath);
    return CreateCommands(pluginAssembly);
}).ToList();
```

Następnie zastąp `// Output the loaded commands` komentarz następującym fragmentem kodu:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

Zastąp `// Execute the command with the name passed as an argument` komentarz następującym fragmentem kodu:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

A wreszcie Dodaj metody statyczne do `Program` klasy o nazwie `LoadPlugin` i `CreateCommands`, jak pokazano poniżej:

```csharp
static Assembly LoadPlugin(string relativePath)
{
    throw new NotImplementedException();
}

static IEnumerable<ICommand> CreateCommands(Assembly assembly)
{
    int count = 0;

    foreach (Type type in assembly.GetTypes())
    {
        if (typeof(ICommand).IsAssignableFrom(type))
        {
            ICommand result = Activator.CreateInstance(type) as ICommand;
            if (result != null)
            {
                count++;
                yield return result;
            }
        }
    }

    if (count == 0)
    {
        string availableTypes = string.Join(",", assembly.GetTypes().Select(t => t.FullName));
        throw new ApplicationException(
            $"Can't find any type which implements ICommand in {assembly} from {assembly.Location}.\n" +
            $"Available types: {availableTypes}");
    }
}
```

## <a name="load-plugins"></a>Załaduj wtyczki

Teraz aplikacja może prawidłowo załadować i utworzyć wystąpienia poleceń z załadowanych zestawów wtyczek, ale nadal nie można załadować zestawów wtyczek. Utwórz plik o nazwie *PluginLoadContext.cs* w folderze *AppWithPlugin* o następującej zawartości:

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

Typ pochodzi od <xref:System.Runtime.Loader.AssemblyLoadContext>. `PluginLoadContext` `AssemblyLoadContext` Typ jest specjalnym typem w środowisku uruchomieniowym, który umożliwia deweloperom izolowanie załadowanych zestawów do różnych grup, aby upewnić się, że wersje zestawu nie powodują konfliktu. Ponadto niestandardowe `AssemblyLoadContext` może wybrać różne ścieżki, z których mają zostać załadowane zestawy, i zastąpić zachowanie domyślne. `PluginLoadContext` Używa wystąpienia`AssemblyDependencyResolver` typu wprowadzonego w środowisku .NET Core 3,0 w celu rozpoznania nazw zestawów w ścieżkach. `AssemblyDependencyResolver` Obiekt jest skonstruowany ze ścieżką do biblioteki klas .NET. Rozwiązuje zestawy i biblioteki natywne do ich ścieżek względnych opartych na pliku *. deps. JSON* dla biblioteki klas, której ścieżka została przeniesiona `AssemblyDependencyResolver` do konstruktora. Niestandardowe `AssemblyLoadContext` umożliwiają wtyczki mają własne zależności `AssemblyDependencyResolver` i ułatwiają prawidłowe ładowanie zależności.

Teraz, gdy `AppWithPlugin` projekt `PluginLoadContext` ma typ, zaktualizuj `Program.LoadPlugin` metodę za pomocą następującej treści:

```csharp
static Assembly LoadPlugin(string relativePath)
{
    // Navigate up to the solution root
    string root = Path.GetFullPath(Path.Combine(
        Path.GetDirectoryName(
            Path.GetDirectoryName(
                Path.GetDirectoryName(
                    Path.GetDirectoryName(
                        Path.GetDirectoryName(typeof(Program).Assembly.Location)))))));

    string pluginLocation = Path.GetFullPath(Path.Combine(root, relativePath.Replace('\\', Path.DirectorySeparatorChar)));
    Console.WriteLine($"Loading commands from: {pluginLocation}");
    PluginLoadContext loadContext = new PluginLoadContext(pluginLocation);
    return loadContext.LoadFromAssemblyName(new AssemblyName(Path.GetFileNameWithoutExtension(pluginLocation)));
}
```

Przy użyciu innego `PluginLoadContext` wystąpienia dla każdej wtyczki wtyczki mogą mieć różne lub nawet zależności powodujące konflikty bez problemu.

## <a name="create-a-simple-plugin-with-no-dependencies"></a>Tworzenie prostej wtyczki bez zależności

W folderze głównym wykonaj następujące czynności:

1. Uruchom następujące polecenie, aby utworzyć nowy projekt biblioteki klas o nazwie `HelloPlugin`:
    
    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. Uruchom następujące polecenie, aby dodać projekt do `AppWithPlugin` rozwiązania:

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. Zastąp plik *HelloPlugin/Class1. cs* plikiem o nazwie *HelloCommand.cs* następującym zawartością:

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

Teraz otwórz plik *HelloPlugin. csproj* . Powinien wyglądać podobnie do poniższego:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

W obu `<Project>` tagach Dodaj następujące elementy:

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

`<Private>false</Private>` Element jest bardzo istotny. Oznacza to, że program MSBuild nie skopiuje *PluginBase. dll* do katalogu wyjściowego dla HelloPlugin. Jeśli zestaw *PluginBase. dll* jest obecny w katalogu wyjściowym, `PluginLoadContext` program odnajdzie zestaw i załaduje go podczas ładowania zestawu *HelloPlugin. dll* . `HelloPlugin.HelloCommand` W tym momencie typ `ICommand` Zaimplementuj interfejs z *PluginBase. dll* w katalogu `HelloPlugin` wyjściowym projektu, a `ICommand` nie interfejsu, który jest ładowany do domyślnego kontekstu ładowania. Ponieważ środowisko uruchomieniowe widzi te dwa typy jako różne typy z różnych zestawów, `AppWithPlugin.Program.CreateCommands` Metoda nie znajdzie poleceń. W związku `<Private>false</Private>` z tym metadane są wymagane dla odwołania do zestawu zawierającego interfejsy wtyczki.

Po `HelloPlugin` zakończeniu projektu należy `AppWithPlugin` zaktualizować projekt, aby dowiedzieć się, `HelloPlugin` gdzie można znaleźć wtyczkę. Po komentarzu `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` Dodaj`pluginPaths`jakoelementtablicy. `// Paths to plugins to load`

## <a name="create-a-plugin-with-library-dependencies"></a>Tworzenie wtyczki z zależnościami biblioteki

Prawie wszystkie wtyczki są bardziej skomplikowane niż proste "Hello world", a wiele wtyczek ma zależności od innych bibliotek. Projekty wtyczki `OldJson`iw przykładzie pokazują dwa przykłady wtyczek `Newtonsoft.Json`z zależnościami pakietów NuGet. `JsonPlugin` Pliki projektu nie zawierają żadnych specjalnych informacji o odwołaniach do projektu i (po dodaniu ścieżek wtyczki do `pluginPaths` tablicy) wtyczki są wykonywane doskonale, nawet jeśli są uruchamiane w tym samym uruchomieniu aplikacji AppWithPlugin. Jednak te projekty nie kopiują zestawów, do których istnieją odwołania, do ich katalogu wyjściowego, więc zestawy muszą być obecne na komputerze użytkownika, aby wtyczki działały. Istnieją dwa sposoby obejścia tego problemu. Pierwszą opcją jest użycie `dotnet publish` polecenia do opublikowania biblioteki klas. Alternatywnie, jeśli chcesz mieć możliwość użycia danych wyjściowych `dotnet build` dla wtyczki, możesz `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` dodać właściwość między `<PropertyGroup>` tagami w pliku projektu wtyczki. Przykład można znaleźć w projekcie wtyczki.`XcopyablePlugin`

## <a name="other-plugin-examples-in-the-sample"></a>Inne przykłady dodatków plug-in w przykładzie

Pełny kod źródłowy dla tego samouczka można znaleźć w [repozytorium dotnet/Samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). Ukończony przykład zawiera kilka innych przykładowych `AssemblyDependencyResolver` zachowań. Na przykład `AssemblyDependencyResolver` obiekt może również rozpoznać biblioteki natywne oraz zlokalizowane zestawy satelickie zawarte w pakietach NuGet. `UVPlugin` Wrepozytorium`FrenchPlugin` przykładów przedstawiono te scenariusze.

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a>Jak odwołać się do zestawu interfejsu wtyczki zdefiniowanego w pakiecie NuGet

Załóżmy, że istnieje aplikacja A, która ma interfejs wtyczki zdefiniowany w pakiecie NuGet o nazwie `A.PluginBase`. Jak prawidłowo odwołać pakiet w projekcie wtyczki? W przypadku odwołań do projektu użycie `<Private>false</Private>` metadanych `ProjectReference` w elemencie w pliku projektu uniemożliwiło skopiowanie biblioteki DLL do danych wyjściowych.

Aby prawidłowo utworzyć odwołanie `A.PluginBase` do pakietu, należy `<PackageReference>` zmienić element w pliku projektu na następujący:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Zapobiega `A.PluginBase` to kopiowaniu zestawów do katalogu wyjściowego wtyczki i gwarantuje, że wtyczka będzie używać wersji programu `A.PluginBase`.

## <a name="plugin-target-framework-recommendations"></a>Zalecenia dotyczące platformy docelowej wtyczki

Ponieważ ładowanie zależności wtyczki używa pliku *. deps. JSON* , istnieje Gotcha powiązane z platformą docelową wtyczki. W związku z tym wtyczki powinny kierować do środowiska uruchomieniowego, takiego jak .NET Core 3,0, zamiast wersji .NET Standard. Plik *. deps. JSON* jest generowany na podstawie struktury docelowej projektu, a ponieważ wiele pakietów zgodnych z .NET Standard dostarcza zestawy referencyjne do kompilowania względem zestawów .NET Standard i implementacji dla określonych środowisk uruchomieniowych, plik *. deps. JSON* może nie być prawidłowo widoczny dla zestawów implementacji lub może odnieść się do .NET Standard wersji zestawu zamiast oczekiwanej wersji platformy .NET Core.
