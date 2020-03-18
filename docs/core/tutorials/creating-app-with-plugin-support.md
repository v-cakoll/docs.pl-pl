---
title: Tworzenie aplikacji platformy .NET Core za pomocą wtyczek
description: Dowiedz się, jak utworzyć aplikację .NET Core obsługą wtyczek.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: eae792ddaa6655bfdcd932d3cb695f9dafa68130
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240847"
---
# <a name="create-a-net-core-application-with-plugins"></a>Tworzenie aplikacji platformy .NET Core za pomocą wtyczek

W tym samouczku pokazano, jak utworzyć niestandardowe, <xref:System.Runtime.Loader.AssemblyLoadContext> aby załadować wtyczki. An <xref:System.Runtime.Loader.AssemblyDependencyResolver> służy do rozwiązywania zależności wtyczki. Samouczek poprawnie izoluje zależności wtyczki od aplikacji hostingowej. Omawiane tematy:

- Struktura projektu do obsługi wtyczek.
- Utwórz <xref:System.Runtime.Loader.AssemblyLoadContext> niestandardowy, aby załadować każdą wtyczkę.
- Użyj <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> tego typu, aby zezwolić wtyczkom na zależności.
- Autor wtyczek, które można łatwo wdrożyć, po prostu kopiując artefakty kompilacji.

## <a name="prerequisites"></a>Wymagania wstępne

- Zainstaluj [zestaw SDK .NET Core 3.0](https://dotnet.microsoft.com/download) lub nowszą wersję.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie aplikacji:

1. Utwórz nowy folder, a w tym folderze uruchom następujące polecenie:

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. Aby ułatwić tworzenie projektu, utwórz plik rozwiązania programu Visual Studio w tym samym folderze. Uruchom następujące polecenie:

    ```dotnetcli
    dotnet new sln
    ```

3. Uruchom następujące polecenie, aby dodać projekt aplikacji do rozwiązania:

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

Teraz możemy wypełnić szkielet naszej aplikacji. Zamień kod w pliku *AppWithPlugin/Program.cs* na następujący kod:

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

Następnym krokiem w tworzeniu aplikacji z wtyczkami jest definiowanie interfejsu, który wtyczki muszą zaimplementować. Sugerujemy, aby stworzyć bibliotekę klas, która zawiera wszystkie typy, które mają być używane do komunikowania się między aplikacją a wtyczkami. Ten podział pozwala na opublikowanie interfejsu wtyczki jako pakiet bez konieczności wysyłki pełnej aplikacji.

W folderze głównym projektu `dotnet new classlib -o PluginBase`uruchom . Ponadto uruchom, `dotnet sln add PluginBase/PluginBase.csproj` aby dodać projekt do pliku rozwiązania. Usuń `PluginBase/Class1.cs` plik i utwórz nowy `PluginBase` plik `ICommand.cs` w folderze o nazwie z następującą definicją interfejsu:

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

Ten `ICommand` interfejs jest interfejsem, który zaimplementują wszystkie wtyczki.

Teraz, `ICommand` gdy interfejs jest zdefiniowany, projekt aplikacji można wypełnić trochę więcej. Dodaj odwołanie z `AppWithPlugin` projektu `PluginBase` do projektu `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` za pomocą polecenia z folderu głównego.

Zastąp `// Load commands from plugins` komentarz następującym fragmentem kodu, aby umożliwić ładowanie wtyczek z podanych ścieżek plików:

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

I na koniec dodaj metody `Program` statyczne `LoadPlugin` `CreateCommands`do klasy o nazwie i , jak pokazano tutaj:

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

## <a name="load-plugins"></a>Wtyczki ładowania

Teraz aplikacja może poprawnie ładować i tworzyć polecenia z załadowanych zestawów wtyczek, ale nadal nie jest w stanie załadować zestawów wtyczek. Utwórz plik o nazwie *PluginLoadContext.cs* w folderze *AppWithPlugin* o następującej zawartości:

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

Typ `PluginLoadContext` pochodzi od <xref:System.Runtime.Loader.AssemblyLoadContext>. Typ `AssemblyLoadContext` jest specjalnym typem w czasie wykonywania, który umożliwia deweloperom izolowanie załadowanych zestawów do różnych grup, aby upewnić się, że wersje zestawu nie są w konflikcie. Ponadto niestandardowe `AssemblyLoadContext` można wybrać różne ścieżki do ładowania zestawów z i zastąpić zachowanie domyślne. Używa `PluginLoadContext` wystąpienia typu `AssemblyDependencyResolver` wprowadzonego w .NET Core 3.0 do rozpoznawania nazw zestawów do ścieżek. Obiekt `AssemblyDependencyResolver` jest konstruowany ze ścieżką do biblioteki klas .NET. Rozwiązuje zestawy i biblioteki macierzyste do ich ścieżek względnych na podstawie pliku *.deps.json* dla biblioteki klas, których ścieżka została przekazana do `AssemblyDependencyResolver` konstruktora. Custom `AssemblyLoadContext` umożliwia wtyczki mają własne zależności i `AssemblyDependencyResolver` sprawia, że łatwo poprawnie załadować zależności.

Teraz, `AppWithPlugin` gdy projekt `PluginLoadContext` ma typ, zaktualizuj `Program.LoadPlugin` metodę o następującej treści:

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

Za pomocą `PluginLoadContext` innego wystąpienia dla każdej wtyczki, wtyczki mogą mieć różne lub nawet konflikty zależności bez problemu.

## <a name="simple-plugin-with-no-dependencies"></a>Prosta wtyczka bez zależności

W folderze głównym wykonaj następujące czynności:

1. Uruchom następujące polecenie, aby utworzyć nowy `HelloPlugin`projekt biblioteki klas o nazwie:

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. Uruchom następujące polecenie, aby dodać `AppWithPlugin` projekt do rozwiązania:

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. Zamień plik *HelloPlugin/Class1.cs* na plik o nazwie *HelloCommand.cs* na następującą zawartość:

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

Teraz otwórz plik *HelloPlugin.csproj.* Zawartość okna powinna wyglądać mniej więcej tak:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

Pomiędzy `<Project>` znacznikami dodaj następujące elementy:

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

Element `<Private>false</Private>` jest ważny. Informuje to msbuild, aby nie kopiować *pliku PluginBase.dll* do katalogu wyjściowego helloplugin. Jeśli zestaw *Dll PluginBase.dll* jest `PluginLoadContext` obecny w katalogu wyjściowym, znajdzie tam zestaw i załaduje go podczas ładowania zestawu *HelloPlugin.dll.* W tym momencie `HelloPlugin.HelloCommand` `ICommand` typ zaimplementuje interfejs z pliku *PluginBase.dll* w katalogu wyjściowym `HelloPlugin` projektu, a `ICommand` nie interfejs, który jest ładowany do domyślnego kontekstu ładowania. Ponieważ czas wykonywania widzi te dwa typy jako `AppWithPlugin.Program.CreateCommands` różne typy z różnych zestawów, metoda nie znajdzie poleceń. W rezultacie `<Private>false</Private>` metadane są wymagane dla odwołania do zestawu zawierającego interfejsy wtyczki.

Podobnie `<ExcludeAssets>runtime</ExcludeAssets>` element jest również ważne, `PluginBase` jeśli odwołuje się do innych pakietów. To ustawienie ma taki `<Private>false</Private>` sam efekt jak, `PluginBase` ale działa na odwołania do pakietu, które może zawierać projekt lub jeden z jego zależności.

Po zakończeniu `HelloPlugin` projektu należy zaktualizować `AppWithPlugin` projekt, aby `HelloPlugin` wiedzieć, gdzie można znaleźć wtyczkę. Po `// Paths to plugins to load` komentarzu `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` dodaj jako element `pluginPaths` tablicy.

## <a name="plugin-with-library-dependencies"></a>Wtyczka z zależnościami biblioteki

Prawie wszystkie wtyczki są bardziej złożone niż prosty "Hello World", a wiele wtyczek ma zależności od innych bibliotek. Projekty `JsonPlugin` `OldJson` i wtyczki w przykładzie pokazują dwa przykłady wtyczek z `Newtonsoft.Json`zależnościami pakietów NuGet na . Same pliki projektu nie mają żadnych specjalnych informacji dla odwołań do projektu, `pluginPaths` a (po dodaniu ścieżek wtyczki do tablicy) wtyczki działają idealnie, nawet jeśli są uruchamiane w tym samym wykonaniu aplikacji AppWithPlugin. Jednak te projekty nie kopiują zestawów, do których istnieje odwołanie, do ich katalogu wyjściowego, więc zestawy muszą być obecne na komputerze użytkownika, aby wtyczki działały. Istnieją dwa sposoby obejścia tego problemu. Pierwszą opcją jest `dotnet publish` użycie polecenia do opublikowania biblioteki klas. Alternatywnie, jeśli chcesz mieć możliwość korzystania `dotnet build` z danych wyjściowych dla `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` wtyczki, `<PropertyGroup>` możesz dodać właściwość między tagami w pliku projektu wtyczki. Zobacz `XcopyablePlugin` projekt wtyczki na przykład.

## <a name="other-examples-in-the-sample"></a>Inne przykłady w próbce

Pełny kod źródłowy dla tego samouczka można znaleźć w [repozytorium dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). Ukończony przykład zawiera kilka innych `AssemblyDependencyResolver` przykładów zachowania. Na przykład `AssemblyDependencyResolver` obiekt może również rozpoznać natywnych bibliotek, a także zlokalizowane zestawy satelickie zawarte w pakietach NuGet. I `UVPlugin` `FrenchPlugin` w repozytorium próbek demonstrować te scenariusze.

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a>Odwoływanie się do interfejsu wtyczki z pakietu NuGet

Załóżmy, że istnieje aplikacja A, która ma interfejs wtyczki zdefiniowany w pakiecie NuGet o nazwie `A.PluginBase`. Jak poprawnie odwołać się do pakietu w projekcie wtyczki? W przypadku odwołań `<Private>false</Private>` do projektu `ProjectReference` użycie metadanych w elemencie w pliku projektu uniemożliwiło kopiowanie dll do danych wyjściowych.

Aby poprawnie odwołać się do `A.PluginBase` pakietu, chcesz zmienić `<PackageReference>` element w pliku projektu na następujący:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Zapobiega to `A.PluginBase` kopiowaniu zestawów do katalogu wyjściowego wtyczki i zapewnia, że wtyczka będzie `A.PluginBase`korzystać z wersji A .

## <a name="plugin-target-framework-recommendations"></a>Zalecenia dotyczące struktury docelowej wtyczki

Ponieważ ładowanie zależności wtyczki używa pliku *.deps.json,* istnieje gotcha związane z platformą docelową wtyczki. W szczególności wtyczki powinny być przeznaczone dla czasu wykonywania, takich jak .NET Core 3.0, zamiast wersji .NET Standard. Plik *.deps.json* jest generowany na podstawie struktury, której jest przeznaczony dla projektu, a ponieważ wiele pakietów zgodnych ze standardem .NET wysyła zestawy referencyjne do tworzenia względem standardu .NET i zestawów implementacji dla określonych środowiskauruchomieniowego, *zestawy .deps.json* mogą nie poprawnie widzieć zestawów implementacji lub może pobrać standardową wersję zestawu .NET zamiast oczekiwaną wersję .NET Core.

## <a name="plugin-framework-references"></a>Odwołania do struktury wtyczek

Obecnie wtyczki nie mogą wprowadzać nowych struktur do procesu. Na przykład nie można załadować wtyczki, `Microsoft.AspNetCore.App` która używa struktury do `Microsoft.NETCore.App` aplikacji, która używa tylko struktury głównej. Aplikacja hosta musi zadeklarować odwołania do wszystkich struktur wymaganych przez wtyczki.
