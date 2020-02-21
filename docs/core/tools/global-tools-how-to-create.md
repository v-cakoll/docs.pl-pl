---
title: 'Samouczek: Tworzenie narzędzia platformy .NET Core'
description: Dowiedz się, jak utworzyć narzędzie .NET Core. Narzędzie jest aplikacją konsolową, która jest instalowana przy użyciu interfejs wiersza polecenia platformy .NET Core.
ms.date: 02/12/2020
ms.openlocfilehash: 558bf9e37efc8de68a61f1384fababe342ab7d66
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543407"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a><span data-ttu-id="735f3-104">Samouczek: Tworzenie narzędzia platformy .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="735f3-104">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>

<span data-ttu-id="735f3-105">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="735f3-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="735f3-106">W tym samouczku przedstawiono sposób tworzenia i pakowania narzędzia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="735f3-106">This tutorial teaches you how to create and package a .NET Core tool.</span></span> <span data-ttu-id="735f3-107">Interfejs wiersza polecenia platformy .NET Core pozwala utworzyć aplikację konsolową jako narzędzie, którą mogą instalować i uruchamiać inne osoby.</span><span class="sxs-lookup"><span data-stu-id="735f3-107">The .NET Core CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="735f3-108">Narzędzia .NET Core są pakietami NuGet, które są instalowane z interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="735f3-108">.NET Core tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="735f3-109">Aby uzyskać więcej informacji na temat narzędzi, zobacz [Narzędzia .NET Core Tools — Omówienie](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="735f3-109">For more information about tools, see [.NET Core tools overview](global-tools.md).</span></span>

<span data-ttu-id="735f3-110">Tworzone narzędzie jest aplikacją konsolową, która przyjmuje komunikat jako dane wejściowe i wyświetla komunikat wraz z wierszami tekstu, które tworzą obraz robota.</span><span class="sxs-lookup"><span data-stu-id="735f3-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="735f3-111">Jest to pierwsza z serii trzech samouczków.</span><span class="sxs-lookup"><span data-stu-id="735f3-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="735f3-112">Ten samouczek obejmuje tworzenie i pakowanie narzędzi.</span><span class="sxs-lookup"><span data-stu-id="735f3-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="735f3-113">W następnych dwóch samouczkach [użyjesz narzędzia jako narzędzia globalnego](global-tools-how-to-use.md) i [Użyj tego narzędzia jako narzędzia lokalnego](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="735f3-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="735f3-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="735f3-114">Prerequisites</span></span>

- <span data-ttu-id="735f3-115">[Zestaw .NET Core SDK 3,1](https://dotnet.microsoft.com/download) lub nowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="735f3-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="735f3-116">Ten samouczek i Poniższy samouczek dotyczący [narzędzi globalnych](global-tools-how-to-use.md) mają zastosowanie do zestaw .NET Core SDK 2,1 i nowszych wersji, ponieważ narzędzia globalne są dostępne w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="735f3-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="735f3-117">Jednak w tym samouczku założono, że zainstalowano program 3,1 lub nowszy, aby można było kontynuować korzystanie z [samouczka narzędzi lokalnych](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="735f3-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="735f3-118">Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="735f3-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="735f3-119">Procedury tworzenia narzędzia są takie same, niezależnie od tego, czy są używane jako narzędzie globalne, czy jako narzędzie lokalne.</span><span class="sxs-lookup"><span data-stu-id="735f3-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="735f3-120">Wybrany edytor tekstu lub edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="735f3-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="735f3-121">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="735f3-121">Create a project</span></span>

1. <span data-ttu-id="735f3-122">Otwórz wiersz polecenia i Utwórz folder o nazwie *Repository*.</span><span class="sxs-lookup"><span data-stu-id="735f3-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="735f3-123">Przejdź do folderu *repozytorium* i wprowadź następujące polecenie, zastępując `<name>` unikatową wartością, aby nazwa projektu była unikatowa.</span><span class="sxs-lookup"><span data-stu-id="735f3-123">Navigate to the *repository* folder and enter the following command, replacing `<name>` with a unique value to make the project name unique.</span></span> 

   ```dotnetcli
   dotnet new console -n botsay-<name>
   ```

   <span data-ttu-id="735f3-124">Można na przykład uruchomić następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="735f3-124">For example, you could run the following command:</span></span>

   ```dotnetcli
   dotnet new console -n botsay-nancydavolio
   ```

   <span data-ttu-id="735f3-125">Polecenie tworzy nowy folder o nazwie *botsay-\<name >* w folderze *repozytorium* .</span><span class="sxs-lookup"><span data-stu-id="735f3-125">The command creates a new folder named *botsay-\<name>* under the *repository* folder.</span></span>

1. <span data-ttu-id="735f3-126">Przejdź do folderu *botsay\<name >* .</span><span class="sxs-lookup"><span data-stu-id="735f3-126">Navigate to the *botsay-\<name>* folder.</span></span>

   ```console
   cd botsay-<name>
   ```

## <a name="add-the-code"></a><span data-ttu-id="735f3-127">Dodawanie kodu</span><span class="sxs-lookup"><span data-stu-id="735f3-127">Add the code</span></span>

1. <span data-ttu-id="735f3-128">Otwórz plik `Program.cs` z edytorem kodu.</span><span class="sxs-lookup"><span data-stu-id="735f3-128">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="735f3-129">Dodaj następującą `using` dyrektywę na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="735f3-129">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="735f3-130">Zastąp metodę `Main` poniższym kodem, aby przetworzyć argumenty wiersza polecenia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="735f3-130">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="735f3-131">Jeśli nie przechodzą żadnych argumentów, zostanie wyświetlony krótki komunikat pomocy.</span><span class="sxs-lookup"><span data-stu-id="735f3-131">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="735f3-132">W przeciwnym razie wszystkie argumenty są łączone w jeden ciąg i drukowane przez wywołanie metody `ShowBot` utworzonej w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="735f3-132">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="735f3-133">Dodaj nową metodę o nazwie `ShowBot`, która przyjmuje parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="735f3-133">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="735f3-134">Metoda drukuje komunikat i obraz robota przy użyciu wierszy tekstu.</span><span class="sxs-lookup"><span data-stu-id="735f3-134">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="735f3-135">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="735f3-135">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="735f3-136">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="735f3-136">Test the application</span></span>

<span data-ttu-id="735f3-137">Uruchom projekt i zobacz dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="735f3-137">Run the project and see the output.</span></span> <span data-ttu-id="735f3-138">Wypróbuj te Wariacje w wierszu polecenia, aby zobaczyć różne wyniki:</span><span class="sxs-lookup"><span data-stu-id="735f3-138">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="735f3-139">Wszystkie argumenty po przekroczeniu ogranicznika `--` są przesyłane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="735f3-139">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="735f3-140">Pakowanie narzędzia</span><span class="sxs-lookup"><span data-stu-id="735f3-140">Package the tool</span></span>

<span data-ttu-id="735f3-141">Przed spakowaniem i dystrybucją aplikacji jako narzędzia należy zmodyfikować plik projektu.</span><span class="sxs-lookup"><span data-stu-id="735f3-141">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span> 

1. <span data-ttu-id="735f3-142">Otwórz plik *botsay\<>. csproj* i Dodaj trzy nowe węzły XML na końcu węzła `<PropertyGroup>`:</span><span class="sxs-lookup"><span data-stu-id="735f3-142">Open the *botsay-\<name>.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="735f3-143">`<ToolCommandName>` to opcjonalny element określający polecenie, które spowoduje wywołanie narzędzia po jego zainstalowaniu.</span><span class="sxs-lookup"><span data-stu-id="735f3-143">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="735f3-144">Jeśli ten element nie zostanie podany, nazwa polecenia dla narzędzia jest nazwą pliku projektu bez rozszerzenia *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="735f3-144">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="735f3-145">`<PackageOutputPath>` to opcjonalny element określający, gdzie zostanie utworzony pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="735f3-145">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="735f3-146">Pakiet NuGet jest używany przez interfejs wiersza polecenia platformy .NET Core do instalowania narzędzia.</span><span class="sxs-lookup"><span data-stu-id="735f3-146">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="735f3-147">Plik projektu wygląda teraz tak, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="735f3-147">The project file now looks like the following example:</span></span>

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

1. <span data-ttu-id="735f3-148">Utwórz pakiet NuGet, uruchamiając polecenie [dotnet Pack](dotnet-pack.md) :</span><span class="sxs-lookup"><span data-stu-id="735f3-148">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="735f3-149">*Nazwa botsay\<>. 1.0.0. nupkg* zostanie utworzona w folderze identyfikowanym przez `<PackageOutputPath>` wartość z pliku *botsay-\<nazwa >. csproj* , który w tym przykładzie jest folderem *./nupkg* .</span><span class="sxs-lookup"><span data-stu-id="735f3-149">The *botsay-\<name>.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *botsay-\<name>.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="735f3-150">Aby publicznie wydać narzędzie, można przekazać je do `https://www.nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="735f3-150">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="735f3-151">Po udostępnieniu narzędzia w narzędziu NuGet deweloperzy mogą zainstalować narzędzie za pomocą polecenia [Install narzędzia dotnet](dotnet-tool-install.md) .</span><span class="sxs-lookup"><span data-stu-id="735f3-151">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="735f3-152">Na potrzeby tego samouczka zainstalujesz pakiet bezpośrednio z lokalnego folderu *NUPKG* , więc nie ma potrzeby przekazywania pakietu do narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="735f3-152">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="735f3-153">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="735f3-153">Troubleshoot</span></span>

<span data-ttu-id="735f3-154">Jeśli podczas wykonywania samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z użyciem narzędzia .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="735f3-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="735f3-155">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="735f3-155">Next steps</span></span>

<span data-ttu-id="735f3-156">W tym samouczku utworzysz aplikację konsolową i spakowano ją jako narzędzie.</span><span class="sxs-lookup"><span data-stu-id="735f3-156">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="735f3-157">Aby dowiedzieć się, jak używać narzędzia jako narzędzia globalnego, przejdź do następnego samouczka.</span><span class="sxs-lookup"><span data-stu-id="735f3-157">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="735f3-158">Instalowanie i używanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="735f3-158">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="735f3-159">Jeśli wolisz, możesz pominąć samouczek dotyczący narzędzi globalnych i przejść bezpośrednio do samouczka dotyczącego narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="735f3-159">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="735f3-160">Instalowanie i używanie narzędzia lokalnego</span><span class="sxs-lookup"><span data-stu-id="735f3-160">Install and use a local tool</span></span>](local-tools-how-to-use.md)
