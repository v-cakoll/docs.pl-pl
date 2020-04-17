---
title: Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio
description: Dowiedz się, jak wdrożyć aplikację .NET Core w programie Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: f2299ac807c845dab482306cc4c710560bb7f1e7
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607865"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="57003-103">Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="57003-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="57003-104">Aplikację .NET Core można wdrożyć jako *wdrożenie zależne od struktury,* które zawiera pliki binarne aplikacji, ale zależy od obecności programu .NET Core w systemie docelowym lub jako *samodzielne wdrożenie,* które obejmuje zarówno pliki binarne aplikacji, jak i rdzenia .NET.</span><span class="sxs-lookup"><span data-stu-id="57003-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="57003-105">Aby zapoznać się z omówieniem wdrażania aplikacji .NET Core, zobacz [.NET Core Application Deployment](index.md).</span><span class="sxs-lookup"><span data-stu-id="57003-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="57003-106">W poniższych sekcjach pokazano, jak używać programu Microsoft Visual Studio do tworzenia następujących rodzajów wdrożeń:</span><span class="sxs-lookup"><span data-stu-id="57003-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="57003-107">Wdrożenie zależne od struktury</span><span class="sxs-lookup"><span data-stu-id="57003-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="57003-108">Wdrożenie zależne od struktury z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="57003-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="57003-109">Samodzielne wdrożenie</span><span class="sxs-lookup"><span data-stu-id="57003-109">Self-contained deployment</span></span>
- <span data-ttu-id="57003-110">Samodzielne wdrażanie z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="57003-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="57003-111">Aby uzyskać informacje na temat tworzenia aplikacji .NET Core za pomocą programu Visual Studio, zobacz [zależności i wymagania dotyczące rdzenia .NET](../install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="57003-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/dependencies.md?pivots=os-windows).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="57003-112">Wdrożenie zależne od struktury</span><span class="sxs-lookup"><span data-stu-id="57003-112">Framework-dependent deployment</span></span>

<span data-ttu-id="57003-113">Wdrażanie wdrożenia zależnego od struktury bez zależności innych firm po prostu obejmuje tworzenie, testowanie i publikowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="57003-114">Prosty przykład napisany w języku C# ilustruje proces.</span><span class="sxs-lookup"><span data-stu-id="57003-114">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="57003-115">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="57003-115">Create the project.</span></span>

   <span data-ttu-id="57003-116">Wybierz **pozycję Plik** > **nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="57003-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="57003-117">W oknie dialogowym **Nowy projekt** rozwiń kategorie projektów języka (C# lub Visual Basic) w okienku **Zainstalowane** typy projektów, wybierz pozycję **.NET Core**, a następnie wybierz szablon Aplikacja konsoli **(.NET Core)** w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="57003-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="57003-118">Wprowadź nazwę projektu, taką jak "FDD", w polu tekstowym **Nazwa.**</span><span class="sxs-lookup"><span data-stu-id="57003-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="57003-119">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="57003-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="57003-120">Dodaj kod źródłowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-120">Add the application's source code.</span></span>

   <span data-ttu-id="57003-121">Otwórz *plik Program.cs* lub *Program.vb* w edytorze i zastąp automatyczniegenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="57003-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="57003-122">Monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne słowa wprowadzone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="57003-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="57003-123">Używa wyrażenia `\w+` regularnego do oddzielenia wyrazów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="57003-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="57003-124">Utwórz kompilację debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="57003-125">Wybierz **opcję Zbuduj** > **rozwiązanie kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="57003-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="57003-126">Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowanie** > **start debugowania**.</span><span class="sxs-lookup"><span data-stu-id="57003-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="57003-127">Wdrażanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-127">Deploy your app.</span></span>

   <span data-ttu-id="57003-128">Po debugowanie i przetestowanie programu, należy utworzyć pliki, które mają być wdrożone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="57003-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="57003-129">Aby opublikować z programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="57003-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="57003-130">Zmień konfigurację rozwiązania z **Debugowania** na **Zwolnij** na pasku narzędzi, aby utworzyć wersję aplikacji w wersji (a nie debugowania).</span><span class="sxs-lookup"><span data-stu-id="57003-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="57003-131">Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="57003-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="57003-132">Na karcie **Publikowanie** wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="57003-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="57003-133">Visual Studio zapisuje pliki, które składają się na aplikację do lokalnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="57003-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="57003-134">Na karcie **Publikowanie** jest teraz wyświetlany pojedynczy profil **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="57003-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="57003-135">Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** na karcie.</span><span class="sxs-lookup"><span data-stu-id="57003-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="57003-136">Wynikowe pliki są umieszczane w `Publish` katalogu `publish` o nazwie w systemie Windows i w systemach Unix, który znajduje się w podkatalogu projektu *.\bin\release\netcoreapp2.1.*</span><span class="sxs-lookup"><span data-stu-id="57003-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="57003-137">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje debugowania o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="57003-138">Plik jest przydatny przede wszystkim do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="57003-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="57003-139">Można wybrać opcję niepakować go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="57003-140">Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="57003-141">Wdrażaj kompletny zestaw plików aplikacji w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="57003-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="57003-142">Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru.</span><span class="sxs-lookup"><span data-stu-id="57003-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="57003-143">Po zainstalowaniu użytkownicy mogą następnie `dotnet` wykonać aplikację za pomocą polecenia i `dotnet fdd.dll`podając nazwę pliku aplikacji, na przykład .</span><span class="sxs-lookup"><span data-stu-id="57003-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="57003-144">Oprócz plików binarnych aplikacji instalator powinien również wiązać instalatora współużytkowania struktury udostępnionej lub sprawdzić, czy jest on wymagany jako warunek wstępny w ramach instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="57003-145">Instalacja udostępnionej struktury wymaga dostępu administratora/administratora, ponieważ jest on dostępny na całej maszynie.</span><span class="sxs-lookup"><span data-stu-id="57003-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="57003-146">Wdrożenie zależne od struktury z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="57003-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="57003-147">Wdrażanie wdrożenia zależnego od struktury z co najmniej jedną lub kilkoma zależnościami innych firm wymaga, aby wszystkie zależności były dostępne dla projektu.</span><span class="sxs-lookup"><span data-stu-id="57003-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="57003-148">Przed utworzeniem aplikacji wymagane są następujące dodatkowe kroki:</span><span class="sxs-lookup"><span data-stu-id="57003-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="57003-149">Użyj **Menedżera pakietów NuGet,** aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="57003-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="57003-150">Aby otworzyć Menedżera pakietów, wybierz pozycję **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span><span class="sxs-lookup"><span data-stu-id="57003-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="57003-151">Upewnij się, że zależności innych firm `Newtonsoft.Json`(na przykład) są zainstalowane w systemie, a jeśli nie, zainstaluj je.</span><span class="sxs-lookup"><span data-stu-id="57003-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="57003-152">Karta **Zainstalowana** zawiera listę pakietów NuGet zainstalowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="57003-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="57003-153">Jeśli `Newtonsoft.Json` nie ma tam na liście, wybierz kartę **Przeglądaj** i wpisz "Newtonsoft.Json" w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="57003-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="57003-154">Zaznacz `Newtonsoft.Json` i w prawym okienku wybierz projekt przed wybraniem opcji **Zainstaluj**.</span><span class="sxs-lookup"><span data-stu-id="57003-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="57003-155">Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku karty **Zarządzanie pakietami dla rozwiązania.**</span><span class="sxs-lookup"><span data-stu-id="57003-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="57003-156">Wdrożenie zależne od struktury z zależnościami innych firm jest tylko tak przenośne, jak zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="57003-156">A framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="57003-157">Jeśli na przykład biblioteka innej firmy obsługuje tylko system macOS, aplikacja nie jest przenośna do systemów Windows.</span><span class="sxs-lookup"><span data-stu-id="57003-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="57003-158">Dzieje się tak, jeśli sama zależność innych firm zależy od kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="57003-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="57003-159">Dobrym przykładem jest [serwer Kestrel,](/aspnet/core/fundamentals/servers/kestrel)który wymaga natywnej zależności od [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="57003-159">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="57003-160">Po utworzeniu FDD dla aplikacji z tego rodzaju zależności innych firm, opublikowane dane wyjściowe zawiera folder dla każdego [identyfikatora środowiska wykonawczego (RID),](../rid-catalog.md) który obsługuje zależność macierzystą (i który istnieje w pakiecie NuGet).</span><span class="sxs-lookup"><span data-stu-id="57003-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="self-contained-deployment-without-third-party-dependencies"></a><a name="simpleSelf"></a><span data-ttu-id="57003-161">Samodzielne wdrożenie bez zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="57003-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="57003-162">Wdrażanie samodzielnego wdrożenia bez zależności innych firm wymaga utworzenia projektu, modyfikowania pliku *csproj,* tworzenia, testowania i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="57003-163">Prosty przykład napisany w języku C# ilustruje proces.</span><span class="sxs-lookup"><span data-stu-id="57003-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="57003-164">Można rozpocząć od tworzenia, kodowania i testowania projektu, tak jak wdrożenie zależne od struktury:</span><span class="sxs-lookup"><span data-stu-id="57003-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="57003-165">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="57003-165">Create the project.</span></span>

   <span data-ttu-id="57003-166">Wybierz **pozycję Plik** > **nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="57003-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="57003-167">W oknie dialogowym **Nowy projekt** rozwiń kategorie projektów języka (C# lub Visual Basic) w okienku **Zainstalowane** typy projektów, wybierz pozycję **.NET Core**, a następnie wybierz szablon Aplikacja konsoli **(.NET Core)** w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="57003-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="57003-168">Wprowadź nazwę projektu, taką jak "SCD", w polu tekstowym **Nazwa** i wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="57003-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="57003-169">Dodaj kod źródłowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-169">Add the application's source code.</span></span>

   <span data-ttu-id="57003-170">Otwórz *plik Program.cs* lub *Program.vb* w edytorze i zastąp automatyczniegenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="57003-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="57003-171">Monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne słowa wprowadzone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="57003-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="57003-172">Używa wyrażenia `\w+` regularnego do oddzielenia wyrazów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="57003-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="57003-173">Określ, czy chcesz używać trybu niezmiennego globalizacji.</span><span class="sxs-lookup"><span data-stu-id="57003-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="57003-174">Szczególnie jeśli aplikacja jest przeznaczona dla systemu Linux, można zmniejszyć całkowity rozmiar wdrożenia, korzystając z [trybu niezmiennego globalizacji.](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)</span><span class="sxs-lookup"><span data-stu-id="57003-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span> <span data-ttu-id="57003-175">Tryb niezmienny globalizacji jest przydatny w przypadku aplikacji, które nie są globalnie świadome i które mogą używać konwencji formatowania, konwencji wielkości liter i porównywania ciągów i kolejności sortowania [kultury niezmiennej](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="57003-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="57003-176">Aby włączyć tryb niezmienny, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań**i wybierz polecenie **Edytuj SCD.csproj** lub **Edytuj SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="57003-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="57003-177">Następnie dodaj do pliku następujące wyróżnione wiersze:</span><span class="sxs-lookup"><span data-stu-id="57003-177">Then add the following highlighted lines to the file:</span></span>

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. <span data-ttu-id="57003-178">Utwórz kompilację debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="57003-179">Wybierz **opcję Zbuduj** > **rozwiązanie kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="57003-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="57003-180">Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowanie** > **start debugowania**.</span><span class="sxs-lookup"><span data-stu-id="57003-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="57003-181">Ten krok debugowania umożliwia identyfikowanie problemów z aplikacją, gdy jest uruchomiona na platformie hosta.</span><span class="sxs-lookup"><span data-stu-id="57003-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="57003-182">Nadal będziesz musiał przetestować go na każdej z platform docelowych.</span><span class="sxs-lookup"><span data-stu-id="57003-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="57003-183">Jeśli włączono tryb niezmienny globalizacji, należy szczególnie sprawdzić, czy brak danych wrażliwych na kulturę jest odpowiedni dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="57003-184">Po zakończeniu debugowania można opublikować samodzielne wdrożenie:</span><span class="sxs-lookup"><span data-stu-id="57003-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="57003-185">Visual Studio 15.6 i starsze</span><span class="sxs-lookup"><span data-stu-id="57003-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="57003-186">Po debugowanie i przetestowanie programu, należy utworzyć pliki, które mają być wdrożone z aplikacją dla każdej platformy, która jest przeznaczona.</span><span class="sxs-lookup"><span data-stu-id="57003-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="57003-187">Aby opublikować aplikację w programie Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="57003-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="57003-188">Zdefiniuj platformy, na które będzie kierowana aplikacja.</span><span class="sxs-lookup"><span data-stu-id="57003-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="57003-189">Kliknij prawym przyciskiem myszy swój projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz **pozycję Edytuj scd.csproj**.</span><span class="sxs-lookup"><span data-stu-id="57003-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="57003-190">Utwórz `<RuntimeIdentifiers>` znacznik `<PropertyGroup>` w sekcji pliku *csproj,* który definiuje platformy docelowe aplikacji i określ identyfikator środowiska wykonawczego (RID) każdej platformy, na którą chcesz kierować reklamy.</span><span class="sxs-lookup"><span data-stu-id="57003-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="57003-191">Należy również dodać średnik, aby oddzielić identyfikatory RYT.</span><span class="sxs-lookup"><span data-stu-id="57003-191">You also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="57003-192">Zobacz [katalog IDentifier środowiska uruchomieniowego](../rid-catalog.md) dla listy identyfikatorów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="57003-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="57003-193">Na przykład poniższy przykład wskazuje, że aplikacja działa na 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X w wersji 10.11.</span><span class="sxs-lookup"><span data-stu-id="57003-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="57003-194">Element `<RuntimeIdentifiers>` może przejść `<PropertyGroup>` do dowolnego, który masz w pliku *csproj.*</span><span class="sxs-lookup"><span data-stu-id="57003-194">The `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="57003-195">Pełny przykładowy plik *csproj* pojawia się w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="57003-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="57003-196">Opublikuj aplikację.</span><span class="sxs-lookup"><span data-stu-id="57003-196">Publish your app.</span></span>

   <span data-ttu-id="57003-197">Po debugowanie i przetestowanie programu, należy utworzyć pliki, które mają być wdrożone z aplikacją dla każdej platformy, która jest przeznaczona.</span><span class="sxs-lookup"><span data-stu-id="57003-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="57003-198">Aby opublikować aplikację w programie Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="57003-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="57003-199">Zmień konfigurację rozwiązania z **Debugowania** na **Zwolnij** na pasku narzędzi, aby utworzyć wersję aplikacji w wersji (a nie debugowania).</span><span class="sxs-lookup"><span data-stu-id="57003-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="57003-200">Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="57003-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="57003-201">Na karcie **Publikowanie** wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="57003-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="57003-202">Visual Studio zapisuje pliki, które składają się na aplikację do lokalnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="57003-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="57003-203">Na karcie **Publikowanie** jest teraz wyświetlany pojedynczy profil **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="57003-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="57003-204">Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** na **Target Location** **karcie.**</span><span class="sxs-lookup"><span data-stu-id="57003-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="57003-205">Visual Studio domyślnie zapisuje wszystkie opublikowane pliki w jednym katalogu.</span><span class="sxs-lookup"><span data-stu-id="57003-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="57003-206">Dla wygody najlepiej jest utworzyć oddzielne profile dla każdego docelowego środowiska uruchomieniowego i umieścić opublikowane pliki w katalogu specyficznym dla platformy.</span><span class="sxs-lookup"><span data-stu-id="57003-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="57003-207">Obejmuje to tworzenie oddzielnego profilu publikowania dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="57003-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="57003-208">Więc teraz odbudować aplikację dla każdej platformy, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="57003-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="57003-209">Wybierz **pozycję Utwórz nowy profil** w oknie dialogowym **Publikowanie.**</span><span class="sxs-lookup"><span data-stu-id="57003-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="57003-210">W oknie **dialogowym Wybieranie miejsca docelowego publikowania** zmień lokalizację **folderu na** *bin\Release\PublishOutput\win10-x64*.</span><span class="sxs-lookup"><span data-stu-id="57003-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="57003-211">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="57003-211">Select **OK**.</span></span>

         1. <span data-ttu-id="57003-212">Wybierz nowy profil (**FolderProfile1**) na liście profili i upewnij `win10-x64`się, że **docelowy czas uruchomieniowy** jest .</span><span class="sxs-lookup"><span data-stu-id="57003-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="57003-213">Jeśli tak nie jest, wybierz pozycję **Ustawienia**.</span><span class="sxs-lookup"><span data-stu-id="57003-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="57003-214">W oknie dialogowym **Ustawienia profilu** zmień **docelowy czas pracy** na `win10-x64` i wybierz pozycję **Zapisz**.</span><span class="sxs-lookup"><span data-stu-id="57003-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="57003-215">W przeciwnym razie wybierz pozycję **Anuluj**.</span><span class="sxs-lookup"><span data-stu-id="57003-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="57003-216">Wybierz **pozycję Publikuj,** aby opublikować aplikację dla 64-bitowych platform systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="57003-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="57003-217">Wykonaj ponownie poprzednie kroki, aby `osx.10.11-x64` utworzyć profil dla platformy.</span><span class="sxs-lookup"><span data-stu-id="57003-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="57003-218">**Lokalizacja docelowa** to *bin\Release\PublishOutput\osx.10.11-x64*, a `osx.10.11-x64` **docelowy czas uruchomieniowy** to .</span><span class="sxs-lookup"><span data-stu-id="57003-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="57003-219">Nazwa przypisywana przez program Visual Studio do tego profilu to **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="57003-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="57003-220">Każda lokalizacja docelowa zawiera kompletny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików .NET Core) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-220">Each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="57003-221">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje debugowania o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="57003-222">Plik jest przydatny przede wszystkim do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="57003-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="57003-223">Można wybrać opcję niepakować go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="57003-224">Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="57003-225">Wdrażanie opublikowanych plików w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="57003-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="57003-226">Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru.</span><span class="sxs-lookup"><span data-stu-id="57003-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="57003-227">Poniżej znajduje się kompletny plik *csproj* dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="57003-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="57003-228">Visual Studio 15.7 i nowsze</span><span class="sxs-lookup"><span data-stu-id="57003-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="57003-229">Po debugowanie i przetestowanie programu, należy utworzyć pliki, które mają być wdrożone z aplikacją dla każdej platformy, która jest przeznaczona.</span><span class="sxs-lookup"><span data-stu-id="57003-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="57003-230">Wiąże się to z utworzeniem osobnego profilu dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="57003-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="57003-231">Dla każdej platformy, na którą docelowych aplikacji, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="57003-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="57003-232">Utwórz profil dla swojej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="57003-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="57003-233">Jeśli jest to pierwszy utworzony profil, kliknij prawym przyciskiem myszy projekt (a nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="57003-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="57003-234">Jeśli profil został już utworzony, kliknij go prawym przyciskiem myszy, aby otworzyć okno dialogowe **Publikowania,** jeśli nie zostało jeszcze otwarte.</span><span class="sxs-lookup"><span data-stu-id="57003-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="57003-235">Następnie wybierz **pozycję Nowy profil**.</span><span class="sxs-lookup"><span data-stu-id="57003-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="57003-236">Zostanie otwarte okno dialogowe **Wybieranie celu publikowania.**</span><span class="sxs-lookup"><span data-stu-id="57003-236">The **Pick a Publish Target** dialog box opens.</span></span>

1. <span data-ttu-id="57003-237">Wybierz lokalizację, w której program Visual Studio publikuje aplikację.</span><span class="sxs-lookup"><span data-stu-id="57003-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="57003-238">Jeśli publikujesz tylko na jednej platformie, możesz zaakceptować wartość domyślną w polu **tekstowym Wybierz folder;** w tym celu opublikowano zależne od struktury wdrożenie aplikacji w \* \<katalogu projektu>\bin\Release\netcoreapp2.1\publish\* directory.</span><span class="sxs-lookup"><span data-stu-id="57003-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span></span>

   <span data-ttu-id="57003-239">Jeśli publikujesz na więcej niż jednej platformie, dołącz ciąg identyfikujący platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="57003-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="57003-240">Na przykład jeśli dodasz ciąg "linux" do ścieżki pliku, program Visual Studio opublikuje zależne od struktury wdrożenie aplikacji do \* \<katalogu projektu>\bin\Release\netcoreapp2.1\publish\linux\* directory.</span><span class="sxs-lookup"><span data-stu-id="57003-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="57003-241">Utwórz profil, zaznaczając ikonę listy rozwijanej obok przycisku **Publikuj** i wybierając pozycję **Utwórz profil**.</span><span class="sxs-lookup"><span data-stu-id="57003-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="57003-242">Następnie wybierz przycisk **Utwórz profil,** aby utworzyć profil.</span><span class="sxs-lookup"><span data-stu-id="57003-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="57003-243">Wskaż, że publikujesz samodzielne wdrożenie i zdefiniuj platformę, na którą będzie kierowana aplikacja.</span><span class="sxs-lookup"><span data-stu-id="57003-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="57003-244">W oknie dialogowym **Publikowanie** wybierz **łącze Konfiguruj,** aby otworzyć okno dialogowe **Ustawienia profilu.**</span><span class="sxs-lookup"><span data-stu-id="57003-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="57003-245">Wybierz **opcję Samodzielne** w polu listy **Tryb wdrażania.**</span><span class="sxs-lookup"><span data-stu-id="57003-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="57003-246">W polu listy **Docelowy czas wykonywania** wybierz jedną z platform, na których docelowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="57003-247">Wybierz **pozycję Zapisz,** aby zaakceptować zmiany i zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="57003-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="57003-248">Nazwij swój profil.</span><span class="sxs-lookup"><span data-stu-id="57003-248">Name your profile.</span></span>

   1. <span data-ttu-id="57003-249">Wybierz opcję**Zmień nazwę profilu** **akcji,** > aby nadać nazwę profilowi.</span><span class="sxs-lookup"><span data-stu-id="57003-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="57003-250">Przypisz profil nazwę identyfikującą platformę docelową, a następnie wybierz \**Zapisz*.</span><span class="sxs-lookup"><span data-stu-id="57003-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="57003-251">Powtórz te kroki, aby zdefiniować wszelkie dodatkowe platformy docelowe, które są docelowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="57003-252">Skonfigurowano profile i możesz teraz opublikować aplikację.</span><span class="sxs-lookup"><span data-stu-id="57003-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="57003-253">W tym celu:</span><span class="sxs-lookup"><span data-stu-id="57003-253">To do this:</span></span>

   1. <span data-ttu-id="57003-254">Jeśli okno **Publikowania** nie jest aktualnie otwarte, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="57003-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="57003-255">Wybierz profil, który chcesz opublikować, a następnie wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="57003-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="57003-256">Zrób to dla każdego profilu, który ma zostać opublikowany.</span><span class="sxs-lookup"><span data-stu-id="57003-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="57003-257">Każda lokalizacja docelowa (w przypadku naszego przykładu bin\release\netcoreapp2.1\publish\\nazwa*profilu* zawiera kompletny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików .NET Core) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-257">Each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="57003-258">Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje debugowania o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="57003-259">Plik jest przydatny przede wszystkim do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="57003-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="57003-260">Można wybrać opcję niepakować go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="57003-261">Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="57003-262">Wdrażanie opublikowanych plików w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="57003-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="57003-263">Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru.</span><span class="sxs-lookup"><span data-stu-id="57003-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="57003-264">Poniżej znajduje się kompletny plik *csproj* dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="57003-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="57003-265">Ponadto program Visual Studio tworzy oddzielny\*profil publikowania ( pubxml) dla każdej platformy, która jest kierowana.</span><span class="sxs-lookup"><span data-stu-id="57003-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="57003-266">Na przykład plik dla naszego profilu linuksa (linux.pubxml) jest wyświetlany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="57003-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

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

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="57003-267">Samodzielne wdrażanie z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="57003-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="57003-268">Wdrażanie samodzielnego wdrożenia z co najmniej jedną zależnośćą innych firm wymaga dodania zależności.</span><span class="sxs-lookup"><span data-stu-id="57003-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="57003-269">Przed utworzeniem aplikacji wymagane są następujące dodatkowe kroki:</span><span class="sxs-lookup"><span data-stu-id="57003-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="57003-270">Użyj **Menedżera pakietów NuGet,** aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="57003-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="57003-271">Aby otworzyć Menedżera pakietów, wybierz pozycję **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span><span class="sxs-lookup"><span data-stu-id="57003-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="57003-272">Upewnij się, że zależności innych firm `Newtonsoft.Json`(na przykład) są zainstalowane w systemie, a jeśli nie, zainstaluj je.</span><span class="sxs-lookup"><span data-stu-id="57003-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="57003-273">Karta **Zainstalowana** zawiera listę pakietów NuGet zainstalowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="57003-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="57003-274">Jeśli `Newtonsoft.Json` nie ma tam na liście, wybierz kartę **Przeglądaj** i wpisz "Newtonsoft.Json" w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="57003-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="57003-275">Zaznacz `Newtonsoft.Json` i w prawym okienku wybierz projekt przed wybraniem opcji **Zainstaluj**.</span><span class="sxs-lookup"><span data-stu-id="57003-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="57003-276">Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku karty **Zarządzanie pakietami dla rozwiązania.**</span><span class="sxs-lookup"><span data-stu-id="57003-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="57003-277">Poniżej znajduje się kompletny plik *csproj* dla tego projektu:</span><span class="sxs-lookup"><span data-stu-id="57003-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="57003-278">Visual Studio 15.6 i starsze</span><span class="sxs-lookup"><span data-stu-id="57003-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

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

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="57003-279">Visual Studio 15.7 i nowsze</span><span class="sxs-lookup"><span data-stu-id="57003-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

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

<span data-ttu-id="57003-280">Podczas wdrażania aplikacji wszystkie zależności innych firm używane w aplikacji są również zawarte w plikach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57003-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="57003-281">Biblioteki innych firm nie są wymagane w systemie, w którym aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="57003-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="57003-282">Wdrożenie jest możliwe tylko z biblioteką innej firmy na platformach obsługiwanych przez tę bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="57003-282">You can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="57003-283">Jest to podobne do posiadania zależności innych firm z natywnymi zależnościami we wdrożeniu zależnym od struktury, gdzie natywne zależności nie będą istnieć na platformie docelowej, chyba że zostały tam wcześniej zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="57003-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="57003-284">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57003-284">See also</span></span>

- [<span data-ttu-id="57003-285">Wdrożenie aplikacji core .NET</span><span class="sxs-lookup"><span data-stu-id="57003-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="57003-286">Katalog identyfikatora IDentifier (RID) programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="57003-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
