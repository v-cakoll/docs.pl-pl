---
title: 'Samouczek: Tworzenie narzędzia .NET Core'
description: Dowiedz się, jak utworzyć narzędzie .NET Core. Narzędzie to aplikacja konsoli zainstalowana przy użyciu interfejsu CLI .NET Core.
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156728"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a><span data-ttu-id="fa1f8-104">Samouczek: Tworzenie narzędzia .NET Core przy użyciu procesora CLI programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="fa1f8-104">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>

<span data-ttu-id="fa1f8-105">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="fa1f8-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="fa1f8-106">W tym samouczku nauczycię, jak utworzyć i spakować narzędzie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-106">This tutorial teaches you how to create and package a .NET Core tool.</span></span> <span data-ttu-id="fa1f8-107">Interfejs cli .NET Core umożliwia tworzenie aplikacji konsoli jako narzędzia, które inne osoby mogą instalować i uruchamiać.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-107">The .NET Core CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="fa1f8-108">Narzędzia .NET Core to pakiety NuGet zainstalowane z procesora CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-108">.NET Core tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="fa1f8-109">Aby uzyskać więcej informacji na temat narzędzi, zobacz [omówienie narzędzi programu .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="fa1f8-109">For more information about tools, see [.NET Core tools overview](global-tools.md).</span></span>

<span data-ttu-id="fa1f8-110">Narzędzie, które utworzysz, to aplikacja konsolowa, która przyjmuje komunikat jako dane wejściowe i wyświetla wiadomość wraz z wierszami tekstu, które tworzą obraz robota.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="fa1f8-111">Jest to pierwszy z serii trzech samouczków.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="fa1f8-112">W tym samouczku można utworzyć i spakować narzędzie.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="fa1f8-113">W następnych dwóch samouczkach [używasz tego narzędzia jako narzędzia globalnego](global-tools-how-to-use.md) i używasz tego narzędzia jako narzędzia [lokalnego.](local-tools-how-to-use.md)</span><span class="sxs-lookup"><span data-stu-id="fa1f8-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fa1f8-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fa1f8-114">Prerequisites</span></span>

- <span data-ttu-id="fa1f8-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) lub nowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="fa1f8-116">Ten samouczek i poniższy [samouczek dla narzędzi globalnych](global-tools-how-to-use.md) dotyczą .NET Core SDK 2.1 i nowszych wersji, ponieważ narzędzia globalne są dostępne począwszy od tej wersji.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="fa1f8-117">Ale ten poradnik zakłada, że masz zainstalowany 3.1 lub nowsze tak, że masz możliwość kontynuowania do [samouczka narzędzi lokalnych](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="fa1f8-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="fa1f8-118">Lokalne narzędzia są dostępne od .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="fa1f8-119">Procedury tworzenia narzędzia są takie same, niezależnie od tego, czy są używane jako narzędzie globalne, czy jako narzędzie lokalne.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="fa1f8-120">Wybrany edytor tekstu lub edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="fa1f8-121">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="fa1f8-121">Create a project</span></span>

1. <span data-ttu-id="fa1f8-122">Otwórz wiersz polecenia i utwórz folder o nazwie *repozytorium*.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="fa1f8-123">Przejdź do folderu *repozytorium* i wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="fa1f8-123">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   <span data-ttu-id="fa1f8-124">Polecenie tworzy nowy folder o nazwie *microsoft.botsay* w folderze *repozytorium.*</span><span class="sxs-lookup"><span data-stu-id="fa1f8-124">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

1. <span data-ttu-id="fa1f8-125">Przejdź do folderu *microsoft.botsay.*</span><span class="sxs-lookup"><span data-stu-id="fa1f8-125">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="fa1f8-126">Dodawanie kodu</span><span class="sxs-lookup"><span data-stu-id="fa1f8-126">Add the code</span></span>

1. <span data-ttu-id="fa1f8-127">Otwórz `Program.cs` plik za pomocą edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-127">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="fa1f8-128">Dodaj następującą `using` dyrektywę do górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="fa1f8-128">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="fa1f8-129">Zamień metodę na `Main` następujący kod, aby przetworzyć argumenty wiersza polecenia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-129">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="fa1f8-130">Jeśli nie zostaną przekazane żadne argumenty, zostanie wyświetlony krótki komunikat pomocy.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-130">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="fa1f8-131">W przeciwnym razie wszystkie argumenty są łączone w jeden ciąg `ShowBot` i drukowane przez wywołanie metody, która jest tworzona w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-131">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="fa1f8-132">Dodaj nową metodę `ShowBot` o nazwie, która przyjmuje parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-132">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="fa1f8-133">Metoda drukuje wiadomość i obraz robota za pomocą linii tekstu.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-133">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="fa1f8-134">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-134">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="fa1f8-135">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="fa1f8-135">Test the application</span></span>

<span data-ttu-id="fa1f8-136">Uruchom projekt i zobacz dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-136">Run the project and see the output.</span></span> <span data-ttu-id="fa1f8-137">Wypróbuj te odmiany w wierszu polecenia, aby zobaczyć różne wyniki:</span><span class="sxs-lookup"><span data-stu-id="fa1f8-137">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="fa1f8-138">Wszystkie argumenty `--` po ogranicznik są przekazywane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-138">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="fa1f8-139">Zapakować narzędzie</span><span class="sxs-lookup"><span data-stu-id="fa1f8-139">Package the tool</span></span>

<span data-ttu-id="fa1f8-140">Przed spakowaniem i dystrybucją aplikacji jako narzędzia należy zmodyfikować plik projektu.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-140">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="fa1f8-141">Otwórz plik *microsoft.botsay.csproj* i dodaj trzy nowe węzły `<PropertyGroup>` XML na końcu węzła:</span><span class="sxs-lookup"><span data-stu-id="fa1f8-141">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="fa1f8-142">`<ToolCommandName>`jest opcjonalnym elementem, który określa polecenie, które wywoła narzędzie po jego zainstalowaniu.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-142">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="fa1f8-143">Jeśli ten element nie jest podany, nazwa polecenia narzędzia jest nazwą pliku projektu bez rozszerzenia *csproj.*</span><span class="sxs-lookup"><span data-stu-id="fa1f8-143">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="fa1f8-144">`<PackageOutputPath>`jest opcjonalnym elementem, który określa, gdzie pakiet NuGet zostaną wyprodukowane.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-144">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="fa1f8-145">Pakiet NuGet jest tym, czego używa cli .NET Core do zainstalowania narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-145">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="fa1f8-146">Plik projektu wygląda teraz jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fa1f8-146">The project file now looks like the following example:</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>
  
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="fa1f8-147">Utwórz pakiet NuGet, uruchamiając polecenie [dotnet pack:](dotnet-pack.md)</span><span class="sxs-lookup"><span data-stu-id="fa1f8-147">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="fa1f8-148">Plik *microsoft.botsay.1.0.0.nupkg* jest tworzony w folderze `<PackageOutputPath>` identyfikowanym przez wartość z pliku *microsoft.botsay.csproj,* który w tym przykładzie jest folderem *./nupkg.*</span><span class="sxs-lookup"><span data-stu-id="fa1f8-148">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="fa1f8-149">Jeśli chcesz udostępnić narzędzie publicznie, możesz przesłać `https://www.nuget.org`je do programu .</span><span class="sxs-lookup"><span data-stu-id="fa1f8-149">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="fa1f8-150">Gdy narzędzie jest dostępne na NuGet, deweloperzy mogą zainstalować narzędzie za pomocą polecenia [instalacji narzędzia dotnet.](dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="fa1f8-150">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="fa1f8-151">W tym samouczku można zainstalować pakiet bezpośrednio z lokalnego folderu *nupkg,* więc nie ma potrzeby przekazywania pakietu do NuGet.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-151">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="fa1f8-152">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="fa1f8-152">Troubleshoot</span></span>

<span data-ttu-id="fa1f8-153">Jeśli podczas korzystania z samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z używaniem narzędzia .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="fa1f8-153">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fa1f8-154">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fa1f8-154">Next steps</span></span>

<span data-ttu-id="fa1f8-155">W tym samouczku utworzono aplikację konsoli i spakowałeś ją jako narzędzie.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-155">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="fa1f8-156">Aby dowiedzieć się, jak korzystać z narzędzia jako narzędzia globalnego, przejdź do następnego samouczka.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-156">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fa1f8-157">Instalowanie i używanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="fa1f8-157">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="fa1f8-158">Jeśli wolisz, możesz pominąć samouczek narzędzi globalnych i przejść bezpośrednio do samouczka narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="fa1f8-158">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fa1f8-159">Instalowanie i używanie narzędzia lokalnego</span><span class="sxs-lookup"><span data-stu-id="fa1f8-159">Install and use a local tool</span></span>](local-tools-how-to-use.md)
