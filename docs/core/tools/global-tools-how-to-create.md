---
title: Jak utworzyć narzędzie globalnej platformy .NET Core
description: Opisuje sposób tworzenia narzędzie globalne. Narzędzie globalnej jest aplikacja konsolowa która instaluje się za pośrednictwem interfejsu wiersza polecenia platformy .NET Core.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 1ad3e5c585cbfcaecb7a4d04de068273ef240763
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991158"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="db87a-104">Utworzyć narzędzie globalnej platformy .NET Core przy użyciu interfejsu wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="db87a-104">Create a .NET Core Global Tool using the .NET Core CLI</span></span>

<span data-ttu-id="db87a-105">Ten artykuł nauczy Cię sposobu tworzenia i pakietu Narzędzia globalnej Core środowiska .NET.</span><span class="sxs-lookup"><span data-stu-id="db87a-105">This article teaches you how to create and package a .NET Core Global Tool.</span></span> <span data-ttu-id="db87a-106">Interfejs wiersza polecenia platformy .NET Core umożliwia tworzenie aplikacji konsoli jako globalne narzędzia, które inne osoby można łatwo zainstalować i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="db87a-106">The .NET Core CLI allows you to create a console application as a Global Tool, which others can easily install and run.</span></span> <span data-ttu-id="db87a-107">Narzędzia programu .NET core globalne są pakiety NuGet, które są instalowane z interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="db87a-107">.NET Core Global Tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="db87a-108">Aby uzyskać więcej informacji na temat narzędzia globalnej zobacz [Omówienie narzędzia globalnej platformy .NET Core][global-tool-info].</span><span class="sxs-lookup"><span data-stu-id="db87a-108">For more information about Global Tools, see [.NET Core Global Tools overview][global-tool-info].</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a><span data-ttu-id="db87a-109">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="db87a-109">Create a project</span></span>

<span data-ttu-id="db87a-110">W tym artykule używa interfejsu wiersza polecenia platformy .NET Core do tworzenia i zarządzania projektem.</span><span class="sxs-lookup"><span data-stu-id="db87a-110">This article uses the .NET Core CLI to create and manage a project.</span></span>

<span data-ttu-id="db87a-111">Narzędzie naszym przykładzie będzie aplikację konsolową która generuje bot ASCII i drukuje wiadomość.</span><span class="sxs-lookup"><span data-stu-id="db87a-111">Our example tool will be a console application that generates an ASCII bot and prints a message.</span></span> <span data-ttu-id="db87a-112">Najpierw utwórz nową aplikację Konsolową .NET Core.</span><span class="sxs-lookup"><span data-stu-id="db87a-112">First, create a new .NET Core Console Application.</span></span>

```console
dotnet new console -o botsay
```

<span data-ttu-id="db87a-113">Przejdź do `botsay` Katalog utworzony przez poprzednie polecenie.</span><span class="sxs-lookup"><span data-stu-id="db87a-113">Navigate to the `botsay` directory created by the previous command.</span></span>

## <a name="add-the-code"></a><span data-ttu-id="db87a-114">Dodaj kod</span><span class="sxs-lookup"><span data-stu-id="db87a-114">Add the code</span></span>

<span data-ttu-id="db87a-115">Otwórz `Program.cs` plików za pomocą ulubionego edytora tekstu, takie jak `vim` lub [programu Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="db87a-115">Open the `Program.cs` file with your favorite text editor, such as `vim` or [Visual Studio Code](https://code.visualstudio.com/).</span></span>

<span data-ttu-id="db87a-116">Dodaj następujący kod `using` dyrektywy do górnej części pliku, pomoże skrócić kod, aby wyświetlić informacje o wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db87a-116">Add the following `using` directive to the top of the file, this helps shorten the code to display the version information of the application.</span></span>

```csharp
using System.Reflection;
```

<span data-ttu-id="db87a-117">Następnie Przenieś w dół do `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="db87a-117">Next, move down to the `Main` method.</span></span> <span data-ttu-id="db87a-118">Zastąp metodę następujący kod, aby przetworzyć argumenty wiersza polecenia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db87a-118">Replace the method with the following code to process the command-line arguments for your application.</span></span> <span data-ttu-id="db87a-119">Jeśli nie przekazano argumentów, jest wyświetlany komunikat pomocy krótki.</span><span class="sxs-lookup"><span data-stu-id="db87a-119">If no arguments were passed, a short help message is displayed.</span></span> <span data-ttu-id="db87a-120">W przeciwnym razie tych argumentów są przekształcane na ciąg i drukowania z botami.</span><span class="sxs-lookup"><span data-stu-id="db87a-120">Otherwise, all of those arguments are transformed into a string and printed with the bot.</span></span>

```csharp
static void Main(string[] args)
{
    if (args.Length == 0)
    {
        var versionString = Assembly.GetEntryAssembly()
                                .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                .InformationalVersion
                                .ToString();
                                
        Console.WriteLine($"botsay v{versionString}");
        Console.WriteLine("-------------");
        Console.WriteLine("\nUsage:");
        Console.WriteLine("  botsay <message>");
        return;
    }

    ShowBot(string.Join(' ', args));
}
```

### <a name="create-the-bot"></a><span data-ttu-id="db87a-121">Utwórz bota</span><span class="sxs-lookup"><span data-stu-id="db87a-121">Create the bot</span></span>

<span data-ttu-id="db87a-122">Następnie dodaj nową metodę o nazwie `ShowBot` przyjmującą parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="db87a-122">Next, add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="db87a-123">Ta metoda drukuje wiadomość i ASCII bot.</span><span class="sxs-lookup"><span data-stu-id="db87a-123">This method prints out the message and the ASCII bot.</span></span> <span data-ttu-id="db87a-124">W kodzie bot ASCII została pobrana z [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) próbki.</span><span class="sxs-lookup"><span data-stu-id="db87a-124">The ASCII bot code was taken from the [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) sample.</span></span>

```csharp
static void ShowBot(string message)
{
    string bot = $"\n        {message}";
    bot += @"
    __________________
                      \
                       \
                          ....
                          ....'
                           ....
                        ..........
                    .............'..'..
                 ................'..'.....
               .......'..........'..'..'....
              ........'..........'..'..'.....
             .'....'..'..........'..'.......'.
             .'..................'...   ......
             .  ......'.........         .....
             .    _            __        ......
            ..    #            ##        ......
           ....       .                 .......
           ......  .......          ............
            ................  ......................
            ........................'................
           ......................'..'......    .......
        .........................'..'.....       .......
     ........    ..'.............'..'....      ..........
   ..'..'...      ...............'.......      ..........
  ...'......     ...... ..........  ......         .......
 ...........   .......              ........        ......
.......        '...'.'.              '.'.'.'         ....
.......       .....'..               ..'.....
   ..       ..........               ..'........
          ............               ..............
         .............               '..............
        ...........'..              .'.'............
       ...............              .'.'.............
      .............'..               ..'..'...........
      ...............                 .'..............
       .........                        ..............
        .....
";
    Console.WriteLine(bot);
}
```

### <a name="test-the-tool"></a><span data-ttu-id="db87a-125">Narzędzia testowania</span><span class="sxs-lookup"><span data-stu-id="db87a-125">Test the tool</span></span>

<span data-ttu-id="db87a-126">Uruchom projekt i wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="db87a-126">Run the project and see the output.</span></span> <span data-ttu-id="db87a-127">Wypróbuj te zmiany z wiersza polecenia, aby wyświetlić różne wyniki:</span><span class="sxs-lookup"><span data-stu-id="db87a-127">Try these variations of the command-line to see different results:</span></span>

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

<span data-ttu-id="db87a-128">Wszystkie argumenty po `--` ogranicznik są przekazywane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db87a-128">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="setup-the-global-tool"></a><span data-ttu-id="db87a-129">Ustawienia globalne narzędzia</span><span class="sxs-lookup"><span data-stu-id="db87a-129">Setup the global tool</span></span>

<span data-ttu-id="db87a-130">Przed dodatkiem Service pack i dystrybucji aplikacji jako globalne narzędzie, należy zmodyfikować plik projektu.</span><span class="sxs-lookup"><span data-stu-id="db87a-130">Before you can pack and distribute the application as a Global Tool, you need to modify the project file.</span></span> <span data-ttu-id="db87a-131">Otwórz `botsay.csproj` pliku i Dodaj trzy nowe węzły XML do `<Project><PropertyGroup>` węzła:</span><span class="sxs-lookup"><span data-stu-id="db87a-131">Open the `botsay.csproj` file and add three new XML nodes to the `<Project><PropertyGroup>` node:</span></span>

- `<PackAsTool>`  
<span data-ttu-id="db87a-132">[WYMAGANE] Wskazuje, że aplikacja zostanie umieszczony w pakiecie do zainstalowania narzędzia globalnej.</span><span class="sxs-lookup"><span data-stu-id="db87a-132">[REQUIRED] Indicates that the application will be packaged for install as a Global Tool.</span></span>

- `<ToolCommandName>`  
<span data-ttu-id="db87a-133">[OPCJONALNIE] Alternatywna nazwa narzędzia, w przeciwnym razie nazwa polecenia dla narzędzia będzie identyczna z nazwą pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="db87a-133">[OPTIONAL] An alternative name for the tool, otherwise the command name for the tool will be named after the project file.</span></span> <span data-ttu-id="db87a-134">W pakiecie, wybierając unikatową przyjazną nazwą pomaga odróżnić od innych narzędzi, w tym samym pakiecie, może mieć wielu narzędzi.</span><span class="sxs-lookup"><span data-stu-id="db87a-134">You can have multiple tools in a package, choosing a unique and friendly name helps differentiate from other tools in the same package.</span></span>

- `<PackageOutputPath>`  
<span data-ttu-id="db87a-135">[OPCJONALNIE] Gdzie będą opracowywane pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="db87a-135">[OPTIONAL] Where the NuGet package will be produced.</span></span> <span data-ttu-id="db87a-136">Pakiet NuGet jest narzędzia globalnej interfejsu wiersza polecenia platformy .NET Core używa Aby zainstalować narzędzie.</span><span class="sxs-lookup"><span data-stu-id="db87a-136">The NuGet package is what the .NET Core CLI Global Tools uses to install your tool.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

<span data-ttu-id="db87a-137">Mimo że `<PackageOutputPath>` jest opcjonalny, użyj go w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="db87a-137">Even though `<PackageOutputPath>` is optional, use it in this example.</span></span> <span data-ttu-id="db87a-138">Upewnij się, że jest on ustawiany: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span><span class="sxs-lookup"><span data-stu-id="db87a-138">Make sure you set it: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span></span>

<span data-ttu-id="db87a-139">Następnie należy utworzyć pakiet NuGet na potrzeby aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db87a-139">Next, create a NuGet package for your application.</span></span>

```console
dotnet pack
```

<span data-ttu-id="db87a-140">`botsay.1.0.0.nupkg` Plik jest tworzony w folderze identyfikowane przez `<PackageOutputPath>` wartość XML z `botsay.csproj` pliku, który w tym przykładzie jest `./nupkg` folderu.</span><span class="sxs-lookup"><span data-stu-id="db87a-140">The `botsay.1.0.0.nupkg` file is created in the folder identified by the `<PackageOutputPath>` XML value from the `botsay.csproj` file, which in this example is the `./nupkg` folder.</span></span> <span data-ttu-id="db87a-141">Dzięki temu można łatwo zainstalować i przetestować.</span><span class="sxs-lookup"><span data-stu-id="db87a-141">This makes it easy to install and test.</span></span> <span data-ttu-id="db87a-142">W przypadku wersji narzędzia publicznie, przekaż go do [ https://www.nuget.org ](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="db87a-142">When you want to release a tool publicly, upload it to [https://www.nuget.org](https://www.nuget.org).</span></span>

<span data-ttu-id="db87a-143">Teraz, gdy pakiet, należy zainstalować narzędzia z tego pakietu:</span><span class="sxs-lookup"><span data-stu-id="db87a-143">Now that you have a package, install the tool from that package:</span></span> 

```console
dotnet tool install --global --add-source ./nupkg botsay`
```

<span data-ttu-id="db87a-144">`--add-source` Parametru informuje .NET Core interfejs wiersza polecenia i użyj tymczasowo `./nupkg` folder (nasze `<PackageOutputPath>` folder) jako źródło dodatkowych źródło danych dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="db87a-144">The `--add-source` parameter tells the .NET Core CLI to temporarily use the `./nupkg` folder (our `<PackageOutputPath>` folder) as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="db87a-145">Aby uzyskać więcej informacji na temat instalowania narzędzi globalnych, zobacz [Omówienie narzędzia globalnej platformy .NET Core][global-tool-info].</span><span class="sxs-lookup"><span data-stu-id="db87a-145">For more information about installing Global Tools, see [.NET Core Global Tools overview][global-tool-info].</span></span>

<span data-ttu-id="db87a-146">Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat przedstawiający polecenia używane do wywoływania narzędzia i wersją zainstalowaną, podobny do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="db87a-146">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

<span data-ttu-id="db87a-147">Teraz powinno być możliwe do wpisania `botsay` i uzyskać odpowiedzi z narzędzia.</span><span class="sxs-lookup"><span data-stu-id="db87a-147">You should now be able to type `botsay` and get a response from the tool.</span></span>

> [!NOTE]
> <span data-ttu-id="db87a-148">Jeśli instalacja zakończyła się pomyślnie, ale nie można użyć `botsay` polecenia, może być konieczne otwarcie nowym terminalu, aby odświeżyć ścieżki.</span><span class="sxs-lookup"><span data-stu-id="db87a-148">If the install was successful, but you cannot use the `botsay` command, you may need to open a new terminal to refresh the PATH.</span></span>

## <a name="remove-the-tool"></a><span data-ttu-id="db87a-149">Usuń narzędzie</span><span class="sxs-lookup"><span data-stu-id="db87a-149">Remove the tool</span></span>

<span data-ttu-id="db87a-150">Po zakończeniu eksperymentowanie, za pomocą narzędzia, możesz je usunąć za pomocą następujących commnand:</span><span class="sxs-lookup"><span data-stu-id="db87a-150">Once you're done experimenting with the tool, you can remove it with the following commnand:</span></span>

```console
dotnet tool uninstall -g botsay
```

[global-tool-info]: global-tools.md