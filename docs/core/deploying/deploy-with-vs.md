---
title: Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio
description: Dowiedz się, jak wdrożyć aplikację .NET Core za pomocą programu Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 11a322278ce3ff38964fe2fa389e0b4a58897ec4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449026"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="bdd9c-103">Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bdd9c-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="bdd9c-104">Aplikację .NET Core można wdrożyć jako *wdrożenie zależne od struktury,* które obejmuje pliki binarne aplikacji, ale zależy od obecności programu .NET Core w systemie docelowym lub jako *samodzielne wdrożenie,* które obejmuje zarówno aplikację, jak i pliki binarne .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="bdd9c-105">Aby zapoznać się z omówieniem wdrażania aplikacji .NET Core, zobacz [Wdrażanie aplikacji podstawowej .NET](index.md).</span><span class="sxs-lookup"><span data-stu-id="bdd9c-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="bdd9c-106">W poniższych sekcjach przedstawiono sposób tworzenia następujących rodzajów wdrożeń za pomocą programu Microsoft Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="bdd9c-107">Wdrożenie zależne od struktury</span><span class="sxs-lookup"><span data-stu-id="bdd9c-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="bdd9c-108">Wdrożenie zależne od struktury z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="bdd9c-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="bdd9c-109">Samodzielne wdrażanie</span><span class="sxs-lookup"><span data-stu-id="bdd9c-109">Self-contained deployment</span></span>
- <span data-ttu-id="bdd9c-110">Samodzielne wdrażanie z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="bdd9c-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="bdd9c-111">Aby uzyskać informacje dotyczące tworzenia aplikacji .NET Core za pomocą programu Visual Studio, zobacz [zależności i wymagania programu .NET Core](../install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="bdd9c-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/dependencies.md?pivots=os-windows).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="bdd9c-112">Wdrożenie zależne od struktury</span><span class="sxs-lookup"><span data-stu-id="bdd9c-112">Framework-dependent deployment</span></span>

<span data-ttu-id="bdd9c-113">Wdrażanie wdrożenia zależneod struktury bez zależności innych firm po prostu polega na tworzeniu, testowania i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="bdd9c-114">Prosty przykład napisany w języku C# ilustruje proces.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-114">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="bdd9c-115">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-115">Create the project.</span></span>

   <span data-ttu-id="bdd9c-116">Wybierz **pozycję Plik** > **nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="bdd9c-117">W oknie dialogowym **Nowy projekt** rozwiń kategorie projektów języka (C# lub Visual Basic) w okienku **Zainstalowane** typy projektów wybierz pozycję **.NET Core**, a następnie wybierz szablon aplikacji konsoli **(.NET Core)** w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="bdd9c-118">Wprowadź nazwę projektu, na przykład "FDD", w polu tekstowym **Nazwa.**</span><span class="sxs-lookup"><span data-stu-id="bdd9c-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="bdd9c-119">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="bdd9c-120">Dodaj kod źródłowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-120">Add the application's source code.</span></span>

   <span data-ttu-id="bdd9c-121">Otwórz *plik Program.cs* lub *Program.vb* w edytorze i zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="bdd9c-122">Monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne słowa wprowadzone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="bdd9c-123">Używa wyrażenia `\w+` regularnego do oddzielenia wyrazów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="bdd9c-124">Utwórz kompilację debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="bdd9c-125">Wybierz **rozwiązanie kompilacji** > **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="bdd9c-126">Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowanie** > **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="bdd9c-127">Wdrażanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-127">Deploy your app.</span></span>

   <span data-ttu-id="bdd9c-128">Po debugowania i przetestowaniu programu utwórz pliki do wdrożenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="bdd9c-129">Aby opublikować z programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="bdd9c-130">Zmień konfigurację rozwiązania z **Debug** do **Wydania** na pasku narzędzi, aby utworzyć wersję (a nie debugowanie) wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="bdd9c-131">Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="bdd9c-132">Na karcie **Publikowanie** wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="bdd9c-133">Program Visual Studio zapisuje pliki, które składają się na aplikację do lokalnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="bdd9c-134">Na karcie **Publikuj** jest teraz wyświetlany pojedynczy **profil, FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="bdd9c-135">Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** na karcie.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="bdd9c-136">Pliki wynikowe są umieszczane `Publish` w `publish` katalogu o nazwie w systemie Windows i w systemach Unix, który znajduje się w podkatalogu podkatalogu projektu *.\bin\release\netcoreapp2.1.*</span><span class="sxs-lookup"><span data-stu-id="bdd9c-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="bdd9c-137">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje o debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="bdd9c-138">Plik jest przydatny głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="bdd9c-139">Można wybrać, aby nie pakować go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="bdd9c-140">Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="bdd9c-141">Wdrażaj kompletny zestaw plików aplikacji w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="bdd9c-142">Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="bdd9c-143">Po zainstalowaniu użytkownicy mogą następnie wykonać `dotnet` aplikację za pomocą polecenia i `dotnet fdd.dll`podając nazwę pliku aplikacji, takich jak .</span><span class="sxs-lookup"><span data-stu-id="bdd9c-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="bdd9c-144">Oprócz plików binarnych aplikacji instalator powinien również łączyć instalator udostępnionej struktury lub sprawdzać go jako warunek wstępny w ramach instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="bdd9c-145">Instalacja udostępnionej struktury wymaga dostępu administratora/katalogu głównego, ponieważ jest dostępna na całym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="bdd9c-146">Wdrożenie zależne od struktury z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="bdd9c-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="bdd9c-147">Wdrażanie wdrożenia zależneod struktury z co najmniej jedną zależnościami innych firm wymaga, aby wszystkie zależności były dostępne dla projektu.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="bdd9c-148">Aby można było utworzyć aplikację, wymagane są następujące dodatkowe kroki:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="bdd9c-149">Użyj **Menedżera pakietów NuGet,** aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="bdd9c-150">Aby otworzyć menedżera pakietów, wybierz **narzędzia** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="bdd9c-151">Upewnij się, że zależności innych firm `Newtonsoft.Json`(na przykład) są zainstalowane w systemie i, jeśli nie są, zainstaluj je.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="bdd9c-152">**Zainstalowana** karta zawiera listę pakietów NuGet zainstalowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="bdd9c-153">Jeśli `Newtonsoft.Json` nie ma tam na liście, wybierz kartę **Przeglądaj** i wpisz "Newtonsoft.Json" w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="bdd9c-154">Zaznacz `Newtonsoft.Json` i w prawym okienku wybierz projekt przed wybraniem **opcji Zainstaluj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="bdd9c-155">Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku karty **Zarządzanie pakietami dla rozwiązania.**</span><span class="sxs-lookup"><span data-stu-id="bdd9c-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="bdd9c-156">Wdrożenie zależne od struktury z zależnościami innych firm jest tylko tak przenośne, jak jego zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-156">A framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="bdd9c-157">Jeśli na przykład biblioteka innej firmy obsługuje tylko system macOS, nie jest przenośna w systemach Windows.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="bdd9c-158">Dzieje się tak, jeśli zależność innej firmy sama zależy od kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="bdd9c-159">Dobrym tego przykładem jest [serwer Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), który wymaga natywnej zależności od [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="bdd9c-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="bdd9c-160">Gdy fdd jest tworzony dla aplikacji z tego rodzaju zależności innych firm, opublikowane dane wyjściowe zawiera folder dla każdego [identyfikatora wykonywania (RID),](../rid-catalog.md) który obsługuje zależności macierzystej (i który istnieje w pakiecie NuGet).</span><span class="sxs-lookup"><span data-stu-id="bdd9c-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a><span data-ttu-id="bdd9c-161">Samodzielne wdrażanie bez zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="bdd9c-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="bdd9c-162">Wdrażanie samodzielnego wdrożenia bez zależności innych firm wiąże się z tworzeniem projektu, modyfikowaniem pliku *csproj,* tworzeniem, testowaniem i publikowaniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="bdd9c-163">Prosty przykład napisany w języku C# ilustruje proces.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="bdd9c-164">Rozpoczynasz od tworzenia, kodowania i testowania projektu tak samo, jak wdrożenie zależne od struktury:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="bdd9c-165">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-165">Create the project.</span></span>

   <span data-ttu-id="bdd9c-166">Wybierz **pozycję Plik** > **nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="bdd9c-167">W oknie dialogowym **Nowy projekt** rozwiń kategorie projektów języka (C# lub Visual Basic) w okienku **Zainstalowane** typy projektów wybierz pozycję **.NET Core**, a następnie wybierz szablon aplikacji konsoli **(.NET Core)** w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="bdd9c-168">Wprowadź nazwę projektu, na przykład "SCD", w polu tekstowym **Nazwa** i wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="bdd9c-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="bdd9c-169">Dodaj kod źródłowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-169">Add the application's source code.</span></span>

   <span data-ttu-id="bdd9c-170">Otwórz *plik Program.cs* lub *Program.vb* w edytorze i zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="bdd9c-171">Monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne słowa wprowadzone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="bdd9c-172">Używa wyrażenia `\w+` regularnego do oddzielenia wyrazów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="bdd9c-173">Określ, czy chcesz użyć trybu niezmiennego globalizacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="bdd9c-174">Szczególnie jeśli aplikacja jest przeznaczona dla systemu Linux, można zmniejszyć całkowity rozmiar wdrożenia, korzystając z [trybu niezmiennego globalizacji.](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)</span><span class="sxs-lookup"><span data-stu-id="bdd9c-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span> <span data-ttu-id="bdd9c-175">Tryb niezmienny globalizacji jest przydatny w przypadku aplikacji, które nie są globalnie świadome i które mogą używać konwencji formatowania, konwencji wielkości liter oraz porównania i sortowania ciągów [kultury niezmiennej.](xref:System.Globalization.CultureInfo.InvariantCulture)</span><span class="sxs-lookup"><span data-stu-id="bdd9c-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="bdd9c-176">Aby włączyć tryb niezmienny, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań**i wybierz polecenie **Edit SCD.csproj** lub **Edit SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="bdd9c-177">Następnie dodaj do pliku następujące wyróżnione wiersze:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-177">Then add the following highlighted lines to the file:</span></span>

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. <span data-ttu-id="bdd9c-178">Utwórz kompilację debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="bdd9c-179">Wybierz **rozwiązanie kompilacji** > **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="bdd9c-180">Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowanie** > **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="bdd9c-181">Ten krok debugowania umożliwia identyfikowanie problemów z aplikacją, gdy jest uruchomiona na platformie hosta.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="bdd9c-182">Nadal będziesz musiał przetestować go na każdej z platform docelowych.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="bdd9c-183">Jeśli włączysz tryb niezmienny globalizacji, należy szczególnie sprawdzić, czy brak danych zależnych od kultury jest odpowiedni dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="bdd9c-184">Po zakończeniu debugowania można opublikować wdrożenie niezależne:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="bdd9c-185">Visual Studio 15.6 i wcześniejsze</span><span class="sxs-lookup"><span data-stu-id="bdd9c-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="bdd9c-186">Po debugowania i przetestowaniu programu, utwórz pliki do wdrożenia z aplikacją dla każdej platformy, na której jest przeznaczona.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="bdd9c-187">Aby opublikować aplikację z programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="bdd9c-188">Zdefiniuj platformy, na które będzie kierować aplikacja.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="bdd9c-189">Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz **polecenie Edit SCD.csproj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="bdd9c-190">Utwórz `<RuntimeIdentifiers>` tag `<PropertyGroup>` w sekcji pliku *csproj,* który definiuje platformy, których dotyczy aplikacja, i określ identyfikator czasu wykonywania (RID) każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="bdd9c-191">Należy również dodać średnik, aby oddzielić identyfikatory IDENTYFIKATORY.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-191">You also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="bdd9c-192">Zobacz [katalog identyfikatorów identyfikatorów](../rid-catalog.md) środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="bdd9c-193">Na przykład poniższy przykład wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X w wersji 10.11.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="bdd9c-194">Element `<RuntimeIdentifiers>` może przejść `<PropertyGroup>` do każdego, który masz w pliku *csproj.*</span><span class="sxs-lookup"><span data-stu-id="bdd9c-194">The `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="bdd9c-195">Pełny przykładowy plik *csproj* pojawi się w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="bdd9c-196">Opublikuj aplikację.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-196">Publish your app.</span></span>

   <span data-ttu-id="bdd9c-197">Po debugowania i przetestowaniu programu, utwórz pliki do wdrożenia z aplikacją dla każdej platformy, na której jest przeznaczona.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="bdd9c-198">Aby opublikować aplikację z programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="bdd9c-199">Zmień konfigurację rozwiązania z **Debug** do **Wydania** na pasku narzędzi, aby utworzyć wersję (a nie debugowanie) wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="bdd9c-200">Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="bdd9c-201">Na karcie **Publikowanie** wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="bdd9c-202">Program Visual Studio zapisuje pliki, które składają się na aplikację do lokalnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="bdd9c-203">Na karcie **Publikuj** jest teraz wyświetlany pojedynczy **profil, FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="bdd9c-204">Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** na karcie. **Docelowy czas wykonywania** identyfikuje, który czas wykonywania został opublikowany, a **lokalizacja docelowa** określa, gdzie zostały zapisane pliki dla samodzielnego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="bdd9c-205">Program Visual Studio domyślnie zapisuje wszystkie opublikowane pliki w jednym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="bdd9c-206">Dla wygody najlepiej jest utworzyć oddzielne profile dla każdego docelowego czasu wykonywania i umieścić opublikowane pliki w katalogu specyficznym dla platformy.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="bdd9c-207">Obejmuje to utworzenie oddzielnego profilu publikowania dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="bdd9c-208">Więc teraz odbudować aplikację dla każdej platformy, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="bdd9c-209">Wybierz **pozycję Utwórz nowy profil** w oknie dialogowym **Publikowanie.**</span><span class="sxs-lookup"><span data-stu-id="bdd9c-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="bdd9c-210">W oknie **dialogowym Wybieranie obiektu docelowego publikowania** zmień pozycję **Wybierz lokalizację folderu** do *kosza\Release\PublishOutput\win10-x64*.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="bdd9c-211">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-211">Select **OK**.</span></span>

         1. <span data-ttu-id="bdd9c-212">Wybierz nowy profil **(FolderProfile1)** na liście profilów i upewnij się, `win10-x64`że docelowy czas **wykonywania** jest .</span><span class="sxs-lookup"><span data-stu-id="bdd9c-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="bdd9c-213">Jeśli tak nie jest, wybierz **pozycję Ustawienia**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="bdd9c-214">W oknie dialogowym **Ustawienia profilu** zmień docelowy **czas wykonywania** i `win10-x64` wybierz pozycję **Zapisz**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="bdd9c-215">W przeciwnym razie wybierz **pozycję Anuluj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="bdd9c-216">Wybierz **pozycję Publikuj,** aby opublikować aplikację dla 64-bitowych platform systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="bdd9c-217">Wykonaj ponownie poprzednie kroki, aby `osx.10.11-x64` utworzyć profil dla platformy.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="bdd9c-218">**Lokalizacja docelowa** to *bin\Release\PublishOutput\osx.10.11-x64*, a `osx.10.11-x64`docelowy **m.in.**</span><span class="sxs-lookup"><span data-stu-id="bdd9c-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="bdd9c-219">Nazwa, którą program Visual Studio przypisuje do tego profilu, to **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="bdd9c-220">Każda lokalizacja docelowa zawiera kompletny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików .NET Core) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-220">Each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="bdd9c-221">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje o debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="bdd9c-222">Plik jest przydatny głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="bdd9c-223">Można wybrać, aby nie pakować go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="bdd9c-224">Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="bdd9c-225">Wdrażaj opublikowane pliki w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="bdd9c-226">Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="bdd9c-227">Poniżej znajduje się kompletny plik *csproj* dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="bdd9c-228">Visual Studio 15.7 i nowsze</span><span class="sxs-lookup"><span data-stu-id="bdd9c-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="bdd9c-229">Po debugowania i przetestowaniu programu, utwórz pliki do wdrożenia z aplikacją dla każdej platformy, na której jest przeznaczona.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="bdd9c-230">Wiąże się to z utworzeniem oddzielnego profilu dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="bdd9c-231">Dla każdej platformy, na którą dotyczy aplikacji, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="bdd9c-232">Utwórz profil dla swojej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="bdd9c-233">Jeśli jest to pierwszy utworzony profil, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="bdd9c-234">Jeśli profil został już utworzony, kliknij prawym przyciskiem myszy projekt, aby otworzyć okno **dialogowe Publikowanie,** jeśli nie jest jeszcze otwarty.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="bdd9c-235">Następnie wybierz **pozycję Nowy profil**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="bdd9c-236">Zostanie otwarte okno **dialogowe Wybieranie obiektu docelowego publikowania.**</span><span class="sxs-lookup"><span data-stu-id="bdd9c-236">The **Pick a Publish Target** dialog box opens.</span></span>

1. <span data-ttu-id="bdd9c-237">Wybierz lokalizację, w której program Visual Studio publikuje aplikację.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="bdd9c-238">Jeśli publikujesz tylko na jednej platformie, możesz zaakceptować wartość domyślną w polu **tekstowym Wybierz folder;** spowoduje to opublikowanie wdrożenia aplikacji zależnego od struktury w \* \<katalogu projektu>\bin\Release\netcoreapp2.1\publish\* directory.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span></span>

   <span data-ttu-id="bdd9c-239">Jeśli publikujesz na więcej niż jednej platformie, dołącz ciąg, który identyfikuje platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="bdd9c-240">Na przykład jeśli dościeżnica pliku zostanie dołączona ciąg "linux", program Visual Studio opublikuje zależne od struktury wdrożenie aplikacji do \* \<katalogu projektu>\bin\Release\netcoreapp2.1\publish\linux.\*</span><span class="sxs-lookup"><span data-stu-id="bdd9c-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="bdd9c-241">Utwórz profil, wybierając ikonę listy rozwijanej obok przycisku **Publikuj** i wybierając pozycję **Utwórz profil**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="bdd9c-242">Następnie wybierz przycisk **Utwórz profil,** aby utworzyć profil.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="bdd9c-243">Wskaż, że publikujesz niezależne wdrożenie i zdefiniuj platformę, na którą będzie kierować aplikację.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="bdd9c-244">W oknie **dialogowym Publikowanie** wybierz łącze **Konfigurowanie,** aby otworzyć okno dialogowe **Ustawienia profilu.**</span><span class="sxs-lookup"><span data-stu-id="bdd9c-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="bdd9c-245">Wybierz **opcję Samodzielne w** polu listy Tryb **wdrażania.**</span><span class="sxs-lookup"><span data-stu-id="bdd9c-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="bdd9c-246">W polu listy **Docelowe uruchomienie** wybierz jedną z platform, na których znajduje się aplikacja.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="bdd9c-247">Wybierz **pozycję Zapisz,** aby zaakceptować zmiany i zamknij okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="bdd9c-248">Nazwij swój profil.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-248">Name your profile.</span></span>

   1. <span data-ttu-id="bdd9c-249">Wybierz **pozycję Akcje** > **Zmień nazwę profilu,** aby nazwać swój profil.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="bdd9c-250">Przypisz profil nazwę identyfikującą platformę docelową, a następnie wybierz \**Zapisz*.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="bdd9c-251">Powtórz te kroki, aby zdefiniować wszelkie dodatkowe platformy docelowe, które są przeznaczone dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="bdd9c-252">Skonfigurowato swoje profile i są teraz gotowe do opublikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="bdd9c-253">W tym celu:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-253">To do this:</span></span>

   1. <span data-ttu-id="bdd9c-254">Jeśli okno **Publikowania** nie jest aktualnie otwarte, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="bdd9c-255">Wybierz profil, który chcesz opublikować, a następnie wybierz **pozycję Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="bdd9c-256">Zrób to dla każdego profilu, który ma zostać opublikowany.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="bdd9c-257">Każda lokalizacja docelowa (w naszym przykładzie bin\release\netcoreapp2.1\publish\\*profile-name* zawiera kompletny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików .NET Core) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-257">Each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="bdd9c-258">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje o debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="bdd9c-259">Plik jest przydatny głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="bdd9c-260">Można wybrać, aby nie pakować go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="bdd9c-261">Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="bdd9c-262">Wdrażaj opublikowane pliki w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="bdd9c-263">Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="bdd9c-264">Poniżej znajduje się kompletny plik *csproj* dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="bdd9c-265">Ponadto visual studio tworzy oddzielny profil\*publikowania (.pubxml) dla każdej platformy, na którą kierujesz.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="bdd9c-266">Na przykład plik dla naszego profilu linuksa (linux.pubxml) pojawia się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

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

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="bdd9c-267">Samodzielne wdrażanie z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="bdd9c-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="bdd9c-268">Wdrażanie samodzielnego wdrożenia z co najmniej jedną zależnościami innych firm polega na dodawaniu zależności.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="bdd9c-269">Aby można było utworzyć aplikację, wymagane są następujące dodatkowe kroki:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="bdd9c-270">Użyj **Menedżera pakietów NuGet,** aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="bdd9c-271">Aby otworzyć menedżera pakietów, wybierz **narzędzia** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="bdd9c-272">Upewnij się, że zależności innych firm `Newtonsoft.Json`(na przykład) są zainstalowane w systemie i, jeśli nie są, zainstaluj je.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="bdd9c-273">**Zainstalowana** karta zawiera listę pakietów NuGet zainstalowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="bdd9c-274">Jeśli `Newtonsoft.Json` nie ma tam na liście, wybierz kartę **Przeglądaj** i wpisz "Newtonsoft.Json" w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="bdd9c-275">Zaznacz `Newtonsoft.Json` i w prawym okienku wybierz projekt przed wybraniem **opcji Zainstaluj**.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="bdd9c-276">Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku karty **Zarządzanie pakietami dla rozwiązania.**</span><span class="sxs-lookup"><span data-stu-id="bdd9c-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="bdd9c-277">Poniżej znajduje się kompletny plik *csproj* dla tego projektu:</span><span class="sxs-lookup"><span data-stu-id="bdd9c-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="bdd9c-278">Visual Studio 15.6 i wcześniejsze</span><span class="sxs-lookup"><span data-stu-id="bdd9c-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

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

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="bdd9c-279">Visual Studio 15.7 i nowsze</span><span class="sxs-lookup"><span data-stu-id="bdd9c-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

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

<span data-ttu-id="bdd9c-280">Podczas wdrażania aplikacji wszelkie zależności innych firm używane w aplikacji są również zawarte z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="bdd9c-281">Biblioteki innych firm nie są wymagane w systemie, w którym aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="bdd9c-282">Wdrożenie samodzielne można wdrażać tylko z biblioteką innych firm na platformach obsługiwanych przez tę bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-282">You can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="bdd9c-283">Jest to podobne do zależności innych firm z zależnościami macierzystymi we wdrożeniu zależnym od struktury, gdzie zależności macierzyste nie będą istnieć na platformie docelowej, chyba że zostały wcześniej tam zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="bdd9c-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdd9c-284">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bdd9c-284">See also</span></span>

- [<span data-ttu-id="bdd9c-285">Wdrożenie aplikacji podstawowej .NET</span><span class="sxs-lookup"><span data-stu-id="bdd9c-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="bdd9c-286">Wykaz identyfikatora środowiska uruchomienionowego programu .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="bdd9c-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
