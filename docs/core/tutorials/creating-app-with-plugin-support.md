---
title: Tworzenie aplikacji platformy .NET Core za pomocą wtyczek
description: Dowiedz się, jak utworzyć aplikację platformy .NET Core, która obsługuje wtyczki.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: 5267a56d0742d8e1cae4a81c058bc4ee05e83b4e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579503"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="03a20-103">Tworzenie aplikacji platformy .NET Core za pomocą wtyczek</span><span class="sxs-lookup"><span data-stu-id="03a20-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="03a20-104">W tym samouczku pokazano, jak utworzyć niestandardowy <xref:System.Runtime.Loader.AssemblyLoadContext> do ładowania wtyczek.</span><span class="sxs-lookup"><span data-stu-id="03a20-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="03a20-105">@No__t_0 jest używany do rozpoznawania zależności wtyczki.</span><span class="sxs-lookup"><span data-stu-id="03a20-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="03a20-106">Samouczek prawidłowo izoluje zależności wtyczki od aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="03a20-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="03a20-107">Dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="03a20-107">You'll learn how to:</span></span>

- <span data-ttu-id="03a20-108">Tworzenie struktury projektu do obsługi wtyczek.</span><span class="sxs-lookup"><span data-stu-id="03a20-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="03a20-109">Utwórz niestandardową <xref:System.Runtime.Loader.AssemblyLoadContext>, aby załadować każdą wtyczkę.</span><span class="sxs-lookup"><span data-stu-id="03a20-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="03a20-110">Użyj typu <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName>, aby umożliwić dodatkiom zależności.</span><span class="sxs-lookup"><span data-stu-id="03a20-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="03a20-111">Tworzenie wtyczek, które można łatwo wdrożyć przez Kopiowanie artefaktów kompilacji.</span><span class="sxs-lookup"><span data-stu-id="03a20-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="03a20-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="03a20-112">Prerequisites</span></span>

- <span data-ttu-id="03a20-113">Zainstaluj [zestaw SDK platformy .NET Core 3,0](https://dotnet.microsoft.com/download) lub nowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="03a20-113">Install the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="03a20-114">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="03a20-114">Create the application</span></span>

<span data-ttu-id="03a20-115">Pierwszym krokiem jest utworzenie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="03a20-115">The first step is to create the application:</span></span>

1. <span data-ttu-id="03a20-116">Utwórz nowy folder, a w tym folderze Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="03a20-116">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="03a20-117">Aby ułatwić Kompilowanie projektu, Utwórz plik rozwiązania programu Visual Studio w tym samym folderze.</span><span class="sxs-lookup"><span data-stu-id="03a20-117">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="03a20-118">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="03a20-118">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="03a20-119">Uruchom następujące polecenie, aby dodać projekt aplikacji do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="03a20-119">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="03a20-120">Teraz możemy wypełnić szkielet naszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03a20-120">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="03a20-121">Zastąp kod w pliku *AppWithPlugin/program. cs* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="03a20-121">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="03a20-122">Tworzenie interfejsów wtyczek</span><span class="sxs-lookup"><span data-stu-id="03a20-122">Create the plugin interfaces</span></span>

<span data-ttu-id="03a20-123">Następnym krokiem tworzenia aplikacji z wtyczkami jest zdefiniowanie interfejsu, do którego wtyczki wymagają wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="03a20-123">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="03a20-124">Sugerujemy, aby utworzyć bibliotekę klas, która zawiera wszystkie typy, które mają być używane do komunikacji między aplikacją i wtyczkami.</span><span class="sxs-lookup"><span data-stu-id="03a20-124">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="03a20-125">Ten oddział umożliwia opublikowanie interfejsu wtyczki jako pakietu bez konieczności dostarczania kompletnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03a20-125">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="03a20-126">W folderze głównym projektu uruchom `dotnet new classlib -o PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="03a20-126">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="03a20-127">Ponadto Uruchom `dotnet sln add PluginBase/PluginBase.csproj`, aby dodać projekt do pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="03a20-127">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="03a20-128">Usuń plik `PluginBase/Class1.cs` i Utwórz nowy plik w folderze `PluginBase` o nazwie `ICommand.cs` przy użyciu następującej definicji interfejsu:</span><span class="sxs-lookup"><span data-stu-id="03a20-128">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="03a20-129">Ten interfejs `ICommand` jest interfejsem, który implementuje wszystkie wtyczki.</span><span class="sxs-lookup"><span data-stu-id="03a20-129">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="03a20-130">Teraz, gdy jest zdefiniowany interfejs `ICommand`, projekt aplikacji może być wypełniony nieco więcej.</span><span class="sxs-lookup"><span data-stu-id="03a20-130">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="03a20-131">Dodaj odwołanie z projektu `AppWithPlugin` do projektu `PluginBase` z poleceniem `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` w folderze głównym.</span><span class="sxs-lookup"><span data-stu-id="03a20-131">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="03a20-132">Zastąp komentarz `// Load commands from plugins` następującym fragmentem kodu, aby umożliwić mu ładowanie wtyczek z danych ścieżek plików:</span><span class="sxs-lookup"><span data-stu-id="03a20-132">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="03a20-133">Następnie Zastąp komentarz `// Output the loaded commands` następującym fragmentem kodu:</span><span class="sxs-lookup"><span data-stu-id="03a20-133">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="03a20-134">Zastąp komentarz `// Execute the command with the name passed as an argument` następującym fragmentem kodu:</span><span class="sxs-lookup"><span data-stu-id="03a20-134">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="03a20-135">A wreszcie Dodaj metody statyczne do klasy `Program` o nazwie `LoadPlugin` i `CreateCommands`, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="03a20-135">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="03a20-136">Załaduj wtyczki</span><span class="sxs-lookup"><span data-stu-id="03a20-136">Load plugins</span></span>

<span data-ttu-id="03a20-137">Teraz aplikacja może prawidłowo załadować i utworzyć wystąpienia poleceń z załadowanych zestawów wtyczek, ale nadal nie można załadować zestawów wtyczek.</span><span class="sxs-lookup"><span data-stu-id="03a20-137">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="03a20-138">Utwórz plik o nazwie *PluginLoadContext.cs* w folderze *AppWithPlugin* o następującej zawartości:</span><span class="sxs-lookup"><span data-stu-id="03a20-138">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="03a20-139">Typ `PluginLoadContext` pochodzi od <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="03a20-139">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="03a20-140">Typ `AssemblyLoadContext` jest specjalnym typem w środowisku uruchomieniowym, który umożliwia deweloperom izolowanie załadowanych zestawów w różnych grupach, aby upewnić się, że wersje zestawu nie powodują konfliktu.</span><span class="sxs-lookup"><span data-stu-id="03a20-140">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="03a20-141">Ponadto niestandardowy `AssemblyLoadContext` może wybrać różne ścieżki, z których mają zostać załadowane zestawy, i zastąpić zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="03a20-141">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="03a20-142">@No__t_0 używa wystąpienia typu `AssemblyDependencyResolver` wprowadzonego w środowisku .NET Core 3,0 w celu rozpoznania nazw zestawów w ścieżkach.</span><span class="sxs-lookup"><span data-stu-id="03a20-142">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="03a20-143">Obiekt `AssemblyDependencyResolver` jest skonstruowany ze ścieżką do biblioteki klas .NET.</span><span class="sxs-lookup"><span data-stu-id="03a20-143">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="03a20-144">Rozwiązuje zestawy i biblioteki natywne do ich ścieżek względnych opartych na pliku *. deps. JSON* dla biblioteki klas, której ścieżka została przeniesiona do konstruktora `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="03a20-144">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="03a20-145">Niestandardowy `AssemblyLoadContext` włącza wtyczki do własnych zależności, a `AssemblyDependencyResolver` ułatwia prawidłowe ładowanie zależności.</span><span class="sxs-lookup"><span data-stu-id="03a20-145">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="03a20-146">Teraz, gdy projekt `AppWithPlugin` ma typ `PluginLoadContext`, zaktualizuj metodę `Program.LoadPlugin` przy użyciu następującej treści:</span><span class="sxs-lookup"><span data-stu-id="03a20-146">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="03a20-147">Przy użyciu innego wystąpienia `PluginLoadContext` dla każdej wtyczki dodatki mogą mieć różne lub nawet zależności powodujące konflikty bez problemu.</span><span class="sxs-lookup"><span data-stu-id="03a20-147">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="03a20-148">Prosta wtyczka bez zależności</span><span class="sxs-lookup"><span data-stu-id="03a20-148">Simple plugin with no dependencies</span></span>

<span data-ttu-id="03a20-149">W folderze głównym wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="03a20-149">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="03a20-150">Uruchom następujące polecenie, aby utworzyć nowy projekt biblioteki klas o nazwie `HelloPlugin`:</span><span class="sxs-lookup"><span data-stu-id="03a20-150">Run the following command to create a new class library project named `HelloPlugin`:</span></span>
    
    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="03a20-151">Uruchom następujące polecenie, aby dodać projekt do rozwiązania `AppWithPlugin`:</span><span class="sxs-lookup"><span data-stu-id="03a20-151">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="03a20-152">Zastąp plik *HelloPlugin/Class1. cs* plikiem o nazwie *HelloCommand.cs* następującym zawartością:</span><span class="sxs-lookup"><span data-stu-id="03a20-152">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="03a20-153">Teraz otwórz plik *HelloPlugin. csproj* .</span><span class="sxs-lookup"><span data-stu-id="03a20-153">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="03a20-154">Powinien wyglądać podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="03a20-154">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="03a20-155">W przypadku tagów `<Project>` Dodaj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="03a20-155">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="03a20-156">Element `<Private>false</Private>` jest ważny.</span><span class="sxs-lookup"><span data-stu-id="03a20-156">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="03a20-157">Oznacza to, że program MSBuild nie skopiuje *PluginBase. dll* do katalogu wyjściowego dla HelloPlugin.</span><span class="sxs-lookup"><span data-stu-id="03a20-157">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="03a20-158">Jeśli zestaw *PluginBase. dll* jest obecny w katalogu wyjściowym, `PluginLoadContext` znajdzie zestaw i załaduje go podczas ładowania zestawu *HelloPlugin. dll* .</span><span class="sxs-lookup"><span data-stu-id="03a20-158">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="03a20-159">W tym momencie typ `HelloPlugin.HelloCommand` spowoduje zaimplementowanie interfejsu `ICommand` z *PluginBase. dll* w katalogu wyjściowym projektu `HelloPlugin`, a nie interfejsu `ICommand`, który jest ładowany do domyślnego kontekstu ładowania.</span><span class="sxs-lookup"><span data-stu-id="03a20-159">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="03a20-160">Ponieważ środowisko uruchomieniowe widzi te dwa typy jako różne typy z różnych zestawów, Metoda `AppWithPlugin.Program.CreateCommands` nie odnajdzie poleceń.</span><span class="sxs-lookup"><span data-stu-id="03a20-160">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="03a20-161">W związku z tym metadane `<Private>false</Private>` są wymagane dla odwołania do zestawu zawierającego interfejsy wtyczki.</span><span class="sxs-lookup"><span data-stu-id="03a20-161">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="03a20-162">Teraz, gdy projekt `HelloPlugin` został ukończony, należy zaktualizować projekt `AppWithPlugin`, aby dowiedzieć się, gdzie można znaleźć wtyczkę `HelloPlugin`.</span><span class="sxs-lookup"><span data-stu-id="03a20-162">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="03a20-163">Po komentarzu `// Paths to plugins to load` Dodaj `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` jako element tablicy `pluginPaths`.</span><span class="sxs-lookup"><span data-stu-id="03a20-163">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="03a20-164">Wtyczka z zależnościami biblioteki</span><span class="sxs-lookup"><span data-stu-id="03a20-164">Plugin with library dependencies</span></span>

<span data-ttu-id="03a20-165">Prawie wszystkie wtyczki są bardziej skomplikowane niż proste "Hello world", a wiele wtyczek ma zależności od innych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="03a20-165">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="03a20-166">Projekty wtyczek `JsonPlugin` i `OldJson` w przykładzie pokazują dwa przykłady wtyczek z zależnościami pakietów NuGet na `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="03a20-166">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="03a20-167">Same pliki projektu nie zawierają żadnych specjalnych informacji o odwołaniach do projektu i (po dodaniu ścieżek wtyczki do tablicy `pluginPaths`) te wtyczki działają doskonale, nawet jeśli są uruchamiane w ramach tego samego uruchomienia aplikacji AppWithPlugin.</span><span class="sxs-lookup"><span data-stu-id="03a20-167">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="03a20-168">Jednak te projekty nie kopiują przywoływanych zestawów do ich katalogu wyjściowego, więc zestawy muszą być obecne na komputerze użytkownika, aby wtyczki działały.</span><span class="sxs-lookup"><span data-stu-id="03a20-168">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="03a20-169">Istnieją dwa sposoby obejścia tego problemu.</span><span class="sxs-lookup"><span data-stu-id="03a20-169">There are two ways to work around this problem.</span></span> <span data-ttu-id="03a20-170">Pierwszą opcją jest użycie polecenia `dotnet publish` w celu opublikowania biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="03a20-170">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="03a20-171">Alternatywnie, jeśli chcesz mieć możliwość użycia danych wyjściowych `dotnet build` dla wtyczki, możesz dodać właściwość `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` między tagami `<PropertyGroup>` w pliku projektu wtyczki.</span><span class="sxs-lookup"><span data-stu-id="03a20-171">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="03a20-172">Przykład można znaleźć w projekcie wtyczki `XcopyablePlugin`.</span><span class="sxs-lookup"><span data-stu-id="03a20-172">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="03a20-173">Inne przykłady w przykładzie</span><span class="sxs-lookup"><span data-stu-id="03a20-173">Other examples in the sample</span></span>

<span data-ttu-id="03a20-174">Pełny kod źródłowy dla tego samouczka można znaleźć w [repozytorium dotnet/Samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="03a20-174">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="03a20-175">Ukończony przykład zawiera kilka innych przykładów zachowania `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="03a20-175">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="03a20-176">Na przykład obiekt `AssemblyDependencyResolver` może również rozpoznać biblioteki natywne oraz zlokalizowane zestawy satelickie zawarte w pakietach NuGet.</span><span class="sxs-lookup"><span data-stu-id="03a20-176">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="03a20-177">@No__t_0 i `FrenchPlugin` w repozytorium przykłady przedstawiają te scenariusze.</span><span class="sxs-lookup"><span data-stu-id="03a20-177">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-from-a-nuget-package"></a><span data-ttu-id="03a20-178">Odwołuje się do wtyczki z pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="03a20-178">Reference a plugin from a NuGet package</span></span>

<span data-ttu-id="03a20-179">Załóżmy, że istnieje aplikacja A, która ma interfejs wtyczki zdefiniowany w pakiecie NuGet o nazwie `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="03a20-179">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="03a20-180">Jak prawidłowo odwołać pakiet w projekcie wtyczki?</span><span class="sxs-lookup"><span data-stu-id="03a20-180">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="03a20-181">W przypadku odwołań do projektu użycie metadanych `<Private>false</Private>` w elemencie `ProjectReference` w pliku projektu uniemożliwiło skopiowanie biblioteki DLL do danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="03a20-181">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="03a20-182">Aby prawidłowo odwołać się do pakietu `A.PluginBase`, należy zmienić element `<PackageReference>` w pliku projektu na następujący:</span><span class="sxs-lookup"><span data-stu-id="03a20-182">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="03a20-183">Zapobiega to kopiowaniu zestawów `A.PluginBase` do katalogu wyjściowego wtyczki i gwarantuje, że wtyczka będzie używać wersji `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="03a20-183">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="03a20-184">Zalecenia dotyczące platformy docelowej wtyczki</span><span class="sxs-lookup"><span data-stu-id="03a20-184">Plugin target framework recommendations</span></span>

<span data-ttu-id="03a20-185">Ponieważ ładowanie zależności wtyczki używa pliku *. deps. JSON* , istnieje Gotcha powiązane z platformą docelową wtyczki.</span><span class="sxs-lookup"><span data-stu-id="03a20-185">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="03a20-186">W związku z tym wtyczki powinny kierować do środowiska uruchomieniowego, takiego jak .NET Core 3,0, zamiast wersji .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="03a20-186">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="03a20-187">Plik *. deps. JSON* jest generowany na podstawie struktury docelowej projektu, a ponieważ wiele pakietów zgodnych z .NET Standard dostarcza zestawy referencyjne do kompilowania względem zestawów .NET Standard i implementacji dla określonych środowisk uruchomieniowych, plik *. deps. JSON* może nie być prawidłowo widoczny dla zestawów implementacji lub może odnieść się do .NET Standard wersji zestawu zamiast oczekiwanej wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03a20-187">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>
