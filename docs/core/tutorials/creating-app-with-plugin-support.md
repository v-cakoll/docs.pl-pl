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
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="068d4-103">Tworzenie aplikacji platformy .NET Core za pomocą wtyczek</span><span class="sxs-lookup"><span data-stu-id="068d4-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="068d4-104">W tym samouczku pokazano, jak utworzyć niestandardowe, <xref:System.Runtime.Loader.AssemblyLoadContext> aby załadować wtyczki.</span><span class="sxs-lookup"><span data-stu-id="068d4-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="068d4-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> służy do rozwiązywania zależności wtyczki.</span><span class="sxs-lookup"><span data-stu-id="068d4-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="068d4-106">Samouczek poprawnie izoluje zależności wtyczki od aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="068d4-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="068d4-107">Omawiane tematy:</span><span class="sxs-lookup"><span data-stu-id="068d4-107">You'll learn how to:</span></span>

- <span data-ttu-id="068d4-108">Struktura projektu do obsługi wtyczek.</span><span class="sxs-lookup"><span data-stu-id="068d4-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="068d4-109">Utwórz <xref:System.Runtime.Loader.AssemblyLoadContext> niestandardowy, aby załadować każdą wtyczkę.</span><span class="sxs-lookup"><span data-stu-id="068d4-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="068d4-110">Użyj <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> tego typu, aby zezwolić wtyczkom na zależności.</span><span class="sxs-lookup"><span data-stu-id="068d4-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="068d4-111">Autor wtyczek, które można łatwo wdrożyć, po prostu kopiując artefakty kompilacji.</span><span class="sxs-lookup"><span data-stu-id="068d4-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="068d4-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="068d4-112">Prerequisites</span></span>

- <span data-ttu-id="068d4-113">Zainstaluj [zestaw SDK .NET Core 3.0](https://dotnet.microsoft.com/download) lub nowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="068d4-113">Install the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="068d4-114">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="068d4-114">Create the application</span></span>

<span data-ttu-id="068d4-115">Pierwszym krokiem jest utworzenie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="068d4-115">The first step is to create the application:</span></span>

1. <span data-ttu-id="068d4-116">Utwórz nowy folder, a w tym folderze uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="068d4-116">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="068d4-117">Aby ułatwić tworzenie projektu, utwórz plik rozwiązania programu Visual Studio w tym samym folderze.</span><span class="sxs-lookup"><span data-stu-id="068d4-117">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="068d4-118">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="068d4-118">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="068d4-119">Uruchom następujące polecenie, aby dodać projekt aplikacji do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="068d4-119">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="068d4-120">Teraz możemy wypełnić szkielet naszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="068d4-120">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="068d4-121">Zamień kod w pliku *AppWithPlugin/Program.cs* na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="068d4-121">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="068d4-122">Tworzenie interfejsów wtyczek</span><span class="sxs-lookup"><span data-stu-id="068d4-122">Create the plugin interfaces</span></span>

<span data-ttu-id="068d4-123">Następnym krokiem w tworzeniu aplikacji z wtyczkami jest definiowanie interfejsu, który wtyczki muszą zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="068d4-123">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="068d4-124">Sugerujemy, aby stworzyć bibliotekę klas, która zawiera wszystkie typy, które mają być używane do komunikowania się między aplikacją a wtyczkami.</span><span class="sxs-lookup"><span data-stu-id="068d4-124">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="068d4-125">Ten podział pozwala na opublikowanie interfejsu wtyczki jako pakiet bez konieczności wysyłki pełnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="068d4-125">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="068d4-126">W folderze głównym projektu `dotnet new classlib -o PluginBase`uruchom .</span><span class="sxs-lookup"><span data-stu-id="068d4-126">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="068d4-127">Ponadto uruchom, `dotnet sln add PluginBase/PluginBase.csproj` aby dodać projekt do pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="068d4-127">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="068d4-128">Usuń `PluginBase/Class1.cs` plik i utwórz nowy `PluginBase` plik `ICommand.cs` w folderze o nazwie z następującą definicją interfejsu:</span><span class="sxs-lookup"><span data-stu-id="068d4-128">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

<span data-ttu-id="068d4-129">Ten `ICommand` interfejs jest interfejsem, który zaimplementują wszystkie wtyczki.</span><span class="sxs-lookup"><span data-stu-id="068d4-129">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="068d4-130">Teraz, `ICommand` gdy interfejs jest zdefiniowany, projekt aplikacji można wypełnić trochę więcej.</span><span class="sxs-lookup"><span data-stu-id="068d4-130">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="068d4-131">Dodaj odwołanie z `AppWithPlugin` projektu `PluginBase` do projektu `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` za pomocą polecenia z folderu głównego.</span><span class="sxs-lookup"><span data-stu-id="068d4-131">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="068d4-132">Zastąp `// Load commands from plugins` komentarz następującym fragmentem kodu, aby umożliwić ładowanie wtyczek z podanych ścieżek plików:</span><span class="sxs-lookup"><span data-stu-id="068d4-132">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="068d4-133">Następnie zastąp `// Output the loaded commands` komentarz następującym fragmentem kodu:</span><span class="sxs-lookup"><span data-stu-id="068d4-133">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="068d4-134">Zastąp `// Execute the command with the name passed as an argument` komentarz następującym fragmentem kodu:</span><span class="sxs-lookup"><span data-stu-id="068d4-134">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="068d4-135">I na koniec dodaj metody `Program` statyczne `LoadPlugin` `CreateCommands`do klasy o nazwie i , jak pokazano tutaj:</span><span class="sxs-lookup"><span data-stu-id="068d4-135">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="068d4-136">Wtyczki ładowania</span><span class="sxs-lookup"><span data-stu-id="068d4-136">Load plugins</span></span>

<span data-ttu-id="068d4-137">Teraz aplikacja może poprawnie ładować i tworzyć polecenia z załadowanych zestawów wtyczek, ale nadal nie jest w stanie załadować zestawów wtyczek.</span><span class="sxs-lookup"><span data-stu-id="068d4-137">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="068d4-138">Utwórz plik o nazwie *PluginLoadContext.cs* w folderze *AppWithPlugin* o następującej zawartości:</span><span class="sxs-lookup"><span data-stu-id="068d4-138">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="068d4-139">Typ `PluginLoadContext` pochodzi od <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="068d4-139">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="068d4-140">Typ `AssemblyLoadContext` jest specjalnym typem w czasie wykonywania, który umożliwia deweloperom izolowanie załadowanych zestawów do różnych grup, aby upewnić się, że wersje zestawu nie są w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="068d4-140">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="068d4-141">Ponadto niestandardowe `AssemblyLoadContext` można wybrać różne ścieżki do ładowania zestawów z i zastąpić zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="068d4-141">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="068d4-142">Używa `PluginLoadContext` wystąpienia typu `AssemblyDependencyResolver` wprowadzonego w .NET Core 3.0 do rozpoznawania nazw zestawów do ścieżek.</span><span class="sxs-lookup"><span data-stu-id="068d4-142">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="068d4-143">Obiekt `AssemblyDependencyResolver` jest konstruowany ze ścieżką do biblioteki klas .NET.</span><span class="sxs-lookup"><span data-stu-id="068d4-143">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="068d4-144">Rozwiązuje zestawy i biblioteki macierzyste do ich ścieżek względnych na podstawie pliku *.deps.json* dla biblioteki klas, których ścieżka została przekazana do `AssemblyDependencyResolver` konstruktora.</span><span class="sxs-lookup"><span data-stu-id="068d4-144">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="068d4-145">Custom `AssemblyLoadContext` umożliwia wtyczki mają własne zależności i `AssemblyDependencyResolver` sprawia, że łatwo poprawnie załadować zależności.</span><span class="sxs-lookup"><span data-stu-id="068d4-145">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="068d4-146">Teraz, `AppWithPlugin` gdy projekt `PluginLoadContext` ma typ, zaktualizuj `Program.LoadPlugin` metodę o następującej treści:</span><span class="sxs-lookup"><span data-stu-id="068d4-146">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="068d4-147">Za pomocą `PluginLoadContext` innego wystąpienia dla każdej wtyczki, wtyczki mogą mieć różne lub nawet konflikty zależności bez problemu.</span><span class="sxs-lookup"><span data-stu-id="068d4-147">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="068d4-148">Prosta wtyczka bez zależności</span><span class="sxs-lookup"><span data-stu-id="068d4-148">Simple plugin with no dependencies</span></span>

<span data-ttu-id="068d4-149">W folderze głównym wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="068d4-149">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="068d4-150">Uruchom następujące polecenie, aby utworzyć nowy `HelloPlugin`projekt biblioteki klas o nazwie:</span><span class="sxs-lookup"><span data-stu-id="068d4-150">Run the following command to create a new class library project named `HelloPlugin`:</span></span>

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="068d4-151">Uruchom następujące polecenie, aby dodać `AppWithPlugin` projekt do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="068d4-151">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="068d4-152">Zamień plik *HelloPlugin/Class1.cs* na plik o nazwie *HelloCommand.cs* na następującą zawartość:</span><span class="sxs-lookup"><span data-stu-id="068d4-152">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="068d4-153">Teraz otwórz plik *HelloPlugin.csproj.*</span><span class="sxs-lookup"><span data-stu-id="068d4-153">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="068d4-154">Zawartość okna powinna wyglądać mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="068d4-154">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="068d4-155">Pomiędzy `<Project>` znacznikami dodaj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="068d4-155">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

<span data-ttu-id="068d4-156">Element `<Private>false</Private>` jest ważny.</span><span class="sxs-lookup"><span data-stu-id="068d4-156">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="068d4-157">Informuje to msbuild, aby nie kopiować *pliku PluginBase.dll* do katalogu wyjściowego helloplugin.</span><span class="sxs-lookup"><span data-stu-id="068d4-157">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="068d4-158">Jeśli zestaw *Dll PluginBase.dll* jest `PluginLoadContext` obecny w katalogu wyjściowym, znajdzie tam zestaw i załaduje go podczas ładowania zestawu *HelloPlugin.dll.*</span><span class="sxs-lookup"><span data-stu-id="068d4-158">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="068d4-159">W tym momencie `HelloPlugin.HelloCommand` `ICommand` typ zaimplementuje interfejs z pliku *PluginBase.dll* w katalogu wyjściowym `HelloPlugin` projektu, a `ICommand` nie interfejs, który jest ładowany do domyślnego kontekstu ładowania.</span><span class="sxs-lookup"><span data-stu-id="068d4-159">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="068d4-160">Ponieważ czas wykonywania widzi te dwa typy jako `AppWithPlugin.Program.CreateCommands` różne typy z różnych zestawów, metoda nie znajdzie poleceń.</span><span class="sxs-lookup"><span data-stu-id="068d4-160">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="068d4-161">W rezultacie `<Private>false</Private>` metadane są wymagane dla odwołania do zestawu zawierającego interfejsy wtyczki.</span><span class="sxs-lookup"><span data-stu-id="068d4-161">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="068d4-162">Podobnie `<ExcludeAssets>runtime</ExcludeAssets>` element jest również ważne, `PluginBase` jeśli odwołuje się do innych pakietów.</span><span class="sxs-lookup"><span data-stu-id="068d4-162">Similarly, the `<ExcludeAssets>runtime</ExcludeAssets>` element is also important if the `PluginBase` references other packages.</span></span> <span data-ttu-id="068d4-163">To ustawienie ma taki `<Private>false</Private>` sam efekt jak, `PluginBase` ale działa na odwołania do pakietu, które może zawierać projekt lub jeden z jego zależności.</span><span class="sxs-lookup"><span data-stu-id="068d4-163">This setting has the same effect as `<Private>false</Private>` but works on package references that the `PluginBase` project or one of its dependencies may include.</span></span>

<span data-ttu-id="068d4-164">Po zakończeniu `HelloPlugin` projektu należy zaktualizować `AppWithPlugin` projekt, aby `HelloPlugin` wiedzieć, gdzie można znaleźć wtyczkę.</span><span class="sxs-lookup"><span data-stu-id="068d4-164">Now that the `HelloPlugin` project is complete, you should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="068d4-165">Po `// Paths to plugins to load` komentarzu `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` dodaj jako element `pluginPaths` tablicy.</span><span class="sxs-lookup"><span data-stu-id="068d4-165">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="068d4-166">Wtyczka z zależnościami biblioteki</span><span class="sxs-lookup"><span data-stu-id="068d4-166">Plugin with library dependencies</span></span>

<span data-ttu-id="068d4-167">Prawie wszystkie wtyczki są bardziej złożone niż prosty "Hello World", a wiele wtyczek ma zależności od innych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="068d4-167">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="068d4-168">Projekty `JsonPlugin` `OldJson` i wtyczki w przykładzie pokazują dwa przykłady wtyczek z `Newtonsoft.Json`zależnościami pakietów NuGet na .</span><span class="sxs-lookup"><span data-stu-id="068d4-168">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="068d4-169">Same pliki projektu nie mają żadnych specjalnych informacji dla odwołań do projektu, `pluginPaths` a (po dodaniu ścieżek wtyczki do tablicy) wtyczki działają idealnie, nawet jeśli są uruchamiane w tym samym wykonaniu aplikacji AppWithPlugin.</span><span class="sxs-lookup"><span data-stu-id="068d4-169">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="068d4-170">Jednak te projekty nie kopiują zestawów, do których istnieje odwołanie, do ich katalogu wyjściowego, więc zestawy muszą być obecne na komputerze użytkownika, aby wtyczki działały.</span><span class="sxs-lookup"><span data-stu-id="068d4-170">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="068d4-171">Istnieją dwa sposoby obejścia tego problemu.</span><span class="sxs-lookup"><span data-stu-id="068d4-171">There are two ways to work around this problem.</span></span> <span data-ttu-id="068d4-172">Pierwszą opcją jest `dotnet publish` użycie polecenia do opublikowania biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="068d4-172">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="068d4-173">Alternatywnie, jeśli chcesz mieć możliwość korzystania `dotnet build` z danych wyjściowych dla `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` wtyczki, `<PropertyGroup>` możesz dodać właściwość między tagami w pliku projektu wtyczki.</span><span class="sxs-lookup"><span data-stu-id="068d4-173">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="068d4-174">Zobacz `XcopyablePlugin` projekt wtyczki na przykład.</span><span class="sxs-lookup"><span data-stu-id="068d4-174">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="068d4-175">Inne przykłady w próbce</span><span class="sxs-lookup"><span data-stu-id="068d4-175">Other examples in the sample</span></span>

<span data-ttu-id="068d4-176">Pełny kod źródłowy dla tego samouczka można znaleźć w [repozytorium dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="068d4-176">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="068d4-177">Ukończony przykład zawiera kilka innych `AssemblyDependencyResolver` przykładów zachowania.</span><span class="sxs-lookup"><span data-stu-id="068d4-177">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="068d4-178">Na przykład `AssemblyDependencyResolver` obiekt może również rozpoznać natywnych bibliotek, a także zlokalizowane zestawy satelickie zawarte w pakietach NuGet.</span><span class="sxs-lookup"><span data-stu-id="068d4-178">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="068d4-179">I `UVPlugin` `FrenchPlugin` w repozytorium próbek demonstrować te scenariusze.</span><span class="sxs-lookup"><span data-stu-id="068d4-179">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a><span data-ttu-id="068d4-180">Odwoływanie się do interfejsu wtyczki z pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="068d4-180">Reference a plugin interface from a NuGet package</span></span>

<span data-ttu-id="068d4-181">Załóżmy, że istnieje aplikacja A, która ma interfejs wtyczki zdefiniowany w pakiecie NuGet o nazwie `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="068d4-181">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="068d4-182">Jak poprawnie odwołać się do pakietu w projekcie wtyczki?</span><span class="sxs-lookup"><span data-stu-id="068d4-182">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="068d4-183">W przypadku odwołań `<Private>false</Private>` do projektu `ProjectReference` użycie metadanych w elemencie w pliku projektu uniemożliwiło kopiowanie dll do danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="068d4-183">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="068d4-184">Aby poprawnie odwołać się do `A.PluginBase` pakietu, chcesz zmienić `<PackageReference>` element w pliku projektu na następujący:</span><span class="sxs-lookup"><span data-stu-id="068d4-184">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="068d4-185">Zapobiega to `A.PluginBase` kopiowaniu zestawów do katalogu wyjściowego wtyczki i zapewnia, że wtyczka będzie `A.PluginBase`korzystać z wersji A .</span><span class="sxs-lookup"><span data-stu-id="068d4-185">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="068d4-186">Zalecenia dotyczące struktury docelowej wtyczki</span><span class="sxs-lookup"><span data-stu-id="068d4-186">Plugin target framework recommendations</span></span>

<span data-ttu-id="068d4-187">Ponieważ ładowanie zależności wtyczki używa pliku *.deps.json,* istnieje gotcha związane z platformą docelową wtyczki.</span><span class="sxs-lookup"><span data-stu-id="068d4-187">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="068d4-188">W szczególności wtyczki powinny być przeznaczone dla czasu wykonywania, takich jak .NET Core 3.0, zamiast wersji .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="068d4-188">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="068d4-189">Plik *.deps.json* jest generowany na podstawie struktury, której jest przeznaczony dla projektu, a ponieważ wiele pakietów zgodnych ze standardem .NET wysyła zestawy referencyjne do tworzenia względem standardu .NET i zestawów implementacji dla określonych środowiskauruchomieniowego, *zestawy .deps.json* mogą nie poprawnie widzieć zestawów implementacji lub może pobrać standardową wersję zestawu .NET zamiast oczekiwaną wersję .NET Core.</span><span class="sxs-lookup"><span data-stu-id="068d4-189">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>

## <a name="plugin-framework-references"></a><span data-ttu-id="068d4-190">Odwołania do struktury wtyczek</span><span class="sxs-lookup"><span data-stu-id="068d4-190">Plugin framework references</span></span>

<span data-ttu-id="068d4-191">Obecnie wtyczki nie mogą wprowadzać nowych struktur do procesu.</span><span class="sxs-lookup"><span data-stu-id="068d4-191">Currently, plugins can't introduce new frameworks into the process.</span></span> <span data-ttu-id="068d4-192">Na przykład nie można załadować wtyczki, `Microsoft.AspNetCore.App` która używa struktury do `Microsoft.NETCore.App` aplikacji, która używa tylko struktury głównej.</span><span class="sxs-lookup"><span data-stu-id="068d4-192">For example, you can't load a plugin that uses the `Microsoft.AspNetCore.App` framework into an application that only uses the root `Microsoft.NETCore.App` framework.</span></span> <span data-ttu-id="068d4-193">Aplikacja hosta musi zadeklarować odwołania do wszystkich struktur wymaganych przez wtyczki.</span><span class="sxs-lookup"><span data-stu-id="068d4-193">The host application must declare references to all frameworks needed by plugins.</span></span>
