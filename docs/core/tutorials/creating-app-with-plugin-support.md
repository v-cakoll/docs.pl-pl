---
title: Tworzenie aplikacji platformy .NET Core za pomocą wtyczek
description: Dowiedz się, jak utworzyć aplikację platformy .NET Core, która obsługuje wtyczki.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: 16fc9d3c721ddd0618c980c7dc406b7ad7864ff5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739701"
---
# <a name="create-a-net-core-application-with-plugins"></a>Tworzenie aplikacji platformy .NET Core za pomocą wtyczek

W tym samouczku pokazano, jak utworzyć niestandardowy <xref:System.Runtime.Loader.AssemblyLoadContext> do ładowania wtyczek. <xref:System.Runtime.Loader.AssemblyDependencyResolver> jest używany do rozpoznawania zależności wtyczki. Samouczek prawidłowo izoluje zależności wtyczki od aplikacji hostingowej. Dowiesz się, jak:

- Tworzenie struktury projektu do obsługi wtyczek.
- Utwórz niestandardową <xref:System.Runtime.Loader.AssemblyLoadContext>, aby załadować każdą wtyczkę.
- Użyj typu <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName>, aby umożliwić dodatkiom zależności.
- Tworzenie wtyczek, które można łatwo wdrożyć przez Kopiowanie artefaktów kompilacji.

## <a name="prerequisites"></a>Wymagania wstępne

- Zainstaluj [zestaw SDK platformy .NET Core 3,0](https://dotnet.microsoft.com/download) lub nowszą wersję.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie aplikacji:

1. Utwórz nowy folder, a w tym folderze Uruchom następujące polecenie:

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. Aby ułatwić Kompilowanie projektu, Utwórz plik rozwiązania programu Visual Studio w tym samym folderze. Uruchom następujące polecenie:

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

W folderze głównym projektu uruchom `dotnet new classlib -o PluginBase`. Ponadto Uruchom `dotnet sln add PluginBase/PluginBase.csproj`, aby dodać projekt do pliku rozwiązania. Usuń plik `PluginBase/Class1.cs` i Utwórz nowy plik w folderze `PluginBase` o nazwie `ICommand.cs` przy użyciu następującej definicji interfejsu:

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

Ten interfejs `ICommand` jest interfejsem, który implementuje wszystkie wtyczki.

Teraz, gdy jest zdefiniowany interfejs `ICommand`, projekt aplikacji może być wypełniony nieco więcej. Dodaj odwołanie z projektu `AppWithPlugin` do projektu `PluginBase` z poleceniem `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` w folderze głównym.

Zastąp komentarz `// Load commands from plugins` następującym fragmentem kodu, aby umożliwić mu ładowanie wtyczek z danych ścieżek plików:

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

Następnie Zastąp komentarz `// Output the loaded commands` następującym fragmentem kodu:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

Zastąp komentarz `// Execute the command with the name passed as an argument` następującym fragmentem kodu:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

A wreszcie Dodaj metody statyczne do klasy `Program` o nazwie `LoadPlugin` i `CreateCommands`, jak pokazano poniżej:

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

Typ `PluginLoadContext` pochodzi od <xref:System.Runtime.Loader.AssemblyLoadContext>. Typ `AssemblyLoadContext` jest specjalnym typem w środowisku uruchomieniowym, który umożliwia deweloperom izolowanie załadowanych zestawów w różnych grupach, aby upewnić się, że wersje zestawu nie powodują konfliktu. Ponadto niestandardowy `AssemblyLoadContext` może wybrać różne ścieżki, z których mają zostać załadowane zestawy, i zastąpić zachowanie domyślne. `PluginLoadContext` używa wystąpienia typu `AssemblyDependencyResolver` wprowadzonego w środowisku .NET Core 3,0 w celu rozpoznania nazw zestawów w ścieżkach. Obiekt `AssemblyDependencyResolver` jest skonstruowany ze ścieżką do biblioteki klas .NET. Rozwiązuje zestawy i biblioteki natywne do ich ścieżek względnych opartych na pliku *. deps. JSON* dla biblioteki klas, której ścieżka została przeniesiona do konstruktora `AssemblyDependencyResolver`. Niestandardowy `AssemblyLoadContext` włącza wtyczki do własnych zależności, a `AssemblyDependencyResolver` ułatwia prawidłowe ładowanie zależności.

Teraz, gdy projekt `AppWithPlugin` ma typ `PluginLoadContext`, zaktualizuj metodę `Program.LoadPlugin` przy użyciu następującej treści:

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

Przy użyciu innego wystąpienia `PluginLoadContext` dla każdej wtyczki dodatki mogą mieć różne lub nawet zależności powodujące konflikty bez problemu.

## <a name="simple-plugin-with-no-dependencies"></a>Prosta wtyczka bez zależności

W folderze głównym wykonaj następujące czynności:

1. Uruchom następujące polecenie, aby utworzyć nowy projekt biblioteki klas o nazwie `HelloPlugin`:
    
    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. Uruchom następujące polecenie, aby dodać projekt do rozwiązania `AppWithPlugin`:

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

W przypadku tagów `<Project>` Dodaj następujące elementy:

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

Element `<Private>false</Private>` jest ważny. Oznacza to, że program MSBuild nie skopiuje *PluginBase. dll* do katalogu wyjściowego dla HelloPlugin. Jeśli zestaw *PluginBase. dll* jest obecny w katalogu wyjściowym, `PluginLoadContext` znajdzie zestaw i załaduje go podczas ładowania zestawu *HelloPlugin. dll* . W tym momencie typ `HelloPlugin.HelloCommand` spowoduje zaimplementowanie interfejsu `ICommand` z *PluginBase. dll* w katalogu wyjściowym projektu `HelloPlugin`, a nie interfejsu `ICommand`, który jest ładowany do domyślnego kontekstu ładowania. Ponieważ środowisko uruchomieniowe widzi te dwa typy jako różne typy z różnych zestawów, Metoda `AppWithPlugin.Program.CreateCommands` nie odnajdzie poleceń. W związku z tym metadane `<Private>false</Private>` są wymagane dla odwołania do zestawu zawierającego interfejsy wtyczki.

Teraz, gdy projekt `HelloPlugin` został ukończony, należy zaktualizować projekt `AppWithPlugin`, aby dowiedzieć się, gdzie można znaleźć wtyczkę `HelloPlugin`. Po komentarzu `// Paths to plugins to load` Dodaj `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` jako element tablicy `pluginPaths`.

## <a name="plugin-with-library-dependencies"></a>Wtyczka z zależnościami biblioteki

Prawie wszystkie wtyczki są bardziej skomplikowane niż proste "Hello world", a wiele wtyczek ma zależności od innych bibliotek. Projekty wtyczek `JsonPlugin` i `OldJson` w przykładzie pokazują dwa przykłady wtyczek z zależnościami pakietów NuGet na `Newtonsoft.Json`. Same pliki projektu nie zawierają żadnych specjalnych informacji o odwołaniach do projektu i (po dodaniu ścieżek wtyczki do tablicy `pluginPaths`) te wtyczki działają doskonale, nawet jeśli są uruchamiane w ramach tego samego uruchomienia aplikacji AppWithPlugin. Jednak te projekty nie kopiują przywoływanych zestawów do ich katalogu wyjściowego, więc zestawy muszą być obecne na komputerze użytkownika, aby wtyczki działały. Istnieją dwa sposoby obejścia tego problemu. Pierwszą opcją jest użycie polecenia `dotnet publish` w celu opublikowania biblioteki klas. Alternatywnie, jeśli chcesz mieć możliwość użycia danych wyjściowych `dotnet build` dla wtyczki, możesz dodać właściwość `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` między tagami `<PropertyGroup>` w pliku projektu wtyczki. Przykład można znaleźć w projekcie wtyczki `XcopyablePlugin`.

## <a name="other-examples-in-the-sample"></a>Inne przykłady w przykładzie

Pełny kod źródłowy dla tego samouczka można znaleźć w [repozytorium dotnet/Samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). Ukończony przykład zawiera kilka innych przykładów zachowania `AssemblyDependencyResolver`. Na przykład obiekt `AssemblyDependencyResolver` może również rozpoznać biblioteki natywne oraz zlokalizowane zestawy satelickie zawarte w pakietach NuGet. `UVPlugin` i `FrenchPlugin` w repozytorium przykłady przedstawiają te scenariusze.

## <a name="reference-a-plugin-from-a-nuget-package"></a>Odwołuje się do wtyczki z pakietu NuGet

Załóżmy, że istnieje aplikacja A, która ma interfejs wtyczki zdefiniowany w pakiecie NuGet o nazwie `A.PluginBase`. Jak prawidłowo odwołać pakiet w projekcie wtyczki? W przypadku odwołań do projektu użycie metadanych `<Private>false</Private>` w elemencie `ProjectReference` w pliku projektu uniemożliwiło skopiowanie biblioteki DLL do danych wyjściowych.

Aby prawidłowo odwołać się do pakietu `A.PluginBase`, należy zmienić element `<PackageReference>` w pliku projektu na następujący:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Zapobiega to kopiowaniu zestawów `A.PluginBase` do katalogu wyjściowego wtyczki i gwarantuje, że wtyczka będzie używać wersji `A.PluginBase`.

## <a name="plugin-target-framework-recommendations"></a>Zalecenia dotyczące platformy docelowej wtyczki

Ponieważ ładowanie zależności wtyczki używa pliku *. deps. JSON* , istnieje Gotcha powiązane z platformą docelową wtyczki. W związku z tym wtyczki powinny kierować do środowiska uruchomieniowego, takiego jak .NET Core 3,0, zamiast wersji .NET Standard. Plik *. deps. JSON* jest generowany na podstawie struktury docelowej projektu, a ponieważ wiele pakietów zgodnych z .NET Standard dostarcza zestawy referencyjne do kompilowania względem zestawów .NET Standard i implementacji dla określonych środowisk uruchomieniowych, plik *. deps. JSON* może nie być prawidłowo widoczny dla zestawów implementacji lub może odnieść się do .NET Standard wersji zestawu zamiast oczekiwanej wersji platformy .NET Core.

## <a name="plugin-framework-references"></a>Odwołania do struktury wtyczki

Obecnie wtyczki nie mogą wprowadzać nowych struktur do procesu. Na przykład nie można załadować wtyczki, która używa struktury `Microsoft.AspNetCore.App` w aplikacji, która używa tylko głównej struktury `Microsoft.NETCore.App`. Aplikacja hosta musi deklarować odwołania do wszystkich struktur wymaganych przez wtyczki.
