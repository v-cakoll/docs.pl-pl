---
title: Tworzenie aplikacji .NET Core za pomocą wtyczki
description: Dowiedz się, jak utworzyć aplikację platformy .NET Core, która obsługuje wtyczki.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: a9431ee28c7df21a8688f845be20e062eca21887
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076812"
---
# <a name="create-a-net-core-application-with-plugins"></a>Tworzenie aplikacji .NET Core za pomocą wtyczki

Ten samouczek pokazuje, jak do:

- Tworzenie struktury projektu do obsługi wtyczek.
- Utwórz niestandardową <xref:System.Runtime.Loader.AssemblyLoadContext> załadować wtyczki.
- Użyj `System.Runtime.Loader.AssemblyDependencyResolver` typu, aby umożliwić wtyczki do mają zależności.
- Tworzenie wtyczek, które można łatwo wdrożyć przez skopiowanie artefaktów kompilacji.

## <a name="prerequisites"></a>Wymagania wstępne

- Zainstaluj [zestawu SDK platformy .NET Core 3.0 w wersji zapoznawczej 2](https://www.microsoft.com/net/core) lub nowszej.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie aplikacji:

1. Utwórz nowy folder, a w tym folderze uruchom `dotnet new console -o AppWithPlugin`. 
2. Aby skompilowanie projektu łatwiejsze, Utwórz plik rozwiązania Visual Studio. Uruchom `dotnet new sln` w tym samym folderze. 
3. Uruchom `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` można dodać projektu aplikacji do rozwiązania.

Teraz możemy Wypełnij szkielet naszej aplikacji. Zastąp kod w *AppWithPlugin/Program.cs* pliku następującym kodem:

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

## <a name="create-the-plugin-interfaces"></a>Tworzenie interfejsów wtyczki

Następnym krokiem w tworzeniu aplikacji za pomocą wtyczki jest zdefiniowanie interfejs, który muszą implementować wtyczki. Zalecamy, aby biblioteka klas, który zawiera wszystkie typy, które ma być używany do komunikacji między aplikacji i wtyczek. Podział ten umożliwia publikowanie interfejsu wtyczki jako pakiet bez konieczności wysyłania pełnej aplikacji.

W folderze głównym projektu, uruchom `dotnet new classlib -o PluginBase`. Ponadto uruchomić `dotnet sln add PluginBase/PluginBase.csproj` można dodać projektu do pliku rozwiązania. Usuń `PluginBase/Class1.cs` pliku i Utwórz nowy plik w `PluginBase` folder o nazwie `ICommand.cs` przy użyciu następującej definicji interfejsu:

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

To `ICommand` interfejs jest interfejsem wszystkie wtyczki będzie implementowany.

Teraz, gdy `ICommand` interfejsu jest zdefiniowany, projekt aplikacji może być wypełnione nieco bardziej. Dodaj odwołanie z `AppWithPlugin` projekt `PluginBase` projektu o `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` polecenia w folderze głównym.

Zastąp `// Load commands from plugins` komentarz z poniższego fragmentu kodu, włączyć go do załadowania wtyczki z podanej ścieżki pliku:

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

Następnie zastąp `// Output the loaded commands` komentarz z poniższego fragmentu kodu:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

Zastąp `// Execute the command with the name passed as an argument` komentarza z następującego fragmentu kodu:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

A na koniec należy dodać metody statyczne do `Program` klasę o nazwie `LoadPlugin` i `CreateCommands`, jak pokazano poniżej:

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

## <a name="load-plugins"></a>Ładowanie wtyczki

Teraz można poprawnie załadować i aplikacji wystąpienia poleceń z zestawów załadowanych wtyczki, ale jest nadal nie można załadować zestawy dodatków plug-in. Utwórz plik o nazwie *PluginLoadContext.cs* w *AppWithPlugin* folder o następującej zawartości:

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

`PluginLoadContext` Typ pochodzi z <xref:System.Runtime.Loader.AssemblyLoadContext>. `AssemblyLoadContext` Typ to specjalny typ w środowisku uruchomieniowym, która umożliwia deweloperom do izolowania załadowanych zestawów w różnych grupach, aby upewnić się, że wersje zestawów nie wchodzą w konflikt. Ponadto niestandardowy `AssemblyLoadContext` można wybrać różne ścieżki ładować zestawów z i zastąpić domyślne zachowanie. `PluginLoadContext` Używa wystąpienia `AssemblyDependencyResolver` typu wprowadzone w programie .NET Core 3.0 to rozpoznawanie nazw zestawu ścieżek. `AssemblyDependencyResolver` Obiekt jest konstruowany przy użyciu ścieżki do biblioteki klas platformy .NET. Jest on rozpoznawany jako zestawów i bibliotek natywnych ich względnych ścieżek na podstawie *deps.json* pliku dla biblioteki klas, w których ścieżka został przekazany do `AssemblyDependencyResolver` konstruktora. Niestandardowy `AssemblyLoadContext` umożliwia wtyczki do mają swoje własne zależności i `AssemblyDependencyResolver` ułatwia można prawidłowo załadować zależności.

Teraz, gdy `AppWithPlugin` projekt ma `PluginLoadContext` wpisz, zaktualizuj `Program.LoadPlugin` metody z treścią następujące:

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

Przy użyciu innego `PluginLoadContext` wystąpienie dla każdej wtyczki wtyczki mogą mieć różne lub nawet sprzeczne zależności bez problemu.

## <a name="create-a-simple-plugin-with-no-dependencies"></a>Tworzenie prostego wtyczki bez zależności

W folderze głównym wykonaj następujące czynności:

1. Uruchom `dotnet new classlib -o HelloPlugin` Aby utworzyć nowy projekt biblioteki klas o nazwie `HelloPlugin`.
2. Uruchom `dotnet sln add HelloPlugin/HelloPlugin.csproj` można dodać projektu do `AppWithPlugin` rozwiązania. 
3. Zastąp *HelloPlugin/Class1.cs* pliku przy użyciu pliku o nazwie *HelloCommand.cs* z następującą zawartością:

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

Teraz Otwórz *HelloPlugin.csproj* pliku. Powinny one wyglądać podobnie do następującego:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

Między `<Project>` tagi, Dodaj następujące elementy:

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

`<Private>false</Private>` Element jest bardzo ważne. Informuje program MSBuild nie kopią *PluginBase.dll* do katalogu wyjściowego dla HelloPlugin. Jeśli *PluginBase.dll* zestawu znajduje się w katalogu wyjściowym `PluginLoadContext` znajdzie istnieje zestaw i załadować go podczas ładowania *HelloPlugin.dll* zestawu. W tym momencie `HelloPlugin.HelloCommand` wdroży typu `ICommand` interfejs z *PluginBase.dll* w katalogu danych wyjściowych `HelloPlugin` projektu nie `ICommand` interfejsu, który jest ładowany do domyślny kontekst ładowania. Ponieważ środowisko uruchomieniowe uznaje różnych typów z różnych zestawów tych dwóch typów `AppWithPlugin.Program.CreateCommands` metody nie będą dostępne polecenia. W rezultacie `<Private>false</Private>` metadanych jest wymagana dla odwołania do zestawu zawierającego interfejsów wtyczki.

Teraz, gdy `HelloPlugin` projektu będzie gotowa, możemy zaktualizować `AppWithPlugin` projekt, aby wiedzieć, gdzie `HelloPlugin` można znaleźć wtyczki. Po `// Paths to plugins to load` komentarz, dodawanie `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` jako element `pluginPaths` tablicy.

## <a name="create-a-plugin-with-library-dependencies"></a>Tworzenie wtyczki za pomocą zależności biblioteki

Prawie wszystkie wtyczki są bardziej skomplikowane niż proste "Hello World", a wiele wtyczek być zależny od innych bibliotek. `JsonPlugin` i `OldJson` projektów wtyczki w przykładzie przedstawiono dwa przykłady wtyczek przy użyciu zależności pakietów NuGet, na `Newtonsoft.Json`. Pliki projektu, sami nie mają żadnych specjalnych informacji odwołania projektu i (po dodaniu ścieżki wtyczki do `pluginPaths` tablicy) wtyczki uruchamiania idealnie, nawet wtedy, gdy uruchamiane w tym samym wykonywanie aplikacji AppWithPlugin. Jednak te projekty nie Kopiuj zestawy występujące w odwołaniach do swojego katalogu wyjściowego, więc zestawy muszą znajdować się na komputerze użytkownika dla wtyczek do pracy. Istnieją dwa sposoby obejścia tego problemu. Pierwszą opcją jest użycie `dotnet publish` polecenie w celu opublikowania biblioteki klas. Alternatywnie Jeśli chcesz mieć możliwość korzystania z danych wyjściowych `dotnet build` dla Twojej wtyczki, można dodać `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` właściwości między `<PropertyGroup>` tagów w pliku projektu wtyczki programu. Zobacz `XcopyablePlugin` wtyczki projektu, na przykład.

## <a name="other-plugin-examples-in-the-sample"></a>Inne przykłady wtyczki w przykładzie

Pełnego kodu źródłowego w ramach tego samouczka można znaleźć w [repozytorium dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). Ukończone przykład obejmuje kilka innych przykładów `AssemblyDependencyResolver` zachowanie. Na przykład `AssemblyDependencyResolver` obiektu można również rozwiązać natywnych bibliotek, a także zlokalizowane zestawy satelickie uwzględnione w pakietach NuGet. `UVPlugin` i `FrenchPlugin` w repozytorium przykładów przedstawione następujące scenariusze obejmujące.

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a>Jak odwołanie do zestawu interfejsu wtyczki zdefiniowanych w pakiecie NuGet

Załóżmy, że istnieje aplikacja A, która ma interfejs wtyczki zdefiniowanych w pakiecie NuGet o nazwie `A.PluginBase`. Jak odwołujesz się pakiet poprawnie w projekcie dodatku? Dla odwołań do projektu przy użyciu `<Private>false</Private>` metadanych na `ProjectReference` elementu w pliku projektu można zapobiec biblioteki dll są kopiowane do danych wyjściowych.

Aby odwołać się prawidłowo `A.PluginBase` pakietu, który chcesz zmienić `<PackageReference>` elementu w pliku projektu do następującego:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Zapobiega to `A.PluginBase` zestawów z kopiowane do katalogu wyjściowego Twojej wtyczki i zapewnia, że Twoje wtyczka użyje A wersja `A.PluginBase`.

## <a name="plugin-target-framework-recommendations"></a>Wtyczka target framework zalecenia

Ponieważ zależność wtyczki, ładowanie używa *deps.json* plików znajduje się problemy związane z wtyczki platformy docelowej. W szczególności z wtyczek powinien dotyczyć środowiska uruchomieniowego, takich jak .NET Core 3.0 zamiast wersji programu .NET Standard. `deps.json` Generowany jest plik oparty na które framework cele projektu i ponieważ wiele pakietów zgodnego z technologią .NET Standard dostarczanie zestawy referencyjne do kompilowania dla zestawów .NET Standard i wykonania dla określonych środowisk uruchomieniowych `deps.json` może nie zostały prawidłowo zestawy implementacji Zobacz lub może on Pobierz .NET Standard wersją zestawu zamiast wersji platformy .NET Core, oczekujesz, że.
