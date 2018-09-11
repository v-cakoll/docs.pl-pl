---
title: Wdrażanie aplikacji .NET core za pomocą narzędzi interfejsu wiersza polecenia
description: Dowiedz się, wdrażanie aplikacji .NET Core za pomocą narzędzia interfejsu wiersza polecenia (CLI)
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: a7e810372d831699eae777186385e45fe65cdf45
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353910"
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="4dc0e-103">Wdrażanie aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="4dc0e-103">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="4dc0e-104">Możesz wdrożyć aplikację platformy .NET Core albo jako *wdrożenia zależny od struktury*, który zawiera pliki binarne aplikacji, ale zależy od obecności platformy .NET Core w systemie docelowym lub jako *niezależna wdrożenie*, który zawiera pliki binarne .NET Core i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="4dc0e-105">Aby uzyskać przegląd, zobacz [wdrożenie aplikacji programu .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="4dc0e-105">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="4dc0e-106">W poniższych sekcjach opisano sposób użycia [narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md) do tworzenia następujących rodzajów wdrożenia:</span><span class="sxs-lookup"><span data-stu-id="4dc0e-106">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="4dc0e-107">Wdrożenie zależny od struktury</span><span class="sxs-lookup"><span data-stu-id="4dc0e-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="4dc0e-108">Wdrażanie zależny od struktury za pomocą zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="4dc0e-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="4dc0e-109">Niezależne wdrożenia</span><span class="sxs-lookup"><span data-stu-id="4dc0e-109">Self-contained deployment</span></span>
- <span data-ttu-id="4dc0e-110">Niezależne wdrożenia przy użyciu zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="4dc0e-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="4dc0e-111">Podczas pracy z poziomu wiersza polecenia, można użyć dowolnego edytora w programie.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-111">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="4dc0e-112">Jeśli Edytor programu [programu Visual Studio Code](https://code.visualstudio.com), można otworzyć konsoli poleceń w środowisku Visual Studio Code, wybierając **widoku** > **zintegrowany Terminal**.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-112">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="4dc0e-113">Wdrożenie zależny od struktury</span><span class="sxs-lookup"><span data-stu-id="4dc0e-113">Framework-dependent deployment</span></span>

<span data-ttu-id="4dc0e-114">Wdrożenie zależny od struktury bez zależności innych firm po prostu polega na tworzenia, testowania i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="4dc0e-115">Prosty przykład napisany w języku C# przedstawiono proces.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-115">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="4dc0e-116">Utwórz katalog projektu.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-116">Create a project directory.</span></span>

   <span data-ttu-id="4dc0e-117">Utwórz katalog dla projektu, co bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-117">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="4dc0e-118">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-118">Create the project.</span></span>

   <span data-ttu-id="4dc0e-119">W wierszu polecenia wpisz polecenie [dotnet nową konsolę](../tools/dotnet-new.md) Aby utworzyć nowy projekt konsoli języka C# lub [dotnet nowej konsoli — lang vb](../tools/dotnet-new.md) Aby utworzyć nowy projekt konsoli języka Visual Basic, w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-119">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project or [dotnet new console -lang vb](../tools/dotnet-new.md) to create a new Visual Basic console project in that directory.</span></span>

1. <span data-ttu-id="4dc0e-120">Dodawanie kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-120">Add the application's source code.</span></span>

   <span data-ttu-id="4dc0e-121">Otwórz *Program.cs* lub *Program.vb* w edytorze i Zastęp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-121">Open the *Program.cs* or *Program.vb* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="4dc0e-122">On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="4dc0e-123">Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="4dc0e-124">Zależności projektu i narzędzia do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-124">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="4dc0e-125">Uruchom [dotnet restore](../tools/dotnet-restore.md) ([patrz Uwaga](#dotnet-restore-note)) polecenie, aby przywrócić zależności określony w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-125">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="4dc0e-126">Utworzenie kompilacja do debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-126">Create a Debug build of your app.</span></span>

   <span data-ttu-id="4dc0e-127">Użyj [kompilacji dotnet](../tools/dotnet-build.md) polecenie, aby skompilować aplikację lub [dotnet, uruchom](../tools/dotnet-run.md) polecenie, aby skompilować i uruchomić ją.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-127">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="4dc0e-128">Wdrażanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-128">Deploy your app.</span></span>

   <span data-ttu-id="4dc0e-129">Po utworzeniu debugowania i przetestować program, należy utworzyć wdrożenie za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="4dc0e-129">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp2.1 -c Release
      ```
   <span data-ttu-id="4dc0e-130">Spowoduje to utworzenie wydania (zamiast debugowania) wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-130">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="4dc0e-131">Pliki wynikowe są umieszczane w katalogu o nazwie *publikowania* znajdujący się w podkatalogu projektu *bin* katalogu.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-131">The resulting files are placed in a directory named *publish*      that's in a subdirectory of your project's *bin* directory.</span></span>

   <span data-ttu-id="4dc0e-132">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-132">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="4dc0e-133">Plik jest przydatne głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-133">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="4dc0e-134">Można nie rozprowadzić go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-134">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="4dc0e-135">Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-135">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

   <span data-ttu-id="4dc0e-136">Kompletny zestaw plików aplikacji w jakikolwiek sposób, który można wdrożyć.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-136">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="4dc0e-137">Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-137">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

1. <span data-ttu-id="4dc0e-138">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="4dc0e-138">Run your app</span></span>

   <span data-ttu-id="4dc0e-139">Po zainstalowaniu, użytkownicy mogą wykonać aplikacji przy użyciu `dotnet` polecenia i podając nazwę pliku aplikacji, takich jak `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-139">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

   <span data-ttu-id="4dc0e-140">Oprócz plików binarnych aplikacji Instalatora należy również pakietu Instalatora udostępnionego framework albo Wyszukaj jako warunek wstępny jako część instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-140">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="4dc0e-141">Instalacja udostępnionego framework wymaga dostępu administratora/root.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-141">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="4dc0e-142">Wdrażanie zależny od struktury za pomocą zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="4dc0e-142">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="4dc0e-143">Wdrożenie zależny od struktury z co najmniej jeden zależności innych firm wymaga tych zależności dostępne dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-143">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="4dc0e-144">Wymagane są dwa dodatkowe kroki, aby można było uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia:</span><span class="sxs-lookup"><span data-stu-id="4dc0e-144">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="4dc0e-145">Dodaj odwołania do wymaganych bibliotek innych firm, aby `<ItemGroup>` części Twojej *csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-145">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="4dc0e-146">Następujące `<ItemGroup>` sekcja zawiera zależność na [Json.NET](http://www.newtonsoft.com/json) jako biblioteki innej firmy:</span><span class="sxs-lookup"><span data-stu-id="4dc0e-146">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="4dc0e-147">Jeśli jeszcze nie, Pobierz pakiet NuGet zawierający zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-147">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="4dc0e-148">Aby pobrać pakiet, należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia po dodaniu zależności.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-148">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="4dc0e-149">Ponieważ zależność jest rozwiązany z lokalnej pamięci podręcznej narzędzia NuGet w czasu publikacji, musi on być dostępny w Twoim systemie.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-149">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="4dc0e-150">Należy pamiętać, że wdrożenie zależny od struktury z zależności innych firm tylko jako przenośne jako jego zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-150">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="4dc0e-151">Na przykład jeśli biblioteki innych firm obsługuje tylko z systemem macOS, aplikacja nie jest przenośny z systemami Windows.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-151">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="4dc0e-152">Dzieje się tak, jeśli zależności innych firm, sama jest zależna od kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-152">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="4dc0e-153">Dobrym przykładem jest [serwera Kestrel](/aspnet/core/fundamentals/servers/kestrel), co wymaga zależności natywnych na [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="4dc0e-153">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="4dc0e-154">Podczas tworzenia Dyskietki dla aplikacji za pomocą tego rodzaju zależności innych firm opublikowane dane wyjściowe zawiera folder dla każdego [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) obsługującego natywnych zależności (i znajdujące się w pakiecie NuGet).</span><span class="sxs-lookup"><span data-stu-id="4dc0e-154">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="4dc0e-155">Niezależne wdrożenia bez zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="4dc0e-155">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="4dc0e-156">Wdrożenie niezależna bez zależności innych firm obejmuje tworzenie projektu i modyfikując *csproj* pliku, tworzenia, testowania i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-156">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="4dc0e-157">Prosty przykład napisany w języku C# przedstawiono proces.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-157">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="4dc0e-158">W przykładzie pokazano, jak utworzyć niezależna wdrożenia przy użyciu [narzędzia dotnet](../tools/dotnet.md) z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-158">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="4dc0e-159">Utwórz katalog dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-159">Create a directory for the project.</span></span>

   <span data-ttu-id="4dc0e-160">Utwórz katalog dla projektu i ułatwiają bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-160">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="4dc0e-161">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-161">Create the project.</span></span>

   <span data-ttu-id="4dc0e-162">W wierszu polecenia wpisz polecenie [dotnet nową konsolę](../tools/dotnet-new.md) Aby utworzyć nowy projekt konsoli języka C#, w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-162">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="4dc0e-163">Dodawanie kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-163">Add the application's source code.</span></span>

   <span data-ttu-id="4dc0e-164">Otwórz *Program.cs* w edytorze i Zastęp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-164">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="4dc0e-165">On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-165">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="4dc0e-166">Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-166">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]
1. <span data-ttu-id="4dc0e-167">Zdefiniuj platformy, dla których będzie dotyczyć aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-167">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="4dc0e-168">Tworzenie `<RuntimeIdentifiers>` tagów w `<PropertyGroup>` części Twojej *csproj* pliku, który definiuje platform aplikacji jest przeznaczony dla i określ identyfikator środowiska uruchomieniowego (RID) dla każdej z platform docelowych.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-168">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="4dc0e-169">Należy zauważyć, że trzeba będzie również dodać średnika do rozdzielenia identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-169">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="4dc0e-170">Zobacz [katalog identyfikatora środowiska uruchomieniowego](../rid-catalog.md) Lista identyfikatorów środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-170">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="4dc0e-171">Na przykład następująca `<PropertyGroup>` sekcja wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X w wersji 10.11.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-171">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="4dc0e-172">Należy pamiętać, że `<RuntimeIdentifiers>` element może znajdować się w dowolnym `<PropertyGroup>` w swojej *csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-172">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="4dc0e-173">Pełny przykład *csproj* plik pojawia się w dalszej części w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-173">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="4dc0e-174">Zależności projektu i narzędzia do aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-174">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="4dc0e-175">Uruchom [dotnet restore](../tools/dotnet-restore.md) ([patrz Uwaga](#dotnet-restore-note)) polecenie, aby przywrócić zależności określony w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-175">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="4dc0e-176">Określ, czy używać globalizacji niezmiennej trybu.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-176">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="4dc0e-177">Szczególnie w przypadku, gdy aplikacja jest przeznaczona na systemie Linux, można zmniejszyć całkowity rozmiar wdrożenia, wykorzystując [globalizacji niezmiennej tryb](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="4dc0e-177">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="4dc0e-178">Globalizacji niezmiennej tryb jest przydatne w przypadku aplikacji, które nie są wspierane i mogą używać konwencji formatowania Konwencji obudowy i ciąg porównywania i sortowania kolejności [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="4dc0e-178">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="4dc0e-179">Aby włączyć tryb niezmiennej, kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań**i wybierz **Edytuj SCD.csproj** lub **Edytuj SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-179">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="4dc0e-180">Następnie dodaj następujące wiersze wyróżnione do pliku:</span><span class="sxs-lookup"><span data-stu-id="4dc0e-180">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="4dc0e-181">Utworzenie kompilacja do debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-181">Create a Debug build of your app.</span></span>

   <span data-ttu-id="4dc0e-182">W wierszu polecenia użyj [kompilacji dotnet](../tools/dotnet-build.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-182">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="4dc0e-183">Po utworzeniu debugowania i przetestować program, należy utworzyć pliki do wdrożenia z aplikacją, dotyczącymi poszczególnych platform, że jest ono przeznaczone dla.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-183">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="4dc0e-184">Użyj `dotnet publish` polecenia dla obu platform docelowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4dc0e-184">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="4dc0e-185">Spowoduje to utworzenie wydania (zamiast debugowania) wersję aplikacji dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-185">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="4dc0e-186">Pliki wynikowe są umieszczane w podkatalogu nazwanym *publikowania* znajdujący się w podkatalogu projektu *.\bin\Release\netcoreapp2.1\<runtime_identifier >* podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-186">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp2.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="4dc0e-187">Należy pamiętać, że każdy podkatalogu zawiera kompletny zestaw plików (pliki aplikacji i wszystkich plików z platformy .NET Core) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-187">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="4dc0e-188">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-188">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="4dc0e-189">Plik jest przydatne głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-189">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="4dc0e-190">Istnieje możliwość nie spakujesz ją z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-190">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="4dc0e-191">Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-191">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="4dc0e-192">Wdrażanie plików publikowanych w jakikolwiek sposób, który chcesz.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-192">Deploy the published files in any way you like.</span></span> <span data-ttu-id="4dc0e-193">Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-193">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="4dc0e-194">Poniżej przedstawiono pełne *csproj* pliku dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-194">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="4dc0e-195">Niezależne wdrożenia przy użyciu zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="4dc0e-195">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="4dc0e-196">Niezależna wdrożenie z co najmniej jeden zależności innych firm obejmuje dodawanie zależności.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-196">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="4dc0e-197">Wymagane są dwa dodatkowe kroki, aby można było uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia:</span><span class="sxs-lookup"><span data-stu-id="4dc0e-197">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="4dc0e-198">Dodaj odwołania do żadnych bibliotek innych firm, aby `<ItemGroup>` części Twojej *csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-198">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="4dc0e-199">Następujące `<ItemGroup>` sekcji używa struktury Json.NET jako biblioteki innej firmy.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-199">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="4dc0e-200">Jeśli jeszcze nie, Pobierz pakiet NuGet zawierający zależności innych firm w systemie.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-200">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="4dc0e-201">Aby jednak udostępnić zależności aplikacji, należy wykonać `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) polecenia po dodaniu zależności.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-201">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="4dc0e-202">Ponieważ zależność jest rozwiązany z lokalnej pamięci podręcznej narzędzia NuGet w czasu publikacji, musi on być dostępny w Twoim systemie.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-202">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="4dc0e-203">Poniżej przedstawiono pełne *csproj* pliku dla tego projektu:</span><span class="sxs-lookup"><span data-stu-id="4dc0e-203">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="4dc0e-204">Podczas wdrażania aplikacji, wszelkie zależności innych firm używanych w aplikacji znajdują się również z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-204">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="4dc0e-205">Bibliotek innych firm nie są wymagane w systemie, na którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-205">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="4dc0e-206">Należy pamiętać, że można wdrożyć tylko niezależna wdrożenia przy użyciu biblioteki innej firmy na platformach obsługiwanych przez tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-206">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="4dc0e-207">Jest to podobne do mających zależności innych firm za pomocą natywnego zależności w ramach wdrożenia zależny od struktury, gdzie zależności natywnych musi być zgodny z platform, w której wdrażana jest aplikacja.</span><span class="sxs-lookup"><span data-stu-id="4dc0e-207">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

## <a name="see-also"></a><span data-ttu-id="4dc0e-208">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dc0e-208">See also</span></span>

* [<span data-ttu-id="4dc0e-209">Wdrożenie aplikacji programu .NET core</span><span class="sxs-lookup"><span data-stu-id="4dc0e-209">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="4dc0e-210">Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="4dc0e-210">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
