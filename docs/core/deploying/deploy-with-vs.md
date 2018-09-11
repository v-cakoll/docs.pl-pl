---
title: Wdrażanie aplikacji .NET core za pomocą programu Visual Studio
description: Dowiedz się, wdrażanie aplikacji .NET Core za pomocą programu Visual Studio
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: 62cfef08a8319981891c713c08c34eba5ab54b6f
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275668"
---
# <a name="deploying-net-core-apps-with-visual-studio"></a><span data-ttu-id="da38e-103">Wdrażanie platformy .NET Core z aplikacji za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da38e-103">Deploying .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="da38e-104">Możesz wdrożyć aplikację platformy .NET Core albo jako *wdrożenia zależny od struktury*, który zawiera pliki binarne aplikacji, ale zależy od obecności platformy .NET Core w systemie docelowym lub jako *niezależna wdrożenie*, który zawiera aplikację i pliki binarne .NET Core.</span><span class="sxs-lookup"><span data-stu-id="da38e-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="da38e-105">Omówienie wdrażania aplikacji .NET Core, zobacz [wdrożenie aplikacji programu .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="da38e-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="da38e-106">Poniższe sekcje pokazują, jak używać programu Microsoft Visual Studio do tworzenia następujących rodzajów wdrożenia:</span><span class="sxs-lookup"><span data-stu-id="da38e-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="da38e-107">Wdrożenie zależny od struktury</span><span class="sxs-lookup"><span data-stu-id="da38e-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="da38e-108">Wdrażanie zależny od struktury za pomocą zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="da38e-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="da38e-109">Niezależne wdrożenia</span><span class="sxs-lookup"><span data-stu-id="da38e-109">Self-contained deployment</span></span>
- <span data-ttu-id="da38e-110">Niezależne wdrożenia przy użyciu zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="da38e-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="da38e-111">Aby uzyskać informacje na temat korzystania z programu Visual Studio do opracowywania aplikacji platformy .NET Core, zobacz [wymagania wstępne dla platformy .NET Core w Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span><span class="sxs-lookup"><span data-stu-id="da38e-111">For information on using Visual Studio to develop .NET Core applications, see [Prerequisites for .NET Core on Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="da38e-112">Wdrożenie zależny od struktury</span><span class="sxs-lookup"><span data-stu-id="da38e-112">Framework-dependent deployment</span></span>

<span data-ttu-id="da38e-113">Wdrożenie zależny od struktury bez zależności innych firm po prostu polega na tworzenia, testowania i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="da38e-114">Prosty przykład napisany w języku C# przedstawiono proces.</span><span class="sxs-lookup"><span data-stu-id="da38e-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="da38e-115">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="da38e-115">Create the project.</span></span>

   <span data-ttu-id="da38e-116">Wybierz **pliku** > **nowe** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="da38e-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="da38e-117">W **nowy projekt** okno dialogowe, rozwiń węzeł kategorii danego języka (C# lub Visual Basic) projektu w **zainstalowane** okienku typów projektu, wybierz polecenie **platformy .NET Core**, a następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonów w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="da38e-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="da38e-118">Wprowadź nazwę projektu, takich jak "Dyskietki" w **nazwa** pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="da38e-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="da38e-119">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="da38e-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="da38e-120">Dodawanie kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-120">Add the application's source code.</span></span>

   <span data-ttu-id="da38e-121">Otwórz *Program.cs* lub *Program.vb* w edytorze i Zastęp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="da38e-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="da38e-122">On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="da38e-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="da38e-123">Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="da38e-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="da38e-124">Utworzenie kompilacja do debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="da38e-125">Wybierz **kompilacji** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="da38e-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="da38e-126">Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowania** > **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="da38e-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="da38e-127">Wdrażanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-127">Deploy your app.</span></span>

   <span data-ttu-id="da38e-128">Po utworzeniu debugowania i przetestować program, należy utworzyć plików do wdrożenia z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="da38e-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="da38e-129">Aby opublikować z programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="da38e-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="da38e-130">Zmień konfigurację przy użyciu rozwiązania **debugowania** do **wersji** na pasku narzędzi do kompilacji w wersji (a nie na debugowanie) wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="da38e-131">Kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="da38e-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="da38e-132">W **Publikuj** zaznacz **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="da38e-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="da38e-133">Program Visual Studio zapisuje pliki, wchodzące w skład aplikacji w lokalnym systemie plików.</span><span class="sxs-lookup"><span data-stu-id="da38e-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="da38e-134">**Publikuj** karta zawiera teraz jeden profil **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="da38e-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="da38e-135">Ustawienia konfiguracji w profilu są wyświetlane w **Podsumowanie** karcie.</span><span class="sxs-lookup"><span data-stu-id="da38e-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="da38e-136">Pliki wynikowe są umieszczane w katalogu o nazwie `Publish` na Windows i `publish` na komputerach z systemem Unix, które znajduje się w podkatalogu projektu *.\bin\release\netcoreapp2.1* podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="da38e-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="da38e-137">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="da38e-138">Plik jest przydatne głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="da38e-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="da38e-139">Istnieje możliwość nie spakujesz ją z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="da38e-140">Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="da38e-141">Wdróż kompletny zestaw plików aplikacji w jakikolwiek sposób, który chcesz.</span><span class="sxs-lookup"><span data-stu-id="da38e-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="da38e-142">Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="da38e-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="da38e-143">Po zainstalowaniu, użytkownicy mogą następnie wykonać aplikacji przy użyciu `dotnet` polecenia i podając nazwę pliku aplikacji, takich jak `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="da38e-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="da38e-144">Oprócz plików binarnych aplikacji Instalatora należy również pakietu Instalatora udostępnionego framework albo Wyszukaj jako warunek wstępny jako część instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="da38e-145">Instalacja udostępnionego framework wymaga dostępu administratora/root, ponieważ jest ono komputera.</span><span class="sxs-lookup"><span data-stu-id="da38e-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="da38e-146">Wdrażanie zależny od struktury za pomocą zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="da38e-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="da38e-147">Wdrożenie zależny od struktury z co najmniej jeden zależności innych firm wymaga, aby wszystkie zależności dostępne dla projektu.</span><span class="sxs-lookup"><span data-stu-id="da38e-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="da38e-148">Przed utworzeniem aplikacji wymagane są następujące dodatkowe czynności:</span><span class="sxs-lookup"><span data-stu-id="da38e-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="da38e-149">Użyj **Menedżera pakietów NuGet** Dodaj odwołanie do pakietu NuGet do projektu; i jeśli pakiet nie jest jeszcze dostępna w systemie, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="da38e-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="da38e-150">Aby otworzyć Menedżera pakietów, wybierz **narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="da38e-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="da38e-151">Upewnij się, że `Newtonsoft.Json` jest zainstalowana w systemie, a jeśli tak nie jest, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="da38e-151">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="da38e-152">**Zainstalowane** karcie znajduje się lista pakietów NuGet, zainstalowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="da38e-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="da38e-153">Jeśli `Newtonsoft.Json` nie ma na liście, wybierz **Przeglądaj** kartę, a następnie wprowadź "Newtonsoft.Json" w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="da38e-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="da38e-154">Wybierz `Newtonsoft.Json` i w okienku po prawej stronie, wybierz swój projekt przed wybraniem **zainstalować**.</span><span class="sxs-lookup"><span data-stu-id="da38e-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="da38e-155">Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku **Zarządzaj pakietami dla rozwiązania** kartę.</span><span class="sxs-lookup"><span data-stu-id="da38e-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of hte **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="da38e-156">Należy pamiętać, że wdrożenie zależny od struktury z zależności innych firm tylko jako przenośne jako jego zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="da38e-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="da38e-157">Na przykład jeśli biblioteki innych firm obsługuje tylko z systemem macOS, aplikacja nie jest przenośny z systemami Windows.</span><span class="sxs-lookup"><span data-stu-id="da38e-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="da38e-158">Dzieje się tak, jeśli zależności innych firm, sama jest zależna od kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="da38e-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="da38e-159">Dobrym przykładem jest [serwera Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), co wymaga zależności natywnych na [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="da38e-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="da38e-160">Podczas tworzenia Dyskietki dla aplikacji za pomocą tego rodzaju zależności innych firm opublikowane dane wyjściowe zawiera folder dla każdego [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) obsługującego natywnych zależności (i znajdujące się w pakiecie NuGet).</span><span class="sxs-lookup"><span data-stu-id="da38e-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="da38e-161">Niezależne wdrożenia bez zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="da38e-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="da38e-162">Wdrożenie niezależna bez zależności innych firm obejmuje tworzenie projektu i modyfikując *csproj* pliku, tworzenia, testowania i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="da38e-163">Prosty przykład napisany w języku C# przedstawiono proces.</span><span class="sxs-lookup"><span data-stu-id="da38e-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="da38e-164">Należy rozpocząć od tworzenia, kodowania i testowania projektu, tak samo jak wdrożenia zależny od struktury:</span><span class="sxs-lookup"><span data-stu-id="da38e-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="da38e-165">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="da38e-165">Create the project.</span></span>

   <span data-ttu-id="da38e-166">Wybierz **pliku** > **nowe** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="da38e-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="da38e-167">W **nowy projekt** okno dialogowe, rozwiń węzeł kategorii danego języka (C# lub Visual Basic) projektu w **zainstalowane** okienku typów projektu, wybierz polecenie **platformy .NET Core**, a następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonów w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="da38e-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="da38e-168">Wprowadź nazwę projektu, takich jak "— SCD", w **nazwa** pola tekstowego, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="da38e-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="da38e-169">Dodawanie kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-169">Add the application's source code.</span></span>

   <span data-ttu-id="da38e-170">Otwórz *Program.cs* lub plik w edytorze i Zastąp kod wygenerowany automatycznie z następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="da38e-170">Open the *Program.cs* or file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="da38e-171">On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="da38e-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="da38e-172">Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="da38e-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="da38e-173">Określ, czy używać globalizacji niezmiennej trybu.</span><span class="sxs-lookup"><span data-stu-id="da38e-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="da38e-174">Szczególnie w przypadku, gdy aplikacja jest przeznaczona na systemie Linux, można zmniejszyć całkowity rozmiar wdrożenia, wykorzystując [globalizacji niezmiennej tryb](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="da38e-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="da38e-175">Globalizacji niezmiennej tryb jest przydatne w przypadku aplikacji, które nie są wspierane i mogą używać konwencji formatowania Konwencji obudowy i ciąg porównywania i sortowania kolejności [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="da38e-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="da38e-176">Aby włączyć tryb niezmiennej, kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań**i wybierz **Edytuj SCD.csproj** lub **Edytuj SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="da38e-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="da38e-177">Następnie dodaj następujące wiersze wyróżnione do pliku:</span><span class="sxs-lookup"><span data-stu-id="da38e-177">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="da38e-178">Utworzenie kompilacja do debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="da38e-179">Wybierz **kompilacji** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="da38e-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="da38e-180">Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowania** > **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="da38e-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="da38e-181">Ten krok debugowania pozwala zidentyfikować problemy z aplikacji, gdy jest uruchomiona na platformie hosta.</span><span class="sxs-lookup"><span data-stu-id="da38e-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="da38e-182">Nadal trzeba będzie je przetestować na każdej z platform docelowych.</span><span class="sxs-lookup"><span data-stu-id="da38e-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="da38e-183">Po włączeniu trybu niezmiennej globalizacji, należy szczególnie sprawdzić, czy brak dane wrażliwe na ustawienia kulturowe jest odpowiedni dla twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="da38e-184">Po zakończeniu debugowania, możesz opublikować niezależna wdrożenia:</span><span class="sxs-lookup"><span data-stu-id="da38e-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="da38e-185">Visual Studio 15.6 i wcześniejszych</span><span class="sxs-lookup"><span data-stu-id="da38e-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="da38e-186">Po utworzeniu debugowania i przetestować program, należy utworzyć pliki do wdrożenia z aplikacją, dotyczącymi poszczególnych platform, że jest ono przeznaczone dla.</span><span class="sxs-lookup"><span data-stu-id="da38e-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="da38e-187">Aby opublikować aplikację z poziomu programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="da38e-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="da38e-188">Zdefiniuj platformy, dla których będzie dotyczyć aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="da38e-189">Kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Edytuj SCD.csproj**.</span><span class="sxs-lookup"><span data-stu-id="da38e-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="da38e-190">Tworzenie `<RuntimeIdentifiers>` tagów w `<PropertyGroup>` części Twojej *csproj* pliku, który definiuje Twojej aplikacji jest przeznaczony dla platform i podaj identyfikator środowiska uruchomieniowego (RID) każdej z platform docelowych.</span><span class="sxs-lookup"><span data-stu-id="da38e-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="da38e-191">Należy zauważyć, że trzeba będzie również dodać średnika do rozdzielenia identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="da38e-191">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="da38e-192">Zobacz [katalog identyfikatora środowiska uruchomieniowego](../rid-catalog.md) Lista identyfikatorów środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="da38e-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="da38e-193">Na przykład w poniższym przykładzie wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X w wersji 10.11.</span><span class="sxs-lookup"><span data-stu-id="da38e-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="da38e-194">Należy pamiętać, że `<RuntimeIdentifiers>` przejść do dowolnego elementu `<PropertyGroup>` zainstalowanej w swojej *csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="da38e-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="da38e-195">Pełny przykład *csproj* plik pojawia się w dalszej części w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="da38e-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="da38e-196">Opublikuj aplikację.</span><span class="sxs-lookup"><span data-stu-id="da38e-196">Publish your app.</span></span>

   <span data-ttu-id="da38e-197">Po utworzeniu debugowania i przetestować program, należy utworzyć pliki do wdrożenia z aplikacją, dotyczącymi poszczególnych platform, że jest ono przeznaczone dla.</span><span class="sxs-lookup"><span data-stu-id="da38e-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="da38e-198">Aby opublikować aplikację z poziomu programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="da38e-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="da38e-199">Zmień konfigurację przy użyciu rozwiązania **debugowania** do **wersji** na pasku narzędzi do kompilacji w wersji (a nie na debugowanie) wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="da38e-200">Kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="da38e-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="da38e-201">W **Publikuj** zaznacz **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="da38e-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="da38e-202">Program Visual Studio zapisuje pliki, wchodzące w skład aplikacji w lokalnym systemie plików.</span><span class="sxs-lookup"><span data-stu-id="da38e-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="da38e-203">**Publikuj** karta zawiera teraz jeden profil **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="da38e-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="da38e-204">Ustawienia konfiguracji w profilu są wyświetlane w **Podsumowanie** karcie. **Docelowe środowisko uruchomieniowe** identyfikuje, które środowisko uruchomieniowe zostało opublikowane, a **lokalizacji docelowej** identyfikuje, gdzie zostały napisane pliki niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="da38e-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="da38e-205">Visual Studio domyślnie zapisuje pliki wszystkie opublikowane w jednym katalogu.</span><span class="sxs-lookup"><span data-stu-id="da38e-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="da38e-206">Dla wygody najlepiej jest utworzyć osobne profile dla każdego docelowe środowisko uruchomieniowe i umieść pliki opublikowane w katalogu specyficzny dla platformy.</span><span class="sxs-lookup"><span data-stu-id="da38e-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="da38e-207">Obejmuje to tworzenie oddzielny profil publikowania dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="da38e-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="da38e-208">Teraz ponownie skompiluj aplikację dla każdej platformy, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="da38e-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="da38e-209">Wybierz **Utwórz nowy profil** w **Publikuj** okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="da38e-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="da38e-210">W **wybierz lokalizację docelową publikowania** okno dialogowe, zmiana **wybierz folder** lokalizację *bin\Release\PublishOutput\win10 x64*.</span><span class="sxs-lookup"><span data-stu-id="da38e-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="da38e-211">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="da38e-211">Select **OK**.</span></span>

         1. <span data-ttu-id="da38e-212">Wybierz nowy profil (**FolderProfile1**) na liście profilów i upewnij się, że **docelowe środowisko uruchomieniowe** jest `win10-x64`.</span><span class="sxs-lookup"><span data-stu-id="da38e-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="da38e-213">Jeśli nie, wybierz **ustawienia**.</span><span class="sxs-lookup"><span data-stu-id="da38e-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="da38e-214">W **ustawienia profilu** okno dialogowe, zmiana **docelowe środowisko uruchomieniowe** do `win10-x64` i wybierz **Zapisz**.</span><span class="sxs-lookup"><span data-stu-id="da38e-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="da38e-215">W przeciwnym razie wybierz **anulować**.</span><span class="sxs-lookup"><span data-stu-id="da38e-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="da38e-216">Wybierz **Publikuj** do publikowania aplikacji dla platformy Windows 10 w 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="da38e-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="da38e-217">Wykonaj poprzednie kroki, aby utworzyć profil dla `osx.10.11-x64` platformy.</span><span class="sxs-lookup"><span data-stu-id="da38e-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="da38e-218">**Lokalizacji docelowej** jest *bin\Release\PublishOutput\osx.10.11-x64*i **docelowe środowisko uruchomieniowe** jest `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="da38e-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="da38e-219">Nazwa programu Visual Studio, przypisuje do tego profilu jest **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="da38e-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="da38e-220">Należy pamiętać, że każda lokalizacja docelowa zawiera kompletny zestaw plików (pliki aplikacji i wszystkich plików z platformy .NET Core) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="da38e-221">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="da38e-222">Plik jest przydatne głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="da38e-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="da38e-223">Istnieje możliwość nie spakujesz ją z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="da38e-224">Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="da38e-225">Wdrażanie plików publikowanych w jakikolwiek sposób, który chcesz.</span><span class="sxs-lookup"><span data-stu-id="da38e-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="da38e-226">Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="da38e-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="da38e-227">Poniżej przedstawiono pełne *csproj* pliku dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="da38e-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="da38e-228">Visual Studio 15.7 i nowsze</span><span class="sxs-lookup"><span data-stu-id="da38e-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="da38e-229">Po utworzeniu debugowania i przetestować program, należy utworzyć pliki do wdrożenia z aplikacją, dotyczącymi poszczególnych platform, że jest ono przeznaczone dla.</span><span class="sxs-lookup"><span data-stu-id="da38e-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="da38e-230">Obejmuje to tworzenie osobny profil dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="da38e-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="da38e-231">Dla każdej platformy, że Twoje cele aplikacji, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="da38e-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="da38e-232">Utwórz profil dla danej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="da38e-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="da38e-233">Jeśli jest to pierwszy profil został utworzony, kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="da38e-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="da38e-234">Jeśli już utworzono profil, kliknij prawym przyciskiem myszy projekt, aby otworzyć **Publikuj** okno dialogowe, jeśli nie jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="da38e-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="da38e-235">Następnie wybierz pozycję **nowy profil**.</span><span class="sxs-lookup"><span data-stu-id="da38e-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="da38e-236">**Wybierz miejsce docelowe publikowania** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="da38e-236">The **Pick a Publish Target** dialog box opens.</span></span>
  
1. <span data-ttu-id="da38e-237">Wybierz lokalizację, w którym program Visual Studio publikuje aplikację.</span><span class="sxs-lookup"><span data-stu-id="da38e-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="da38e-238">Jeśli publikujesz tylko na jednej platformie, możesz zaakceptować wartości domyślne w **wybierz folder** pole tekstowe; publikuje wdrożenia zależne struktury aplikacji, aby \*\<katalogu projektu > \ bin\Release\netcoreapp2.1\publish\* katalogu.</span><span class="sxs-lookup"><span data-stu-id="da38e-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the \*\<project-directory>\bin\Release\netcoreapp2.1\publish\* directory.</span></span>

   <span data-ttu-id="da38e-239">Jeśli publikujesz do więcej niż jedną platformę, Dołącz ciąg, który identyfikuje platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="da38e-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="da38e-240">Na przykład jeśli ciąg "linux" dołączania do ścieżki pliku, programu Visual Studio publikuje wdrożenia zależne struktury aplikacji, aby  *\<katalogu projektu > \bin\Release\netcoreapp2.1\publish\linux*katalogu.</span><span class="sxs-lookup"><span data-stu-id="da38e-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="da38e-241">Tworzenie profilu, wybierając ikonę listy rozwijanej obok **Publikuj** przycisk i wybierając polecenie **Utwórz profil**.</span><span class="sxs-lookup"><span data-stu-id="da38e-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="da38e-242">Następnie wybierz pozycję **Utwórz profil** przycisk, aby utworzyć profil.</span><span class="sxs-lookup"><span data-stu-id="da38e-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="da38e-243">Wskazują, publikują niezależna wdrożenia, a następnie zdefiniuj platformy, przeznaczony dla twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="da38e-244">W **Publikuj** okno dialogowe, wybierz opcję **Konfiguruj** link umożliwiający otworzenie **ustawienia profilu** okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="da38e-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="da38e-245">Wybierz **niezależna** w **tryb wdrożenia** pola listy.</span><span class="sxs-lookup"><span data-stu-id="da38e-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="da38e-246">W **docelowe środowisko uruchomieniowe** pola listy, wybierz jedną z platform, Twoje cele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="da38e-247">Wybierz **Zapisz** zaakceptować zmiany i zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="da38e-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="da38e-248">Nazwa profilu.</span><span class="sxs-lookup"><span data-stu-id="da38e-248">Name your profile.</span></span>

   1. <span data-ttu-id="da38e-249">Wybierz **akcje** > **Zmienianie nazwy profilu** nazwy profilu.</span><span class="sxs-lookup"><span data-stu-id="da38e-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="da38e-250">Przypisywanie profilu nazwa, która określa platformę docelową, a następnie wybierz pozycję \**Zapisz*.</span><span class="sxs-lookup"><span data-stu-id="da38e-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="da38e-251">Powtórz te kroki, aby zdefiniować żadnych dodatkowych platform, Twoje cele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="da38e-252">Skonfigurowano profilów i są teraz gotowe do publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="da38e-253">W tym celu:</span><span class="sxs-lookup"><span data-stu-id="da38e-253">To do this:</span></span>

   1. <span data-ttu-id="da38e-254">Jeśli **Publikuj** okno nie jest obecnie otwarty, kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="da38e-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="da38e-255">Wybierz profil, który chcesz opublikować, a następnie wybierz **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="da38e-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="da38e-256">W tym dla każdego profilu do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="da38e-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="da38e-257">Należy pamiętać, że każda lokalizacja docelowa (w przypadku naszym przykładzie bin\release\netcoreapp2.1\publish\\*nazwa profilu* zawiera kompletny zestaw plików (pliki aplikacji i wszystkich plików z platformy .NET Core) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="da38e-258">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="da38e-259">Plik jest przydatne głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="da38e-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="da38e-260">Istnieje możliwość nie spakujesz ją z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="da38e-261">Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="da38e-262">Wdrażanie plików publikowanych w jakikolwiek sposób, który chcesz.</span><span class="sxs-lookup"><span data-stu-id="da38e-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="da38e-263">Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="da38e-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="da38e-264">Poniżej przedstawiono pełne *csproj* pliku dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="da38e-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="da38e-265">Ponadto program Visual Studio tworzy oddzielny profil publikowania (\*.pubxml) dla każdej z platform docelowych.</span><span class="sxs-lookup"><span data-stu-id="da38e-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="da38e-266">Na przykład w pliku o naszych profilu systemu linux (linux.pubxml) pojawia się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="da38e-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121. 
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="da38e-267">Niezależne wdrożenia przy użyciu zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="da38e-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="da38e-268">Niezależna wdrożenie z co najmniej jeden zależności innych firm obejmuje dodawanie zależności.</span><span class="sxs-lookup"><span data-stu-id="da38e-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="da38e-269">Przed utworzeniem aplikacji wymagane są następujące dodatkowe czynności:</span><span class="sxs-lookup"><span data-stu-id="da38e-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="da38e-270">Użyj **Menedżera pakietów NuGet** Dodaj odwołanie do pakietu NuGet do projektu; i jeśli pakiet nie jest jeszcze dostępna w systemie, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="da38e-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="da38e-271">Aby otworzyć Menedżera pakietów, wybierz **narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="da38e-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="da38e-272">Upewnij się, że `Newtonsoft.Json` jest zainstalowana w systemie, a jeśli tak nie jest, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="da38e-272">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="da38e-273">**Zainstalowane** karcie znajduje się lista pakietów NuGet, zainstalowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="da38e-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="da38e-274">Jeśli `Newtonsoft.Json` nie ma na liście, wybierz **Przeglądaj** kartę, a następnie wprowadź "Newtonsoft.Json" w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="da38e-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="da38e-275">Wybierz `Newtonsoft.Json` i w okienku po prawej stronie, wybierz swój projekt przed wybraniem **zainstalować**.</span><span class="sxs-lookup"><span data-stu-id="da38e-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="da38e-276">Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku **Zarządzaj pakietami dla rozwiązania** kartę.</span><span class="sxs-lookup"><span data-stu-id="da38e-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="da38e-277">Poniżej przedstawiono pełne *csproj* pliku dla tego projektu:</span><span class="sxs-lookup"><span data-stu-id="da38e-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="da38e-278">Visual Studio 15.6 i wcześniejszych</span><span class="sxs-lookup"><span data-stu-id="da38e-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

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

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="da38e-279">Visual Studio 15.7 i nowsze</span><span class="sxs-lookup"><span data-stu-id="da38e-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

<span data-ttu-id="da38e-280">Podczas wdrażania aplikacji, wszelkie zależności innych firm używanych w aplikacji znajdują się również z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da38e-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="da38e-281">Bibliotek innych firm nie są wymagane w systemie, na którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="da38e-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="da38e-282">Należy pamiętać, że można wdrożyć tylko niezależna wdrożenia przy użyciu biblioteki innej firmy na platformach obsługiwanych przez tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="da38e-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="da38e-283">Jest to podobne do mających zależności innych firm za pomocą natywnego zależności w danym wdrożeniu zależny od struktury, gdzie zależności natywnych nie istnieje na platformie docelowej, chyba że zostały wcześniej zainstalowane istnieje.</span><span class="sxs-lookup"><span data-stu-id="da38e-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="da38e-284">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da38e-284">See also</span></span>

* [<span data-ttu-id="da38e-285">Wdrożenie aplikacji programu .NET core</span><span class="sxs-lookup"><span data-stu-id="da38e-285">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="da38e-286">Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)</span><span class="sxs-lookup"><span data-stu-id="da38e-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
