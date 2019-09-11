---
title: Tworzenie aplikacji platformy .NET Core za pomocą wtyczek
description: Dowiedz się, jak utworzyć aplikację platformy .NET Core, która obsługuje wtyczki.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: 54a4459619ee69fc74a14da7ff7fe10a472a4433
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849449"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="bcfd8-103">Tworzenie aplikacji platformy .NET Core za pomocą wtyczek</span><span class="sxs-lookup"><span data-stu-id="bcfd8-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="bcfd8-104">W tym samouczku pokazano, jak:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="bcfd8-105">Tworzenie struktury projektu do obsługi wtyczek.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-105">Structure a project to support plugins.</span></span>
- <span data-ttu-id="bcfd8-106">Utwórz niestandardową <xref:System.Runtime.Loader.AssemblyLoadContext> , aby załadować każdą wtyczkę.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-106">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="bcfd8-107">Użyj typu `System.Runtime.Loader.AssemblyDependencyResolver` , aby zezwolić na wtyczki.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-107">Use the `System.Runtime.Loader.AssemblyDependencyResolver` type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="bcfd8-108">Tworzenie wtyczek, które można łatwo wdrożyć przez Kopiowanie artefaktów kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-108">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bcfd8-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bcfd8-109">Prerequisites</span></span>

- <span data-ttu-id="bcfd8-110">Zainstaluj [zestaw SDK programu .NET Core 3,0 Preview 2](https://dotnet.microsoft.com/download) lub nowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-110">Install the [.NET Core 3.0 Preview 2 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="bcfd8-111">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="bcfd8-111">Create the application</span></span>

<span data-ttu-id="bcfd8-112">Pierwszym krokiem jest utworzenie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-112">The first step is to create the application:</span></span>

1. <span data-ttu-id="bcfd8-113">Utwórz nowy folder i w tym folderze zostanie uruchomiony `dotnet new console -o AppWithPlugin`.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-113">Create a new folder, and in that folder run `dotnet new console -o AppWithPlugin`.</span></span> 
2. <span data-ttu-id="bcfd8-114">Aby ułatwić Kompilowanie projektu, Utwórz plik rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-114">To make building the project easier, create a Visual Studio solution file.</span></span> <span data-ttu-id="bcfd8-115">Uruchom `dotnet new sln` w tym samym folderze.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-115">Run `dotnet new sln` in the same folder.</span></span> 
3. <span data-ttu-id="bcfd8-116">Uruchom `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` , aby dodać projekt aplikacji do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-116">Run `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` to add the app project to the solution.</span></span>

<span data-ttu-id="bcfd8-117">Teraz możemy wypełnić szkielet naszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-117">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="bcfd8-118">Zastąp kod w pliku *AppWithPlugin/program. cs* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-118">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="bcfd8-119">Tworzenie interfejsów wtyczek</span><span class="sxs-lookup"><span data-stu-id="bcfd8-119">Create the plugin interfaces</span></span>

<span data-ttu-id="bcfd8-120">Następnym krokiem tworzenia aplikacji z wtyczkami jest zdefiniowanie interfejsu, do którego wtyczki wymagają wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-120">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="bcfd8-121">Sugerujemy, aby utworzyć bibliotekę klas, która zawiera wszystkie typy, które mają być używane do komunikacji między aplikacją i wtyczkami.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-121">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="bcfd8-122">Ten oddział umożliwia opublikowanie interfejsu wtyczki jako pakietu bez konieczności dostarczania kompletnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-122">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="bcfd8-123">W folderze głównym projektu uruchom `dotnet new classlib -o PluginBase`polecenie.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-123">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="bcfd8-124">Ponadto Uruchom `dotnet sln add PluginBase/PluginBase.csproj` polecenie, aby dodać projekt do pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-124">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="bcfd8-125">Usuń plik i Utwórz nowy plik `PluginBase` w folderze o nazwie `ICommand.cs` przy użyciu następującej definicji interfejsu: `PluginBase/Class1.cs`</span><span class="sxs-lookup"><span data-stu-id="bcfd8-125">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="bcfd8-126">Ten `ICommand` interfejs jest interfejsem, który implementuje wszystkie wtyczki.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-126">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="bcfd8-127">Teraz, gdy interfejs jest zdefiniowany, projekt aplikacji może być wypełniony nieco więcej. `ICommand`</span><span class="sxs-lookup"><span data-stu-id="bcfd8-127">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="bcfd8-128">Dodaj odwołanie z `AppWithPlugin` projektu `PluginBase` do projektu za pomocą `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` polecenia z folderu głównego.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-128">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="bcfd8-129">Zastąp `// Load commands from plugins` komentarz następującym fragmentem kodu, aby umożliwić mu ładowanie wtyczek z danych ścieżek plików:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-129">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="bcfd8-130">Następnie zastąp `// Output the loaded commands` komentarz następującym fragmentem kodu:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-130">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="bcfd8-131">Zastąp `// Execute the command with the name passed as an argument` komentarz następującym fragmentem kodu:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-131">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="bcfd8-132">A wreszcie Dodaj metody statyczne do `Program` klasy o nazwie `LoadPlugin` i `CreateCommands`, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-132">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="bcfd8-133">Załaduj wtyczki</span><span class="sxs-lookup"><span data-stu-id="bcfd8-133">Load plugins</span></span>

<span data-ttu-id="bcfd8-134">Teraz aplikacja może prawidłowo załadować i utworzyć wystąpienia poleceń z załadowanych zestawów wtyczek, ale nadal nie można załadować zestawów wtyczek.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-134">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it is still unable to load the plugin assemblies.</span></span> <span data-ttu-id="bcfd8-135">Utwórz plik o nazwie *PluginLoadContext.cs* w folderze *AppWithPlugin* o następującej zawartości:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-135">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="bcfd8-136">Typ pochodzi od <xref:System.Runtime.Loader.AssemblyLoadContext>. `PluginLoadContext`</span><span class="sxs-lookup"><span data-stu-id="bcfd8-136">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="bcfd8-137">`AssemblyLoadContext` Typ jest specjalnym typem w środowisku uruchomieniowym, który umożliwia deweloperom izolowanie załadowanych zestawów do różnych grup, aby upewnić się, że wersje zestawu nie powodują konfliktu.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-137">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions do not conflict.</span></span> <span data-ttu-id="bcfd8-138">Ponadto niestandardowe `AssemblyLoadContext` może wybrać różne ścieżki, z których mają zostać załadowane zestawy, i zastąpić zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-138">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="bcfd8-139">`PluginLoadContext` Używa wystąpienia`AssemblyDependencyResolver` typu wprowadzonego w środowisku .NET Core 3,0 w celu rozpoznania nazw zestawów w ścieżkach.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-139">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="bcfd8-140">`AssemblyDependencyResolver` Obiekt jest skonstruowany ze ścieżką do biblioteki klas .NET.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-140">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="bcfd8-141">Rozwiązuje zestawy i biblioteki natywne do ich ścieżek względnych opartych na pliku *. deps. JSON* dla biblioteki klas, której ścieżka została przeniesiona `AssemblyDependencyResolver` do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-141">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="bcfd8-142">Niestandardowe `AssemblyLoadContext` umożliwiają wtyczki mają własne zależności `AssemblyDependencyResolver` i ułatwiają prawidłowe ładowanie zależności.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-142">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="bcfd8-143">Teraz, gdy `AppWithPlugin` projekt `PluginLoadContext` ma typ, zaktualizuj `Program.LoadPlugin` metodę za pomocą następującej treści:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-143">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="bcfd8-144">Przy użyciu innego `PluginLoadContext` wystąpienia dla każdej wtyczki wtyczki mogą mieć różne lub nawet zależności powodujące konflikty bez problemu.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-144">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="create-a-simple-plugin-with-no-dependencies"></a><span data-ttu-id="bcfd8-145">Tworzenie prostej wtyczki bez zależności</span><span class="sxs-lookup"><span data-stu-id="bcfd8-145">Create a simple plugin with no dependencies</span></span>

<span data-ttu-id="bcfd8-146">W folderze głównym wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-146">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="bcfd8-147">Uruchom `dotnet new classlib -o HelloPlugin` , aby utworzyć nowy projekt biblioteki klas o `HelloPlugin`nazwie.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-147">Run `dotnet new classlib -o HelloPlugin` to create a new class library project named `HelloPlugin`.</span></span>
2. <span data-ttu-id="bcfd8-148">Uruchom `dotnet sln add HelloPlugin/HelloPlugin.csproj` , aby dodać projekt `AppWithPlugin` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-148">Run `dotnet sln add HelloPlugin/HelloPlugin.csproj` to add the project to the `AppWithPlugin` solution.</span></span> 
3. <span data-ttu-id="bcfd8-149">Zastąp plik *HelloPlugin/Class1. cs* plikiem o nazwie *HelloCommand.cs* następującym zawartością:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-149">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="bcfd8-150">Teraz otwórz plik *HelloPlugin. csproj* .</span><span class="sxs-lookup"><span data-stu-id="bcfd8-150">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="bcfd8-151">Powinien wyglądać podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-151">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="bcfd8-152">W obu `<Project>` tagach Dodaj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-152">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="bcfd8-153">`<Private>false</Private>` Element jest bardzo istotny.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-153">The `<Private>false</Private>` element is very important.</span></span> <span data-ttu-id="bcfd8-154">Oznacza to, że program MSBuild nie skopiuje *PluginBase. dll* do katalogu wyjściowego dla HelloPlugin.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-154">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="bcfd8-155">Jeśli zestaw *PluginBase. dll* jest obecny w katalogu wyjściowym, `PluginLoadContext` program odnajdzie zestaw i załaduje go podczas ładowania zestawu *HelloPlugin. dll* .</span><span class="sxs-lookup"><span data-stu-id="bcfd8-155">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="bcfd8-156">`HelloPlugin.HelloCommand` W tym momencie typ `ICommand` Zaimplementuj interfejs z *PluginBase. dll* w katalogu `HelloPlugin` wyjściowym projektu, a `ICommand` nie interfejsu, który jest ładowany do domyślnego kontekstu ładowania.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-156">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="bcfd8-157">Ponieważ środowisko uruchomieniowe widzi te dwa typy jako różne typy z różnych zestawów, `AppWithPlugin.Program.CreateCommands` Metoda nie znajdzie poleceń.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-157">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method will not find the commands.</span></span> <span data-ttu-id="bcfd8-158">W związku `<Private>false</Private>` z tym metadane są wymagane dla odwołania do zestawu zawierającego interfejsy wtyczki.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-158">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="bcfd8-159">Po `HelloPlugin` zakończeniu projektu należy `AppWithPlugin` zaktualizować projekt, aby dowiedzieć się, `HelloPlugin` gdzie można znaleźć wtyczkę.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-159">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="bcfd8-160">Po komentarzu `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` Dodaj`pluginPaths`jakoelementtablicy. `// Paths to plugins to load`</span><span class="sxs-lookup"><span data-stu-id="bcfd8-160">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="create-a-plugin-with-library-dependencies"></a><span data-ttu-id="bcfd8-161">Tworzenie wtyczki z zależnościami biblioteki</span><span class="sxs-lookup"><span data-stu-id="bcfd8-161">Create a plugin with library dependencies</span></span>

<span data-ttu-id="bcfd8-162">Prawie wszystkie wtyczki są bardziej skomplikowane niż proste "Hello world", a wiele wtyczek ma zależności od innych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-162">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="bcfd8-163">Projekty wtyczki `OldJson`iw przykładzie pokazują dwa przykłady wtyczek `Newtonsoft.Json`z zależnościami pakietów NuGet. `JsonPlugin`</span><span class="sxs-lookup"><span data-stu-id="bcfd8-163">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="bcfd8-164">Pliki projektu nie zawierają żadnych specjalnych informacji o odwołaniach do projektu i (po dodaniu ścieżek wtyczki do `pluginPaths` tablicy) wtyczki są wykonywane doskonale, nawet jeśli są uruchamiane w tym samym uruchomieniu aplikacji AppWithPlugin.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-164">The project files themselves do not have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="bcfd8-165">Jednak te projekty nie kopiują zestawów, do których istnieją odwołania, do ich katalogu wyjściowego, więc zestawy muszą być obecne na komputerze użytkownika, aby wtyczki działały.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-165">However, these projects do not copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="bcfd8-166">Istnieją dwa sposoby obejścia tego problemu.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-166">There are two ways to work around this problem.</span></span> <span data-ttu-id="bcfd8-167">Pierwszą opcją jest użycie `dotnet publish` polecenia do opublikowania biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-167">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="bcfd8-168">Alternatywnie, jeśli chcesz mieć możliwość użycia danych wyjściowych `dotnet build` dla wtyczki, możesz `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` dodać właściwość między `<PropertyGroup>` tagami w pliku projektu wtyczki.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-168">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="bcfd8-169">Przykład można znaleźć w projekcie wtyczki.`XcopyablePlugin`</span><span class="sxs-lookup"><span data-stu-id="bcfd8-169">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-plugin-examples-in-the-sample"></a><span data-ttu-id="bcfd8-170">Inne przykłady dodatków plug-in w przykładzie</span><span class="sxs-lookup"><span data-stu-id="bcfd8-170">Other plugin examples in the sample</span></span>

<span data-ttu-id="bcfd8-171">Pełny kod źródłowy dla tego samouczka można znaleźć w [repozytorium dotnet/Samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="bcfd8-171">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="bcfd8-172">Ukończony przykład zawiera kilka innych przykładowych `AssemblyDependencyResolver` zachowań.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-172">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="bcfd8-173">Na przykład `AssemblyDependencyResolver` obiekt może również rozpoznać biblioteki natywne oraz zlokalizowane zestawy satelickie zawarte w pakietach NuGet.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-173">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="bcfd8-174">`UVPlugin` Wrepozytorium`FrenchPlugin` przykładów przedstawiono te scenariusze.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-174">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a><span data-ttu-id="bcfd8-175">Jak odwołać się do zestawu interfejsu wtyczki zdefiniowanego w pakiecie NuGet</span><span class="sxs-lookup"><span data-stu-id="bcfd8-175">How to reference a plugin interface assembly defined in a NuGet package</span></span>

<span data-ttu-id="bcfd8-176">Załóżmy, że istnieje aplikacja A, która ma interfejs wtyczki zdefiniowany w pakiecie NuGet o nazwie `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-176">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="bcfd8-177">Jak prawidłowo odwołać pakiet w projekcie wtyczki?</span><span class="sxs-lookup"><span data-stu-id="bcfd8-177">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="bcfd8-178">W przypadku odwołań do projektu użycie `<Private>false</Private>` metadanych `ProjectReference` w elemencie w pliku projektu uniemożliwiło skopiowanie biblioteki DLL do danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-178">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="bcfd8-179">Aby prawidłowo utworzyć odwołanie `A.PluginBase` do pakietu, należy `<PackageReference>` zmienić element w pliku projektu na następujący:</span><span class="sxs-lookup"><span data-stu-id="bcfd8-179">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="bcfd8-180">Zapobiega `A.PluginBase` to kopiowaniu zestawów do katalogu wyjściowego wtyczki i gwarantuje, że wtyczka będzie używać wersji programu `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-180">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="bcfd8-181">Zalecenia dotyczące platformy docelowej wtyczki</span><span class="sxs-lookup"><span data-stu-id="bcfd8-181">Plugin target framework recommendations</span></span>

<span data-ttu-id="bcfd8-182">Ponieważ ładowanie zależności wtyczki używa pliku *. deps. JSON* , istnieje Gotcha powiązane z platformą docelową wtyczki.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-182">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="bcfd8-183">W związku z tym wtyczki powinny kierować do środowiska uruchomieniowego, takiego jak .NET Core 3,0, zamiast wersji .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-183">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="bcfd8-184">Plik *. deps. JSON* jest generowany na podstawie struktury docelowej projektu, a ponieważ wiele pakietów zgodnych z .NET Standard dostarcza zestawy referencyjne do kompilowania względem zestawów .NET Standard i implementacji dla określonych środowisk uruchomieniowych, plik *. deps. JSON* może nie być prawidłowo widoczny dla zestawów implementacji lub może odnieść się do .NET Standard wersji zestawu zamiast oczekiwanej wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcfd8-184">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>
