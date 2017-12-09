---
title: "Wdrażanie aplikacji .NET core za pomocą narzędzi interfejsu wiersza polecenia"
description: "Dowiedz się, wdrażanie aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia (CLI)"
keywords: "Wdrożenie .NET Core .NET i .NET core"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 82ebe16d-5e1c-46cc-91e8-71974296429c
ms.openlocfilehash: fc7a40667c9b0a623bb0ebdf4ad60783fa58e6c5
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="8b0af-104">Wdrażanie aplikacji .NET Core za pomocą narzędzia interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="8b0af-104">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="8b0af-105">Możesz wdrożyć aplikację .NET Core albo jako *wdrożenia zależne od framework*, który zawiera pliki binarne z aplikacji, ale zależy od obecności .NET Core w systemie docelowym lub jako *niezależne wdrożenie*, który zawiera pliki binarne .NET Core i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-105">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="8b0af-106">Aby uzyskać ogólne informacje, zobacz [wdrażanie aplikacji .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="8b0af-106">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="8b0af-107">W poniższych sekcjach przedstawiono sposób użycia [narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md) można utworzyć następujące typy wdrożeń:</span><span class="sxs-lookup"><span data-stu-id="8b0af-107">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="8b0af-108">Zależne od Framework wdrożenia</span><span class="sxs-lookup"><span data-stu-id="8b0af-108">Framework-dependent deployment</span></span>
- <span data-ttu-id="8b0af-109">Wdrożenie Framework zależne zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="8b0af-109">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="8b0af-110">Samodzielne wdrożenia</span><span class="sxs-lookup"><span data-stu-id="8b0af-110">Self-contained deployment</span></span>
- <span data-ttu-id="8b0af-111">Samodzielne wdrożenia zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="8b0af-111">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="8b0af-112">Podczas pracy z poziomu wiersza polecenia, można użyć dowolnego edytora programu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-112">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="8b0af-113">Jeśli w edytorze programu [Visual Studio Code](https://code.visualstudio.com), można otworzyć konsoli poleceń w środowisku Visual Studio Code, wybierając **widoku** > **zintegrowane terminali**.</span><span class="sxs-lookup"><span data-stu-id="8b0af-113">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="8b0af-114">Zależne od Framework wdrożenia</span><span class="sxs-lookup"><span data-stu-id="8b0af-114">Framework-dependent deployment</span></span>

<span data-ttu-id="8b0af-115">Po prostu wdrażanie wdrożenia zależne od framework bez zależności innych firm obejmuje tworzenie, testowanie i publikowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-115">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="8b0af-116">Prosty przykład napisane w języku C# przedstawiono proces.</span><span class="sxs-lookup"><span data-stu-id="8b0af-116">A simple example written in C# illustrates the process.</span></span> 

1. <span data-ttu-id="8b0af-117">Utwórz katalog projektu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-117">Create a project directory.</span></span>

   <span data-ttu-id="8b0af-118">Utwórz katalog projektu i stał się bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="8b0af-118">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="8b0af-119">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-119">Create the project.</span></span>

   <span data-ttu-id="8b0af-120">W wierszu polecenia wpisz [dotnet nowej konsoli](../tools/dotnet-new.md) Aby utworzyć nowy projekt console C# w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-120">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="8b0af-121">Należy dodać kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-121">Add the application's source code.</span></span>

   <span data-ttu-id="8b0af-122">Otwórz *Program.cs* plik w edytorze i Zastąp następujący kod automatycznie wygenerowany kod.</span><span class="sxs-lookup"><span data-stu-id="8b0af-122">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="8b0af-123">Monituje użytkownika o wprowadzenie tekstu, a Wyświetla poszczególnych wyrazów wprowadzony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8b0af-123">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="8b0af-124">Używa wyrażenia regularnego `\w+` do oddzielania słów w wejściowego tekstu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-124">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="8b0af-125">Zależności projektu i narzędzia do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-125">Update the project's dependencies and tools.</span></span>
 
   <span data-ttu-id="8b0af-126">Uruchom [przywracania dotnet](../tools/dotnet-restore.md) ([patrz Uwaga](#dotnet-restore-note)) polecenia, aby przywrócić zależności określony w projekcie.</span><span class="sxs-lookup"><span data-stu-id="8b0af-126">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="8b0af-127">Utwórz kompilację debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-127">Create a Debug build of your app.</span></span>

   <span data-ttu-id="8b0af-128">Użyj [kompilacji dotnet](../tools/dotnet-build.md) polecenie, aby skompilować aplikację lub [dotnet Uruchom](../tools/dotnet-run.md) polecenie, aby skompilować i uruchomić go.</span><span class="sxs-lookup"><span data-stu-id="8b0af-128">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="8b0af-129">Wdrażanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-129">Deploy your app.</span></span>

   <span data-ttu-id="8b0af-130">Po utworzeniu debugowania i przetestowane programu, tworzenia wdrożenia za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="8b0af-130">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   <span data-ttu-id="8b0af-131">Spowoduje to utworzenie zlecenia (zamiast debugowania) wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-131">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="8b0af-132">Pliki wynikowe są umieszczane w katalogu o nazwie *publikowania* w podkatalogu projektu *bin* katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-132">The resulting files are placed in a directory named *publish* that's in a subdirectory of your project's *bin* directory.</span></span>

<span data-ttu-id="8b0af-133">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (.pdb) program, który zawiera informacje o debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-133">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="8b0af-134">Plik przydaje się głównie w celu debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="8b0af-134">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="8b0af-135">Można pominąć rozpowszechnienie go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-135">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="8b0af-136">Jednak należy go zapisać, w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-136">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="8b0af-137">Pełny zestaw plików aplikacji w dowolny sposób, który chcesz można wdrożyć.</span><span class="sxs-lookup"><span data-stu-id="8b0af-137">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="8b0af-138">Na przykład można umieścić je w pliku Zip, użyć prostej `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8b0af-138">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="8b0af-139">Po zainstalowaniu użytkowników można uruchamiać aplikacji przy użyciu `dotnet` polecenia i podania nazwy pliku aplikacji, takich jak `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="8b0af-139">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="8b0af-140">Oprócz plików binarnych aplikacji instalatorem należy również pakietu Instalatora udostępnionego framework albo wyszukać jako warunek wstępny jako część instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-140">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="8b0af-141">Instalacja udostępnionego framework wymaga dostępu administratora/root.</span><span class="sxs-lookup"><span data-stu-id="8b0af-141">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="8b0af-142">Wdrożenie Framework zależne zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="8b0af-142">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="8b0af-143">Wdrażanie wdrożenie zależne od framework z co najmniej jeden zależności innych firm wymaga tych zależności dostępne do projektu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-143">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="8b0af-144">Wymagane są dwa dodatkowe czynności, przed uruchomieniem `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia:</span><span class="sxs-lookup"><span data-stu-id="8b0af-144">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="8b0af-145">Dodaj odwołania do wymaganych bibliotek innych firm do `<ItemGroup>` części Twojego *csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="8b0af-145">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="8b0af-146">Następujące `<ItemGroup>` sekcja zawiera zależność na [Json.NET](http://www.newtonsoft.com/json) jako biblioteki innych firm:</span><span class="sxs-lookup"><span data-stu-id="8b0af-146">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="8b0af-147">Jeśli nie jest jeszcze, Pobierz pakiet NuGet zawierający zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="8b0af-147">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="8b0af-148">Aby pobrać pakiet, należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia po dodaniu zależności.</span><span class="sxs-lookup"><span data-stu-id="8b0af-148">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="8b0af-149">Ponieważ zależność jest rozwiązany z lokalnej pamięci podręcznej NuGet w czasie publikacji, musi być dostępna w systemie.</span><span class="sxs-lookup"><span data-stu-id="8b0af-149">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="8b0af-150">Należy pamiętać, że wdrożenie framework zależne zależności innych firm tylko jako przenośne jako jego zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="8b0af-150">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="8b0af-151">Na przykład jeśli biblioteka innych firm obsługuje tylko macOS, aplikacja nie jest przenośne z systemami Windows.</span><span class="sxs-lookup"><span data-stu-id="8b0af-151">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="8b0af-152">Dzieje się tak, jeśli zależności innych firm, sama zależy od kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="8b0af-152">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="8b0af-153">Dobrym przykładem jest [serwera Kestrel](/aspnet/core/fundamentals/servers/kestrel), co wymaga natywnego zależności na [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="8b0af-153">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="8b0af-154">Podczas tworzenia Dyskietki dla aplikacji z tego rodzaju zależności innych firm publikowanych danych wyjściowych zawiera folder dla każdej [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) obsługującego natywnego zależności (i znajdujące się w pakiecie NuGet).</span><span class="sxs-lookup"><span data-stu-id="8b0af-154">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a><span data-ttu-id="8b0af-155">Samodzielne wdrożenia bez zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="8b0af-155">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="8b0af-156">Wdrażanie niezależne wdrożenia bez zależności innych firm obejmuje tworzenie projektu, modyfikując *csproj* plików, tworzenie, testowanie i publikowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-156">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="8b0af-157">Prosty przykład napisane w języku C# przedstawiono proces.</span><span class="sxs-lookup"><span data-stu-id="8b0af-157">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="8b0af-158">W przykładzie przedstawiono sposób tworzenia niezależne wdrożenia przy użyciu [narzędzie dotnet](../tools/dotnet.md) z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8b0af-158">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="8b0af-159">Utwórz katalog projektu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-159">Create a directory for the project.</span></span>

   <span data-ttu-id="8b0af-160">Utwórz katalog projektu i stał się bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="8b0af-160">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="8b0af-161">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-161">Create the project.</span></span>

   <span data-ttu-id="8b0af-162">W wierszu polecenia wpisz [dotnet nowej konsoli](../tools/dotnet-new.md) Aby utworzyć nowy projekt console C# w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-162">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="8b0af-163">Należy dodać kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-163">Add the application's source code.</span></span>

   <span data-ttu-id="8b0af-164">Otwórz *Program.cs* plik w edytorze i Zastąp następujący kod automatycznie wygenerowany kod.</span><span class="sxs-lookup"><span data-stu-id="8b0af-164">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="8b0af-165">Monituje użytkownika o wprowadzenie tekstu, a Wyświetla poszczególnych wyrazów wprowadzony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8b0af-165">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="8b0af-166">Używa wyrażenia regularnego `\w+` do oddzielania słów w wejściowego tekstu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-166">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="8b0af-167">Zdefiniuj platformy, dla których aplikacja będzie obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="8b0af-167">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="8b0af-168">Utwórz `<RuntimeIdentifiers>` tagów w `<PropertyGroup>` części Twojego *csproj* pliku, który definiuje platformy aplikacji elementów docelowych i podaj identyfikator środowiska uruchomieniowego (RID) dla każdej z platform docelowych.</span><span class="sxs-lookup"><span data-stu-id="8b0af-168">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="8b0af-169">Należy pamiętać, że należy również dodać średnika do rozdzielenia identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="8b0af-169">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="8b0af-170">Zobacz [katalogu identyfikator środowiska uruchomieniowego](../rid-catalog.md) dla identyfikatorów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="8b0af-170">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span> 

   <span data-ttu-id="8b0af-171">Na przykład następująca `<PropertyGroup>` sekcji wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X 10.11 wersji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-171">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="8b0af-172">Należy pamiętać, że `<RuntimeIdentifiers>` element może występować w dowolnym `<PropertyGroup>` w Twojej *csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="8b0af-172">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="8b0af-173">Kompletnego przykładu *csproj* plik pojawi się później w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-173">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="8b0af-174">Zależności projektu i narzędzia do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-174">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="8b0af-175">Uruchom [przywracania dotnet](../tools/dotnet-restore.md) ([patrz Uwaga](#dotnet-restore-note)) polecenia, aby przywrócić zależności określony w projekcie.</span><span class="sxs-lookup"><span data-stu-id="8b0af-175">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="8b0af-176">Utwórz kompilację debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-176">Create a Debug build of your app.</span></span>

   <span data-ttu-id="8b0af-177">W wierszu polecenia użyj [kompilacji dotnet](../tools/dotnet-build.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="8b0af-177">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="8b0af-178">Po debugowania i przetestować program, należy utworzyć plików do wdrożenia z aplikacją dla poszczególnych platform jej celem.</span><span class="sxs-lookup"><span data-stu-id="8b0af-178">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="8b0af-179">Użyj `dotnet publish` polecenia dla obu platform docelowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8b0af-179">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="8b0af-180">Spowoduje to utworzenie zlecenia (zamiast debugowania) wersji aplikacji dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="8b0af-180">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="8b0af-181">Pliki wynikowe są umieszczane w podkatalogu o nazwie *publikowania* w podkatalogu projektu *.\bin\Release\netcoreapp1.1\<runtime_identifier >* podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-181">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp1.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="8b0af-182">Należy pamiętać, że każdy podkatalog zawiera pełny zestaw plików (pliki aplikacji i wszystkich plików .NET Core) potrzebne do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-182">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="8b0af-183">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (.pdb) program, który zawiera informacje o debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-183">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="8b0af-184">Plik przydaje się głównie w celu debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="8b0af-184">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="8b0af-185">Możesz nie można skopiować pliki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-185">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="8b0af-186">Jednak należy go zapisać, w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-186">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="8b0af-187">Wdrażanie plików publikowanych w dowolny sposób, który chcesz.</span><span class="sxs-lookup"><span data-stu-id="8b0af-187">Deploy the published files in any way you like.</span></span> <span data-ttu-id="8b0af-188">Na przykład można umieścić je w pliku Zip, użyć prostej `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8b0af-188">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="8b0af-189">Poniżej przedstawiono pełną *csproj* pliku dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="8b0af-189">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="8b0af-190">Samodzielne wdrożenia zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="8b0af-190">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="8b0af-191">Wdrażanie niezależne wdrożenie z co najmniej jeden zależności innych firm obejmuje dodawanie zależności.</span><span class="sxs-lookup"><span data-stu-id="8b0af-191">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="8b0af-192">Wymagane są dwa dodatkowe czynności, przed uruchomieniem `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia:</span><span class="sxs-lookup"><span data-stu-id="8b0af-192">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="8b0af-193">Dodaj odwołania do bibliotek żadnych innych firm, które mają `<ItemGroup>` części Twojego *csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="8b0af-193">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="8b0af-194">Następujące `<ItemGroup>` sekcji używa struktury Json.NET jako biblioteki innych firm.</span><span class="sxs-lookup"><span data-stu-id="8b0af-194">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="8b0af-195">Jeśli nie jest jeszcze, Pobierz pakiet NuGet zawierający zależności innych firm w systemie.</span><span class="sxs-lookup"><span data-stu-id="8b0af-195">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="8b0af-196">Aby udostępnić zależności aplikacji, należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia po dodaniu zależności.</span><span class="sxs-lookup"><span data-stu-id="8b0af-196">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="8b0af-197">Ponieważ zależność jest rozwiązany z lokalnej pamięci podręcznej NuGet w czasie publikacji, musi być dostępna w systemie.</span><span class="sxs-lookup"><span data-stu-id="8b0af-197">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="8b0af-198">Poniżej przedstawiono pełną *csproj* pliku dla tego projektu:</span><span class="sxs-lookup"><span data-stu-id="8b0af-198">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="8b0af-199">Podczas wdrażania aplikacji, wszelkie zależności innych firm używane w aplikacji znajdują się również z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b0af-199">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="8b0af-200">Biblioteki innych firm nie są wymagane na komputerze, na którym jest uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="8b0af-200">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="8b0af-201">Należy pamiętać, że można wdrożyć tylko autonomiczną wdrożenia z biblioteką innych firm na platformach obsługiwanych przez tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="8b0af-201">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="8b0af-202">Przypomina o zależności innych firm z natywnego zależności w ramach wdrożenia zależne od framework gdzie zależności macierzysty musi być zgodny z platformy, na którym aplikacja jest wdrożona.</span><span class="sxs-lookup"><span data-stu-id="8b0af-202">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a><span data-ttu-id="8b0af-203">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b0af-203">See also</span></span>

<span data-ttu-id="8b0af-204">[Wdrażanie aplikacji .NET core](index.md) </span><span class="sxs-lookup"><span data-stu-id="8b0af-204">[.NET Core Application Deployment](index.md) </span></span>  
[<span data-ttu-id="8b0af-205">Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="8b0af-205">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)   

