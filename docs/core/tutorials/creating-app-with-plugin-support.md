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
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="adac2-103">Tworzenie aplikacji .NET Core za pomocą wtyczki</span><span class="sxs-lookup"><span data-stu-id="adac2-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="adac2-104">Ten samouczek pokazuje, jak do:</span><span class="sxs-lookup"><span data-stu-id="adac2-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="adac2-105">Tworzenie struktury projektu do obsługi wtyczek.</span><span class="sxs-lookup"><span data-stu-id="adac2-105">Structure a project to support plugins.</span></span>
- <span data-ttu-id="adac2-106">Utwórz niestandardową <xref:System.Runtime.Loader.AssemblyLoadContext> załadować wtyczki.</span><span class="sxs-lookup"><span data-stu-id="adac2-106">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="adac2-107">Użyj `System.Runtime.Loader.AssemblyDependencyResolver` typu, aby umożliwić wtyczki do mają zależności.</span><span class="sxs-lookup"><span data-stu-id="adac2-107">Use the `System.Runtime.Loader.AssemblyDependencyResolver` type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="adac2-108">Tworzenie wtyczek, które można łatwo wdrożyć przez skopiowanie artefaktów kompilacji.</span><span class="sxs-lookup"><span data-stu-id="adac2-108">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="adac2-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="adac2-109">Prerequisites</span></span>

- <span data-ttu-id="adac2-110">Zainstaluj [zestawu SDK platformy .NET Core 3.0 w wersji zapoznawczej 2](https://www.microsoft.com/net/core) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="adac2-110">Install the [.NET Core 3.0 Preview 2 SDK](https://www.microsoft.com/net/core) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="adac2-111">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="adac2-111">Create the application</span></span>

<span data-ttu-id="adac2-112">Pierwszym krokiem jest utworzenie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="adac2-112">The first step is to create the application:</span></span>

1. <span data-ttu-id="adac2-113">Utwórz nowy folder, a w tym folderze uruchom `dotnet new console -o AppWithPlugin`.</span><span class="sxs-lookup"><span data-stu-id="adac2-113">Create a new folder, and in that folder run `dotnet new console -o AppWithPlugin`.</span></span> 
2. <span data-ttu-id="adac2-114">Aby skompilowanie projektu łatwiejsze, Utwórz plik rozwiązania Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="adac2-114">To make building the project easier, create a Visual Studio solution file.</span></span> <span data-ttu-id="adac2-115">Uruchom `dotnet new sln` w tym samym folderze.</span><span class="sxs-lookup"><span data-stu-id="adac2-115">Run `dotnet new sln` in the same folder.</span></span> 
3. <span data-ttu-id="adac2-116">Uruchom `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` można dodać projektu aplikacji do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="adac2-116">Run `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` to add the app project to the solution.</span></span>

<span data-ttu-id="adac2-117">Teraz możemy Wypełnij szkielet naszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adac2-117">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="adac2-118">Zastąp kod w *AppWithPlugin/Program.cs* pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="adac2-118">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="adac2-119">Tworzenie interfejsów wtyczki</span><span class="sxs-lookup"><span data-stu-id="adac2-119">Create the plugin interfaces</span></span>

<span data-ttu-id="adac2-120">Następnym krokiem w tworzeniu aplikacji za pomocą wtyczki jest zdefiniowanie interfejs, który muszą implementować wtyczki.</span><span class="sxs-lookup"><span data-stu-id="adac2-120">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="adac2-121">Zalecamy, aby biblioteka klas, który zawiera wszystkie typy, które ma być używany do komunikacji między aplikacji i wtyczek.</span><span class="sxs-lookup"><span data-stu-id="adac2-121">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="adac2-122">Podział ten umożliwia publikowanie interfejsu wtyczki jako pakiet bez konieczności wysyłania pełnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adac2-122">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="adac2-123">W folderze głównym projektu, uruchom `dotnet new classlib -o PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="adac2-123">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="adac2-124">Ponadto uruchomić `dotnet sln add PluginBase/PluginBase.csproj` można dodać projektu do pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="adac2-124">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="adac2-125">Usuń `PluginBase/Class1.cs` pliku i Utwórz nowy plik w `PluginBase` folder o nazwie `ICommand.cs` przy użyciu następującej definicji interfejsu:</span><span class="sxs-lookup"><span data-stu-id="adac2-125">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="adac2-126">To `ICommand` interfejs jest interfejsem wszystkie wtyczki będzie implementowany.</span><span class="sxs-lookup"><span data-stu-id="adac2-126">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="adac2-127">Teraz, gdy `ICommand` interfejsu jest zdefiniowany, projekt aplikacji może być wypełnione nieco bardziej.</span><span class="sxs-lookup"><span data-stu-id="adac2-127">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="adac2-128">Dodaj odwołanie z `AppWithPlugin` projekt `PluginBase` projektu o `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` polecenia w folderze głównym.</span><span class="sxs-lookup"><span data-stu-id="adac2-128">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="adac2-129">Zastąp `// Load commands from plugins` komentarz z poniższego fragmentu kodu, włączyć go do załadowania wtyczki z podanej ścieżki pliku:</span><span class="sxs-lookup"><span data-stu-id="adac2-129">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="adac2-130">Następnie zastąp `// Output the loaded commands` komentarz z poniższego fragmentu kodu:</span><span class="sxs-lookup"><span data-stu-id="adac2-130">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="adac2-131">Zastąp `// Execute the command with the name passed as an argument` komentarza z następującego fragmentu kodu:</span><span class="sxs-lookup"><span data-stu-id="adac2-131">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="adac2-132">A na koniec należy dodać metody statyczne do `Program` klasę o nazwie `LoadPlugin` i `CreateCommands`, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="adac2-132">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="adac2-133">Ładowanie wtyczki</span><span class="sxs-lookup"><span data-stu-id="adac2-133">Load plugins</span></span>

<span data-ttu-id="adac2-134">Teraz można poprawnie załadować i aplikacji wystąpienia poleceń z zestawów załadowanych wtyczki, ale jest nadal nie można załadować zestawy dodatków plug-in.</span><span class="sxs-lookup"><span data-stu-id="adac2-134">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it is still unable to load the plugin assemblies.</span></span> <span data-ttu-id="adac2-135">Utwórz plik o nazwie *PluginLoadContext.cs* w *AppWithPlugin* folder o następującej zawartości:</span><span class="sxs-lookup"><span data-stu-id="adac2-135">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="adac2-136">`PluginLoadContext` Typ pochodzi z <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="adac2-136">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="adac2-137">`AssemblyLoadContext` Typ to specjalny typ w środowisku uruchomieniowym, która umożliwia deweloperom do izolowania załadowanych zestawów w różnych grupach, aby upewnić się, że wersje zestawów nie wchodzą w konflikt.</span><span class="sxs-lookup"><span data-stu-id="adac2-137">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions do not conflict.</span></span> <span data-ttu-id="adac2-138">Ponadto niestandardowy `AssemblyLoadContext` można wybrać różne ścieżki ładować zestawów z i zastąpić domyślne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="adac2-138">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="adac2-139">`PluginLoadContext` Używa wystąpienia `AssemblyDependencyResolver` typu wprowadzone w programie .NET Core 3.0 to rozpoznawanie nazw zestawu ścieżek.</span><span class="sxs-lookup"><span data-stu-id="adac2-139">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="adac2-140">`AssemblyDependencyResolver` Obiekt jest konstruowany przy użyciu ścieżki do biblioteki klas platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="adac2-140">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="adac2-141">Jest on rozpoznawany jako zestawów i bibliotek natywnych ich względnych ścieżek na podstawie *deps.json* pliku dla biblioteki klas, w których ścieżka został przekazany do `AssemblyDependencyResolver` konstruktora.</span><span class="sxs-lookup"><span data-stu-id="adac2-141">It resolves assemblies and native libraries to their relative paths based on the *deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="adac2-142">Niestandardowy `AssemblyLoadContext` umożliwia wtyczki do mają swoje własne zależności i `AssemblyDependencyResolver` ułatwia można prawidłowo załadować zależności.</span><span class="sxs-lookup"><span data-stu-id="adac2-142">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="adac2-143">Teraz, gdy `AppWithPlugin` projekt ma `PluginLoadContext` wpisz, zaktualizuj `Program.LoadPlugin` metody z treścią następujące:</span><span class="sxs-lookup"><span data-stu-id="adac2-143">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="adac2-144">Przy użyciu innego `PluginLoadContext` wystąpienie dla każdej wtyczki wtyczki mogą mieć różne lub nawet sprzeczne zależności bez problemu.</span><span class="sxs-lookup"><span data-stu-id="adac2-144">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="create-a-simple-plugin-with-no-dependencies"></a><span data-ttu-id="adac2-145">Tworzenie prostego wtyczki bez zależności</span><span class="sxs-lookup"><span data-stu-id="adac2-145">Create a simple plugin with no dependencies</span></span>

<span data-ttu-id="adac2-146">W folderze głównym wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="adac2-146">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="adac2-147">Uruchom `dotnet new classlib -o HelloPlugin` Aby utworzyć nowy projekt biblioteki klas o nazwie `HelloPlugin`.</span><span class="sxs-lookup"><span data-stu-id="adac2-147">Run `dotnet new classlib -o HelloPlugin` to create a new class library project named `HelloPlugin`.</span></span>
2. <span data-ttu-id="adac2-148">Uruchom `dotnet sln add HelloPlugin/HelloPlugin.csproj` można dodać projektu do `AppWithPlugin` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="adac2-148">Run `dotnet sln add HelloPlugin/HelloPlugin.csproj` to add the project to the `AppWithPlugin` solution.</span></span> 
3. <span data-ttu-id="adac2-149">Zastąp *HelloPlugin/Class1.cs* pliku przy użyciu pliku o nazwie *HelloCommand.cs* z następującą zawartością:</span><span class="sxs-lookup"><span data-stu-id="adac2-149">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="adac2-150">Teraz Otwórz *HelloPlugin.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="adac2-150">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="adac2-151">Powinny one wyglądać podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="adac2-151">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="adac2-152">Między `<Project>` tagi, Dodaj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="adac2-152">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="adac2-153">`<Private>false</Private>` Element jest bardzo ważne.</span><span class="sxs-lookup"><span data-stu-id="adac2-153">The `<Private>false</Private>` element is very important.</span></span> <span data-ttu-id="adac2-154">Informuje program MSBuild nie kopią *PluginBase.dll* do katalogu wyjściowego dla HelloPlugin.</span><span class="sxs-lookup"><span data-stu-id="adac2-154">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="adac2-155">Jeśli *PluginBase.dll* zestawu znajduje się w katalogu wyjściowym `PluginLoadContext` znajdzie istnieje zestaw i załadować go podczas ładowania *HelloPlugin.dll* zestawu.</span><span class="sxs-lookup"><span data-stu-id="adac2-155">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="adac2-156">W tym momencie `HelloPlugin.HelloCommand` wdroży typu `ICommand` interfejs z *PluginBase.dll* w katalogu danych wyjściowych `HelloPlugin` projektu nie `ICommand` interfejsu, który jest ładowany do domyślny kontekst ładowania.</span><span class="sxs-lookup"><span data-stu-id="adac2-156">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="adac2-157">Ponieważ środowisko uruchomieniowe uznaje różnych typów z różnych zestawów tych dwóch typów `AppWithPlugin.Program.CreateCommands` metody nie będą dostępne polecenia.</span><span class="sxs-lookup"><span data-stu-id="adac2-157">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method will not find the commands.</span></span> <span data-ttu-id="adac2-158">W rezultacie `<Private>false</Private>` metadanych jest wymagana dla odwołania do zestawu zawierającego interfejsów wtyczki.</span><span class="sxs-lookup"><span data-stu-id="adac2-158">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="adac2-159">Teraz, gdy `HelloPlugin` projektu będzie gotowa, możemy zaktualizować `AppWithPlugin` projekt, aby wiedzieć, gdzie `HelloPlugin` można znaleźć wtyczki.</span><span class="sxs-lookup"><span data-stu-id="adac2-159">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="adac2-160">Po `// Paths to plugins to load` komentarz, dodawanie `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` jako element `pluginPaths` tablicy.</span><span class="sxs-lookup"><span data-stu-id="adac2-160">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="create-a-plugin-with-library-dependencies"></a><span data-ttu-id="adac2-161">Tworzenie wtyczki za pomocą zależności biblioteki</span><span class="sxs-lookup"><span data-stu-id="adac2-161">Create a plugin with library dependencies</span></span>

<span data-ttu-id="adac2-162">Prawie wszystkie wtyczki są bardziej skomplikowane niż proste "Hello World", a wiele wtyczek być zależny od innych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="adac2-162">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="adac2-163">`JsonPlugin` i `OldJson` projektów wtyczki w przykładzie przedstawiono dwa przykłady wtyczek przy użyciu zależności pakietów NuGet, na `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="adac2-163">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="adac2-164">Pliki projektu, sami nie mają żadnych specjalnych informacji odwołania projektu i (po dodaniu ścieżki wtyczki do `pluginPaths` tablicy) wtyczki uruchamiania idealnie, nawet wtedy, gdy uruchamiane w tym samym wykonywanie aplikacji AppWithPlugin.</span><span class="sxs-lookup"><span data-stu-id="adac2-164">The project files themselves do not have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="adac2-165">Jednak te projekty nie Kopiuj zestawy występujące w odwołaniach do swojego katalogu wyjściowego, więc zestawy muszą znajdować się na komputerze użytkownika dla wtyczek do pracy.</span><span class="sxs-lookup"><span data-stu-id="adac2-165">However, these projects do not copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="adac2-166">Istnieją dwa sposoby obejścia tego problemu.</span><span class="sxs-lookup"><span data-stu-id="adac2-166">There are two ways to work around this problem.</span></span> <span data-ttu-id="adac2-167">Pierwszą opcją jest użycie `dotnet publish` polecenie w celu opublikowania biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="adac2-167">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="adac2-168">Alternatywnie Jeśli chcesz mieć możliwość korzystania z danych wyjściowych `dotnet build` dla Twojej wtyczki, można dodać `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` właściwości między `<PropertyGroup>` tagów w pliku projektu wtyczki programu.</span><span class="sxs-lookup"><span data-stu-id="adac2-168">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="adac2-169">Zobacz `XcopyablePlugin` wtyczki projektu, na przykład.</span><span class="sxs-lookup"><span data-stu-id="adac2-169">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-plugin-examples-in-the-sample"></a><span data-ttu-id="adac2-170">Inne przykłady wtyczki w przykładzie</span><span class="sxs-lookup"><span data-stu-id="adac2-170">Other plugin examples in the sample</span></span>

<span data-ttu-id="adac2-171">Pełnego kodu źródłowego w ramach tego samouczka można znaleźć w [repozytorium dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="adac2-171">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="adac2-172">Ukończone przykład obejmuje kilka innych przykładów `AssemblyDependencyResolver` zachowanie.</span><span class="sxs-lookup"><span data-stu-id="adac2-172">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="adac2-173">Na przykład `AssemblyDependencyResolver` obiektu można również rozwiązać natywnych bibliotek, a także zlokalizowane zestawy satelickie uwzględnione w pakietach NuGet.</span><span class="sxs-lookup"><span data-stu-id="adac2-173">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="adac2-174">`UVPlugin` i `FrenchPlugin` w repozytorium przykładów przedstawione następujące scenariusze obejmujące.</span><span class="sxs-lookup"><span data-stu-id="adac2-174">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a><span data-ttu-id="adac2-175">Jak odwołanie do zestawu interfejsu wtyczki zdefiniowanych w pakiecie NuGet</span><span class="sxs-lookup"><span data-stu-id="adac2-175">How to reference a plugin interface assembly defined in a NuGet package</span></span>

<span data-ttu-id="adac2-176">Załóżmy, że istnieje aplikacja A, która ma interfejs wtyczki zdefiniowanych w pakiecie NuGet o nazwie `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="adac2-176">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="adac2-177">Jak odwołujesz się pakiet poprawnie w projekcie dodatku?</span><span class="sxs-lookup"><span data-stu-id="adac2-177">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="adac2-178">Dla odwołań do projektu przy użyciu `<Private>false</Private>` metadanych na `ProjectReference` elementu w pliku projektu można zapobiec biblioteki dll są kopiowane do danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="adac2-178">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="adac2-179">Aby odwołać się prawidłowo `A.PluginBase` pakietu, który chcesz zmienić `<PackageReference>` elementu w pliku projektu do następującego:</span><span class="sxs-lookup"><span data-stu-id="adac2-179">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="adac2-180">Zapobiega to `A.PluginBase` zestawów z kopiowane do katalogu wyjściowego Twojej wtyczki i zapewnia, że Twoje wtyczka użyje A wersja `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="adac2-180">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="adac2-181">Wtyczka target framework zalecenia</span><span class="sxs-lookup"><span data-stu-id="adac2-181">Plugin target framework recommendations</span></span>

<span data-ttu-id="adac2-182">Ponieważ zależność wtyczki, ładowanie używa *deps.json* plików znajduje się problemy związane z wtyczki platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="adac2-182">Because plugin dependency loading uses the *deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="adac2-183">W szczególności z wtyczek powinien dotyczyć środowiska uruchomieniowego, takich jak .NET Core 3.0 zamiast wersji programu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="adac2-183">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="adac2-184">`deps.json` Generowany jest plik oparty na które framework cele projektu i ponieważ wiele pakietów zgodnego z technologią .NET Standard dostarczanie zestawy referencyjne do kompilowania dla zestawów .NET Standard i wykonania dla określonych środowisk uruchomieniowych `deps.json` może nie zostały prawidłowo zestawy implementacji Zobacz lub może on Pobierz .NET Standard wersją zestawu zamiast wersji platformy .NET Core, oczekujesz, że.</span><span class="sxs-lookup"><span data-stu-id="adac2-184">The `deps.json` file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the `deps.json` may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>
