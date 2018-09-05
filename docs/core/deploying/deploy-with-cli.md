---
title: Wdrażanie aplikacji .NET core za pomocą narzędzi interfejsu wiersza polecenia
description: Dowiedz się, wdrażanie aplikacji .NET Core za pomocą narzędzia interfejsu wiersza polecenia (CLI)
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.openlocfilehash: dbef9d91aa4e7af8e6e0ed2d8f361238385d4976
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559598"
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="70660-103">Wdrażanie aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="70660-103">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="70660-104">Możesz wdrożyć aplikację platformy .NET Core albo jako *wdrożenia zależny od struktury*, który zawiera pliki binarne aplikacji, ale zależy od obecności platformy .NET Core w systemie docelowym lub jako *niezależna wdrożenie*, który zawiera pliki binarne .NET Core i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="70660-105">Aby uzyskać przegląd, zobacz [wdrożenie aplikacji programu .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="70660-105">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="70660-106">W poniższych sekcjach opisano sposób użycia [narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md) do tworzenia następujących rodzajów wdrożenia:</span><span class="sxs-lookup"><span data-stu-id="70660-106">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="70660-107">Wdrożenie zależny od struktury</span><span class="sxs-lookup"><span data-stu-id="70660-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="70660-108">Wdrażanie zależny od struktury za pomocą zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="70660-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="70660-109">Niezależne wdrożenia</span><span class="sxs-lookup"><span data-stu-id="70660-109">Self-contained deployment</span></span>
- <span data-ttu-id="70660-110">Niezależne wdrożenia przy użyciu zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="70660-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="70660-111">Podczas pracy z poziomu wiersza polecenia, można użyć dowolnego edytora w programie.</span><span class="sxs-lookup"><span data-stu-id="70660-111">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="70660-112">Jeśli Edytor programu [programu Visual Studio Code](https://code.visualstudio.com), można otworzyć konsoli poleceń w środowisku Visual Studio Code, wybierając **widoku** > **zintegrowany Terminal**.</span><span class="sxs-lookup"><span data-stu-id="70660-112">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="70660-113">Wdrożenie zależny od struktury</span><span class="sxs-lookup"><span data-stu-id="70660-113">Framework-dependent deployment</span></span>

<span data-ttu-id="70660-114">Wdrożenie zależny od struktury bez zależności innych firm po prostu polega na tworzenia, testowania i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="70660-115">Prosty przykład napisany w języku C# przedstawiono proces.</span><span class="sxs-lookup"><span data-stu-id="70660-115">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="70660-116">Utwórz katalog projektu.</span><span class="sxs-lookup"><span data-stu-id="70660-116">Create a project directory.</span></span>

   <span data-ttu-id="70660-117">Utwórz katalog dla projektu, co bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="70660-117">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="70660-118">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="70660-118">Create the project.</span></span>

   <span data-ttu-id="70660-119">W wierszu polecenia wpisz polecenie [dotnet nową konsolę](../tools/dotnet-new.md) Aby utworzyć nowy projekt konsoli języka C#, w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="70660-119">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="70660-120">Dodawanie kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-120">Add the application's source code.</span></span>

   <span data-ttu-id="70660-121">Otwórz *Program.cs* w edytorze i Zastęp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="70660-121">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="70660-122">On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="70660-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="70660-123">Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="70660-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="70660-124">Zależności projektu i narzędzia do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="70660-124">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="70660-125">Uruchom [dotnet restore](../tools/dotnet-restore.md) ([patrz Uwaga](#dotnet-restore-note)) polecenie, aby przywrócić zależności określony w projekcie.</span><span class="sxs-lookup"><span data-stu-id="70660-125">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="70660-126">Utworzenie kompilacja do debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-126">Create a Debug build of your app.</span></span>

   <span data-ttu-id="70660-127">Użyj [kompilacji dotnet](../tools/dotnet-build.md) polecenie, aby skompilować aplikację lub [dotnet, uruchom](../tools/dotnet-run.md) polecenie, aby skompilować i uruchomić ją.</span><span class="sxs-lookup"><span data-stu-id="70660-127">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="70660-128">Wdrażanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-128">Deploy your app.</span></span>

   <span data-ttu-id="70660-129">Po utworzeniu debugowania i przetestować program, należy utworzyć wdrożenie za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="70660-129">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   <span data-ttu-id="70660-130">Spowoduje to utworzenie wydania (zamiast debugowania) wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-130">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="70660-131">Pliki wynikowe są umieszczane w katalogu o nazwie *publikowania* znajdujący się w podkatalogu projektu *bin* katalogu.</span><span class="sxs-lookup"><span data-stu-id="70660-131">The resulting files are placed in a directory named *publish*      that's in a subdirectory of your project's *bin* directory.</span></span>

   <span data-ttu-id="70660-132">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-132">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="70660-133">Plik jest przydatne głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="70660-133">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="70660-134">Można nie rozprowadzić go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-134">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="70660-135">Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-135">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

   <span data-ttu-id="70660-136">Kompletny zestaw plików aplikacji w jakikolwiek sposób, który można wdrożyć.</span><span class="sxs-lookup"><span data-stu-id="70660-136">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="70660-137">Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="70660-137">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

1. <span data-ttu-id="70660-138">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="70660-138">Run your app</span></span>

   <span data-ttu-id="70660-139">Po zainstalowaniu, użytkownicy mogą wykonać aplikacji przy użyciu `dotnet` polecenia i podając nazwę pliku aplikacji, takich jak `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="70660-139">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

   <span data-ttu-id="70660-140">Oprócz plików binarnych aplikacji Instalatora należy również pakietu Instalatora udostępnionego framework albo Wyszukaj jako warunek wstępny jako część instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-140">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="70660-141">Instalacja udostępnionego framework wymaga dostępu administratora/root.</span><span class="sxs-lookup"><span data-stu-id="70660-141">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="70660-142">Wdrażanie zależny od struktury za pomocą zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="70660-142">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="70660-143">Wdrożenie zależny od struktury z co najmniej jeden zależności innych firm wymaga tych zależności dostępne dla projektu.</span><span class="sxs-lookup"><span data-stu-id="70660-143">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="70660-144">Wymagane są dwa dodatkowe kroki, aby można było uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia:</span><span class="sxs-lookup"><span data-stu-id="70660-144">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="70660-145">Dodaj odwołania do wymaganych bibliotek innych firm, aby `<ItemGroup>` części Twojej *csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="70660-145">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="70660-146">Następujące `<ItemGroup>` sekcja zawiera zależność na [Json.NET](http://www.newtonsoft.com/json) jako biblioteki innej firmy:</span><span class="sxs-lookup"><span data-stu-id="70660-146">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="70660-147">Jeśli jeszcze nie, Pobierz pakiet NuGet zawierający zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="70660-147">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="70660-148">Aby pobrać pakiet, należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia po dodaniu zależności.</span><span class="sxs-lookup"><span data-stu-id="70660-148">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="70660-149">Ponieważ zależność jest rozwiązany z lokalnej pamięci podręcznej narzędzia NuGet w czasu publikacji, musi on być dostępny w Twoim systemie.</span><span class="sxs-lookup"><span data-stu-id="70660-149">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="70660-150">Należy pamiętać, że wdrożenie zależny od struktury z zależności innych firm tylko jako przenośne jako jego zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="70660-150">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="70660-151">Na przykład jeśli biblioteki innych firm obsługuje tylko z systemem macOS, aplikacja nie jest przenośny z systemami Windows.</span><span class="sxs-lookup"><span data-stu-id="70660-151">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="70660-152">Dzieje się tak, jeśli zależności innych firm, sama jest zależna od kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="70660-152">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="70660-153">Dobrym przykładem jest [serwera Kestrel](/aspnet/core/fundamentals/servers/kestrel), co wymaga zależności natywnych na [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="70660-153">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="70660-154">Podczas tworzenia Dyskietki dla aplikacji za pomocą tego rodzaju zależności innych firm opublikowane dane wyjściowe zawiera folder dla każdego [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) obsługującego natywnych zależności (i znajdujące się w pakiecie NuGet).</span><span class="sxs-lookup"><span data-stu-id="70660-154">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="70660-155">Niezależne wdrożenia bez zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="70660-155">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="70660-156">Wdrożenie niezależna bez zależności innych firm obejmuje tworzenie projektu i modyfikując *csproj* pliku, tworzenia, testowania i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-156">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="70660-157">Prosty przykład napisany w języku C# przedstawiono proces.</span><span class="sxs-lookup"><span data-stu-id="70660-157">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="70660-158">W przykładzie pokazano, jak utworzyć niezależna wdrożenia przy użyciu [narzędzia dotnet](../tools/dotnet.md) z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="70660-158">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="70660-159">Utwórz katalog dla projektu.</span><span class="sxs-lookup"><span data-stu-id="70660-159">Create a directory for the project.</span></span>

   <span data-ttu-id="70660-160">Utwórz katalog dla projektu i ułatwiają bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="70660-160">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="70660-161">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="70660-161">Create the project.</span></span>

   <span data-ttu-id="70660-162">W wierszu polecenia wpisz polecenie [dotnet nową konsolę](../tools/dotnet-new.md) Aby utworzyć nowy projekt konsoli języka C#, w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="70660-162">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="70660-163">Dodawanie kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-163">Add the application's source code.</span></span>

   <span data-ttu-id="70660-164">Otwórz *Program.cs* w edytorze i Zastęp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="70660-164">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="70660-165">On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="70660-165">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="70660-166">Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="70660-166">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="70660-167">Zdefiniuj platformy, dla których będzie dotyczyć aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-167">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="70660-168">Tworzenie `<RuntimeIdentifiers>` tagów w `<PropertyGroup>` części Twojej *csproj* pliku, który definiuje platform aplikacji jest przeznaczony dla i określ identyfikator środowiska uruchomieniowego (RID) dla każdej z platform docelowych.</span><span class="sxs-lookup"><span data-stu-id="70660-168">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="70660-169">Należy zauważyć, że trzeba będzie również dodać średnika do rozdzielenia identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="70660-169">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="70660-170">Zobacz [katalog identyfikatora środowiska uruchomieniowego](../rid-catalog.md) Lista identyfikatorów środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="70660-170">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="70660-171">Na przykład następująca `<PropertyGroup>` sekcja wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X w wersji 10.11.</span><span class="sxs-lookup"><span data-stu-id="70660-171">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="70660-172">Należy pamiętać, że `<RuntimeIdentifiers>` element może znajdować się w dowolnym `<PropertyGroup>` w swojej *csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="70660-172">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="70660-173">Pełny przykład *csproj* plik pojawia się w dalszej części w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="70660-173">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="70660-174">Zależności projektu i narzędzia do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="70660-174">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="70660-175">Uruchom [dotnet restore](../tools/dotnet-restore.md) ([patrz Uwaga](#dotnet-restore-note)) polecenie, aby przywrócić zależności określony w projekcie.</span><span class="sxs-lookup"><span data-stu-id="70660-175">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="70660-176">Utworzenie kompilacja do debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-176">Create a Debug build of your app.</span></span>

   <span data-ttu-id="70660-177">W wierszu polecenia użyj [kompilacji dotnet](../tools/dotnet-build.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="70660-177">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="70660-178">Po utworzeniu debugowania i przetestować program, należy utworzyć pliki do wdrożenia z aplikacją, dotyczącymi poszczególnych platform, że jest ono przeznaczone dla.</span><span class="sxs-lookup"><span data-stu-id="70660-178">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="70660-179">Użyj `dotnet publish` polecenia dla obu platform docelowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="70660-179">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="70660-180">Spowoduje to utworzenie wydania (zamiast debugowania) wersję aplikacji dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="70660-180">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="70660-181">Pliki wynikowe są umieszczane w podkatalogu nazwanym *publikowania* znajdujący się w podkatalogu projektu *.\bin\Release\netcoreapp1.1\<runtime_identifier >* podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="70660-181">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp1.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="70660-182">Należy pamiętać, że każdy podkatalogu zawiera kompletny zestaw plików (pliki aplikacji i wszystkich plików z platformy .NET Core) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-182">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="70660-183">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-183">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="70660-184">Plik jest przydatne głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="70660-184">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="70660-185">Istnieje możliwość nie spakujesz ją z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-185">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="70660-186">Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-186">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="70660-187">Wdrażanie plików publikowanych w jakikolwiek sposób, który chcesz.</span><span class="sxs-lookup"><span data-stu-id="70660-187">Deploy the published files in any way you like.</span></span> <span data-ttu-id="70660-188">Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="70660-188">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="70660-189">Poniżej przedstawiono pełne *csproj* pliku dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="70660-189">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="70660-190">Niezależne wdrożenia przy użyciu zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="70660-190">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="70660-191">Niezależna wdrożenie z co najmniej jeden zależności innych firm obejmuje dodawanie zależności.</span><span class="sxs-lookup"><span data-stu-id="70660-191">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="70660-192">Wymagane są dwa dodatkowe kroki, aby można było uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia:</span><span class="sxs-lookup"><span data-stu-id="70660-192">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="70660-193">Dodaj odwołania do żadnych bibliotek innych firm, aby `<ItemGroup>` części Twojej *csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="70660-193">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="70660-194">Następujące `<ItemGroup>` sekcji używa struktury Json.NET jako biblioteki innej firmy.</span><span class="sxs-lookup"><span data-stu-id="70660-194">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="70660-195">Jeśli jeszcze nie, Pobierz pakiet NuGet zawierający zależności innych firm w systemie.</span><span class="sxs-lookup"><span data-stu-id="70660-195">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="70660-196">Aby jednak udostępnić zależności aplikacji, należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia po dodaniu zależności.</span><span class="sxs-lookup"><span data-stu-id="70660-196">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="70660-197">Ponieważ zależność jest rozwiązany z lokalnej pamięci podręcznej narzędzia NuGet w czasu publikacji, musi on być dostępny w Twoim systemie.</span><span class="sxs-lookup"><span data-stu-id="70660-197">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="70660-198">Poniżej przedstawiono pełne *csproj* pliku dla tego projektu:</span><span class="sxs-lookup"><span data-stu-id="70660-198">The following is the complete *csproj* file for this project:</span></span>

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

<span data-ttu-id="70660-199">Podczas wdrażania aplikacji, wszelkie zależności innych firm używanych w aplikacji znajdują się również z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70660-199">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="70660-200">Bibliotek innych firm nie są wymagane w systemie, na którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="70660-200">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="70660-201">Należy pamiętać, że można wdrożyć tylko niezależna wdrożenia przy użyciu biblioteki innej firmy na platformach obsługiwanych przez tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="70660-201">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="70660-202">Jest to podobne do mających zależności innych firm za pomocą natywnego zależności w ramach wdrożenia zależny od struktury, gdzie zależności natywnych musi być zgodny z platform, w której wdrażana jest aplikacja.</span><span class="sxs-lookup"><span data-stu-id="70660-202">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

## <a name="see-also"></a><span data-ttu-id="70660-203">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70660-203">See also</span></span>

* [<span data-ttu-id="70660-204">Wdrożenie aplikacji programu .NET core</span><span class="sxs-lookup"><span data-stu-id="70660-204">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="70660-205">Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="70660-205">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
