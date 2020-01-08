---
title: Jak utworzyć narzędzie globalne platformy .NET Core
description: Opisuje sposób tworzenia narzędzia globalnego. Narzędzie globalne jest aplikacją konsolową, która jest instalowana za pomocą interfejs wiersza polecenia platformy .NET Core.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 1daecf7234f02a5fe0dcf25cf7edbb0af327b8c1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343522"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="1625d-104">Tworzenie globalnego narzędzia platformy .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="1625d-104">Create a .NET Core Global Tool using the .NET Core CLI</span></span>

<span data-ttu-id="1625d-105">W tym artykule przedstawiono sposób tworzenia i pakowania globalnego narzędzia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1625d-105">This article teaches you how to create and package a .NET Core Global Tool.</span></span> <span data-ttu-id="1625d-106">Interfejs wiersza polecenia platformy .NET Core pozwala utworzyć aplikację konsolową jako narzędzie globalne, którą mogą łatwo instalować i uruchamiać inne osoby.</span><span class="sxs-lookup"><span data-stu-id="1625d-106">The .NET Core CLI allows you to create a console application as a Global Tool, which others can easily install and run.</span></span> <span data-ttu-id="1625d-107">Narzędzia globalne platformy .NET Core są pakietami NuGet, które są instalowane z interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1625d-107">.NET Core Global Tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="1625d-108">Aby uzyskać więcej informacji na temat narzędzi globalnych, zobacz [Omówienie narzędzi globalnych platformy .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1625d-108">For more information about Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a><span data-ttu-id="1625d-109">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="1625d-109">Create a project</span></span>

<span data-ttu-id="1625d-110">W tym artykule interfejs wiersza polecenia platformy .NET Core tworzenia projektu i zarządzania nim.</span><span class="sxs-lookup"><span data-stu-id="1625d-110">This article uses the .NET Core CLI to create and manage a project.</span></span>

<span data-ttu-id="1625d-111">Nasze przykładowe narzędzie będzie aplikacją konsolową, która generuje bot ASCII i drukuje komunikat.</span><span class="sxs-lookup"><span data-stu-id="1625d-111">Our example tool will be a console application that generates an ASCII bot and prints a message.</span></span> <span data-ttu-id="1625d-112">Najpierw utwórz nową aplikację konsolową platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1625d-112">First, create a new .NET Core Console Application.</span></span>

```dotnetcli
dotnet new console -o botsay
```

<span data-ttu-id="1625d-113">Przejdź do katalogu `botsay` utworzonego przez poprzednie polecenie.</span><span class="sxs-lookup"><span data-stu-id="1625d-113">Navigate to the `botsay` directory created by the previous command.</span></span>

## <a name="add-the-code"></a><span data-ttu-id="1625d-114">Dodawanie kodu</span><span class="sxs-lookup"><span data-stu-id="1625d-114">Add the code</span></span>

<span data-ttu-id="1625d-115">Otwórz plik `Program.cs` za pomocą ulubionego edytora tekstu, takiego jak `vim` lub [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="1625d-115">Open the `Program.cs` file with your favorite text editor, such as `vim` or [Visual Studio Code](https://code.visualstudio.com/).</span></span>

<span data-ttu-id="1625d-116">Dodaj następującą `using` dyrektywę na początku pliku, co pomaga skrócić kod w celu wyświetlenia informacji o wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1625d-116">Add the following `using` directive to the top of the file, this helps shorten the code to display the version information of the application.</span></span>

```csharp
using System.Reflection;
```

<span data-ttu-id="1625d-117">Następnie przejdź w dół do metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="1625d-117">Next, move down to the `Main` method.</span></span> <span data-ttu-id="1625d-118">Zastąp metodę poniższym kodem, aby przetworzyć argumenty wiersza polecenia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1625d-118">Replace the method with the following code to process the command-line arguments for your application.</span></span> <span data-ttu-id="1625d-119">Jeśli nie przekazano żadnych argumentów, zostanie wyświetlony krótki komunikat pomocy.</span><span class="sxs-lookup"><span data-stu-id="1625d-119">If no arguments were passed, a short help message is displayed.</span></span> <span data-ttu-id="1625d-120">W przeciwnym razie wszystkie te argumenty są przekształcane w ciąg i drukowane przy użyciu bot.</span><span class="sxs-lookup"><span data-stu-id="1625d-120">Otherwise, all of those arguments are transformed into a string and printed with the bot.</span></span>

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

### <a name="create-the-bot"></a><span data-ttu-id="1625d-121">Tworzenie bot</span><span class="sxs-lookup"><span data-stu-id="1625d-121">Create the bot</span></span>

<span data-ttu-id="1625d-122">Następnie Dodaj nową metodę o nazwie `ShowBot`, która przyjmuje parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="1625d-122">Next, add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="1625d-123">Ta metoda drukuje komunikat i bot ASCII.</span><span class="sxs-lookup"><span data-stu-id="1625d-123">This method prints out the message and the ASCII bot.</span></span> <span data-ttu-id="1625d-124">Kod bot ASCII został pobrany z przykładu [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) .</span><span class="sxs-lookup"><span data-stu-id="1625d-124">The ASCII bot code was taken from the [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) sample.</span></span>

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

### <a name="test-the-tool"></a><span data-ttu-id="1625d-125">Testowanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="1625d-125">Test the tool</span></span>

<span data-ttu-id="1625d-126">Uruchom projekt i zobacz dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="1625d-126">Run the project and see the output.</span></span> <span data-ttu-id="1625d-127">Wypróbuj te Wariacje w wierszu polecenia, aby zobaczyć różne wyniki:</span><span class="sxs-lookup"><span data-stu-id="1625d-127">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

<span data-ttu-id="1625d-128">Wszystkie argumenty po przekroczeniu ogranicznika `--` są przesyłane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1625d-128">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="set-up-the-global-tool"></a><span data-ttu-id="1625d-129">Konfigurowanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="1625d-129">Set up the global tool</span></span>

<span data-ttu-id="1625d-130">Przed spakowaniem i dystrybucją aplikacji jako narzędzia globalnego należy zmodyfikować plik projektu.</span><span class="sxs-lookup"><span data-stu-id="1625d-130">Before you can pack and distribute the application as a Global Tool, you need to modify the project file.</span></span> <span data-ttu-id="1625d-131">Otwórz plik `botsay.csproj` i Dodaj trzy nowe węzły XML do węzła `<Project><PropertyGroup>`:</span><span class="sxs-lookup"><span data-stu-id="1625d-131">Open the `botsay.csproj` file and add three new XML nodes to the `<Project><PropertyGroup>` node:</span></span>

- `<PackAsTool>`\
<span data-ttu-id="1625d-132">POTRZEB Wskazuje, że aplikacja zostanie spakowana do zainstalowania jako narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="1625d-132">[REQUIRED] Indicates that the application will be packaged for install as a Global Tool.</span></span>

- `<ToolCommandName>`\
<span data-ttu-id="1625d-133">OBOWIĄZKOWE Alternatywna nazwa narzędzia, w przeciwnym razie nazwa polecenia dla narzędzia będzie nazywana po pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="1625d-133">[OPTIONAL] An alternative name for the tool, otherwise the command name for the tool will be named after the project file.</span></span> <span data-ttu-id="1625d-134">W pakiecie można korzystać z wielu narzędzi, ale wybór unikatowej i przyjaznej nazwy ułatwia odróżnienie od innych narzędzi w tym samym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="1625d-134">You can have multiple tools in a package, choosing a unique and friendly name helps differentiate from other tools in the same package.</span></span>

- `<PackageOutputPath>`\
<span data-ttu-id="1625d-135">OBOWIĄZKOWE Miejsce, w którym zostanie utworzony pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="1625d-135">[OPTIONAL] Where the NuGet package will be produced.</span></span> <span data-ttu-id="1625d-136">Pakiet NuGet jest używany przez narzędzia globalne interfejs wiersza polecenia platformy .NET Core do instalowania narzędzia.</span><span class="sxs-lookup"><span data-stu-id="1625d-136">The NuGet package is what the .NET Core CLI Global Tools uses to install your tool.</span></span>

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

<span data-ttu-id="1625d-137">Mimo że `<PackageOutputPath>` jest opcjonalne, użyj go w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1625d-137">Even though `<PackageOutputPath>` is optional, use it in this example.</span></span> <span data-ttu-id="1625d-138">Upewnij się, że została ustawiona: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span><span class="sxs-lookup"><span data-stu-id="1625d-138">Make sure you set it: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span></span>

<span data-ttu-id="1625d-139">Następnie Utwórz pakiet NuGet dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1625d-139">Next, create a NuGet package for your application.</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="1625d-140">Plik `botsay.1.0.0.nupkg` jest tworzony w folderze identyfikowanym przez `<PackageOutputPath>` wartość XML z pliku `botsay.csproj`, który w tym przykładzie jest folderem `./nupkg`.</span><span class="sxs-lookup"><span data-stu-id="1625d-140">The `botsay.1.0.0.nupkg` file is created in the folder identified by the `<PackageOutputPath>` XML value from the `botsay.csproj` file, which in this example is the `./nupkg` folder.</span></span> <span data-ttu-id="1625d-141">Ułatwia to Instalowanie i testowanie.</span><span class="sxs-lookup"><span data-stu-id="1625d-141">This makes it easy to install and test.</span></span> <span data-ttu-id="1625d-142">Jeśli chcesz publicznie wydać narzędzie, przekaż je do <https://www.nuget.org>.</span><span class="sxs-lookup"><span data-stu-id="1625d-142">When you want to release a tool publicly, upload it to <https://www.nuget.org>.</span></span> <span data-ttu-id="1625d-143">Po udostępnieniu narzędzia w narzędziu NuGet deweloperzy mogą wykonać instalację narzędzia przy użyciu opcji `--global` narzędzia [dotnet](dotnet-tool-install.md) .</span><span class="sxs-lookup"><span data-stu-id="1625d-143">Once the tool is available on NuGet, developers can perform a user-wide installation of the tool using the `--global` option of the [dotnet tool install](dotnet-tool-install.md) command.</span></span>

<span data-ttu-id="1625d-144">Teraz, gdy masz pakiet, zainstaluj narzędzie z tego pakietu:</span><span class="sxs-lookup"><span data-stu-id="1625d-144">Now that you have a package, install the tool from that package:</span></span>

```dotnetcli
dotnet tool install --global --add-source ./nupkg botsay
```

<span data-ttu-id="1625d-145">`--add-source` parametr informuje interfejs wiersza polecenia platformy .NET Core o tymczasowym użyciu folderu `./nupkg` (nasz folder `<PackageOutputPath>`) jako dodatkowego źródła strumieniowego dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="1625d-145">The `--add-source` parameter tells the .NET Core CLI to temporarily use the `./nupkg` folder (our `<PackageOutputPath>` folder) as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="1625d-146">Aby uzyskać więcej informacji na temat instalowania narzędzi globalnych, zobacz [Omówienie narzędzi globalnych platformy .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1625d-146">For more information about installing Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

<span data-ttu-id="1625d-147">Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem, które służy do wywoływania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1625d-147">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

<span data-ttu-id="1625d-148">Teraz powinno być możliwe wpisanie `botsay` i uzyskanie odpowiedzi z narzędzia.</span><span class="sxs-lookup"><span data-stu-id="1625d-148">You should now be able to type `botsay` and get a response from the tool.</span></span>

> [!NOTE]
> <span data-ttu-id="1625d-149">Jeśli instalacja zakończyła się pomyślnie, ale nie można użyć `botsay` polecenia, może być konieczne otwarcie nowego terminalu w celu odświeżenia ścieżki.</span><span class="sxs-lookup"><span data-stu-id="1625d-149">If the install was successful, but you cannot use the `botsay` command, you may need to open a new terminal to refresh the PATH.</span></span>

## <a name="remove-the-tool"></a><span data-ttu-id="1625d-150">Usuń narzędzie</span><span class="sxs-lookup"><span data-stu-id="1625d-150">Remove the tool</span></span>

<span data-ttu-id="1625d-151">Po zakończeniu eksperymentowania z narzędziem można je usunąć za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="1625d-151">Once you're done experimenting with the tool, you can remove it with the following command:</span></span>

```dotnetcli
dotnet tool uninstall -g botsay
```
