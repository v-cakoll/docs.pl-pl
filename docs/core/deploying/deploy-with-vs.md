---
title: Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio
description: Dowiedz się, jak wdrożyć aplikację platformy .NET Core w programie Visual Studio.
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 4e8fbfa14c241c79f8708dfc2b288eeff2899891
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216237"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="cf691-103">Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cf691-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="cf691-104">Aplikację .NET Core można wdrożyć jako *wdrożenie zależne od platformy*, które obejmuje pliki binarne aplikacji, ale zależy od obecności platformy .NET Core w systemie docelowym lub jako *samodzielnego wdrożenia*, które obejmuje zarówno aplikacje i pliki binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cf691-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="cf691-105">Aby zapoznać się z omówieniem wdrażania aplikacji .NET Core, zobacz [wdrażanie aplikacji .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="cf691-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="cf691-106">W poniższych sekcjach pokazano, jak używać Microsoft Visual Studio do tworzenia następujących rodzajów wdrożeń:</span><span class="sxs-lookup"><span data-stu-id="cf691-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="cf691-107">Wdrożenie zależny od struktury</span><span class="sxs-lookup"><span data-stu-id="cf691-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="cf691-108">Wdrożenie zależne od platformy z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="cf691-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="cf691-109">Niezależne wdrożenia</span><span class="sxs-lookup"><span data-stu-id="cf691-109">Self-contained deployment</span></span>
- <span data-ttu-id="cf691-110">Samodzielne wdrożenie z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="cf691-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="cf691-111">Aby uzyskać informacje dotyczące korzystania z programu Visual Studio w celu tworzenia aplikacji platformy .NET Core, zobacz [wymagania wstępne dotyczące platformy .NET Core w systemie Windows](../windows-prerequisites.md#prerequisites-to-develop-net-core-apps-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="cf691-111">For information on using Visual Studio to develop .NET Core applications, see [Prerequisites for .NET Core on Windows](../windows-prerequisites.md#prerequisites-to-develop-net-core-apps-with-visual-studio).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="cf691-112">Wdrożenie zależny od struktury</span><span class="sxs-lookup"><span data-stu-id="cf691-112">Framework-dependent deployment</span></span>

<span data-ttu-id="cf691-113">Wdrażanie wdrożenia zależnego od platformy bez zależności innych firm polega jedynie na kompilowaniu, testowaniu i publikowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="cf691-114">Prosty przykład zapisaniem C# ilustruje proces.</span><span class="sxs-lookup"><span data-stu-id="cf691-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="cf691-115">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="cf691-115">Create the project.</span></span>

   <span data-ttu-id="cf691-116">Wybierz pozycję **plik** > **Nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="cf691-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="cf691-117">W oknie dialogowym **Nowy projekt** C# rozwiń kategorie projektu języka (lub Visual Basic) w okienku **zainstalowane** typy projektów, wybierz pozycję **.NET Core**, a następnie w środkowym okienku wybierz szablon **Aplikacja konsolowa (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="cf691-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="cf691-118">Wprowadź nazwę projektu, na przykład "FDD", w polu tekstowym **Nazwa** .</span><span class="sxs-lookup"><span data-stu-id="cf691-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="cf691-119">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf691-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="cf691-120">Dodaj kod źródłowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-120">Add the application's source code.</span></span>

   <span data-ttu-id="cf691-121">Otwórz plik *program.cs* lub *program. vb* w edytorze i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="cf691-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="cf691-122">Poprosi użytkownika o wprowadzenie tekstu i wyświetlenie pojedynczych słów wprowadzonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cf691-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="cf691-123">Używa wyrażenia `\w+` regularnego do rozdzielania słów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="cf691-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="cf691-124">Utwórz kompilację debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="cf691-125">Wybierz pozycję **kompilacja** > Kompiluj**rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="cf691-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="cf691-126">Możesz również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **Debuguj** > **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="cf691-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="cf691-127">Wdróż aplikację.</span><span class="sxs-lookup"><span data-stu-id="cf691-127">Deploy your app.</span></span>

   <span data-ttu-id="cf691-128">Po debugowaniu i przetestowaniu programu Utwórz pliki do wdrożenia przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="cf691-129">Aby opublikować z programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cf691-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="cf691-130">Zmień konfigurację rozwiązania z **Debuguj** na **Release** na pasku narzędzi, aby utworzyć wydanie (a nie debugowanie) wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="cf691-131">Kliknij prawym przyciskiem myszy projekt (a nie rozwiązanie) w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="cf691-132">Na karcie **Publikowanie** wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="cf691-133">Program Visual Studio zapisuje pliki wchodzące w skład aplikacji w lokalnym systemie plików.</span><span class="sxs-lookup"><span data-stu-id="cf691-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="cf691-134">Karta **Publikowanie** zawiera teraz pojedynczy profil, **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="cf691-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="cf691-135">Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** karty.</span><span class="sxs-lookup"><span data-stu-id="cf691-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="cf691-136">Pliki otrzymane są umieszczane w katalogu o nazwie `Publish` w systemie Windows `publish` i w systemach UNIX, które znajdują się w podkatalogu podkatalogu *.\bin\release\netcoreapp2.1* projektu.</span><span class="sxs-lookup"><span data-stu-id="cf691-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="cf691-137">Podobnie jak w przypadku plików aplikacji, proces publikowania emituje plik bazy danych programu (. pdb), który zawiera informacje o debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="cf691-138">Plik jest przydatny głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="cf691-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="cf691-139">Możesz zrezygnować z spakowania go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="cf691-140">Należy jednak zapisać ją w zdarzeniu, które chcesz debugować kompilację wydania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="cf691-141">Wdróż cały zestaw plików aplikacji w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="cf691-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="cf691-142">Na przykład możesz spakować je w pliku zip, użyć prostego `copy` polecenia lub wdrożyć je przy użyciu dowolnego wybranego pakietu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="cf691-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="cf691-143">Po zainstalowaniu użytkownicy mogą następnie wykonać swoją aplikację za pomocą `dotnet` polecenia i podać nazwę pliku aplikacji, `dotnet fdd.dll`na przykład.</span><span class="sxs-lookup"><span data-stu-id="cf691-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="cf691-144">Oprócz plików binarnych aplikacji Instalator powinien również powiązać Instalatora struktury udostępnionej lub sprawdzić go jako warunek wstępny w ramach instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="cf691-145">Instalacja struktury udostępnionej wymaga dostępu administratora/katalogu głównego, ponieważ jest to cały komputer.</span><span class="sxs-lookup"><span data-stu-id="cf691-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="cf691-146">Wdrożenie zależne od platformy z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="cf691-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="cf691-147">Wdrożenie wdrożenia zależnego od platformy z co najmniej jedną zależnością innej firmy wymaga, aby wszystkie zależności były dostępne dla projektu.</span><span class="sxs-lookup"><span data-stu-id="cf691-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="cf691-148">Aby można było skompilować aplikację, wymagane są następujące dodatkowe kroki:</span><span class="sxs-lookup"><span data-stu-id="cf691-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="cf691-149">Użyj **Menedżera pakietów NuGet** , aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="cf691-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="cf691-150">Aby otworzyć Menedżera pakietów, wybierz kolejno pozycje **Narzędzia** >  > **Menedżer pakietów NuGet**zarządzanie pakietami**NuGet dla rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="cf691-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="cf691-151">Upewnij się `Newtonsoft.Json` , że program jest zainstalowany w systemie i, jeśli nie, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="cf691-151">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="cf691-152">Karta **zainstalowane** zawiera listę pakietów NuGet zainstalowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="cf691-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="cf691-153">Jeśli `Newtonsoft.Json` nie ma go na liście, wybierz kartę **Przeglądaj** i w polu wyszukiwania wprowadź ciąg "Newtonsoft. JSON".</span><span class="sxs-lookup"><span data-stu-id="cf691-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="cf691-154">Wybierz `Newtonsoft.Json` i, w okienku po prawej stronie, wybierz swój projekt przed wybraniem opcji **Zainstaluj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="cf691-155">Jeśli `Newtonsoft.Json` program jest już zainstalowany w systemie, Dodaj go do projektu, wybierając projekt w prawym okienku na karcie **Zarządzaj pakietami dla rozwiązania** .</span><span class="sxs-lookup"><span data-stu-id="cf691-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="cf691-156">Należy zauważyć, że wdrożenie zależne od platformy z zależnościami innych firm jest przenośne tylko jako elementy zależne od innych firm.</span><span class="sxs-lookup"><span data-stu-id="cf691-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="cf691-157">Jeśli na przykład biblioteka innych firm obsługuje tylko macOS, aplikacja nie jest przenośna do systemów Windows.</span><span class="sxs-lookup"><span data-stu-id="cf691-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="cf691-158">Dzieje się tak, jeśli zależność innej firmy zależy od kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="cf691-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="cf691-159">Dobrym przykładem jest [serwer Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), który wymaga natywnej zależności od [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="cf691-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="cf691-160">Gdy FDD jest tworzona dla aplikacji z tym rodzajem zależności innych firm, opublikowane dane wyjściowe zawierają folder dla każdego [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) , który obsługuje zależność natywną (i która istnieje w pakiecie NuGet).</span><span class="sxs-lookup"><span data-stu-id="cf691-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a><span data-ttu-id="cf691-161">Samodzielne wdrażanie bez zależności innych firm</span><span class="sxs-lookup"><span data-stu-id="cf691-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="cf691-162">Wdrożenie samodzielnego wdrożenia bez zależności innych firm polega na tworzeniu projektu, modyfikowaniu pliku *csproj* , tworzeniu, testowaniu i publikowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="cf691-163">Prosty przykład zapisaniem C# ilustruje proces.</span><span class="sxs-lookup"><span data-stu-id="cf691-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="cf691-164">Zacznij od utworzenia, napisania i przetestowania projektu w taki sam sposób, jak w przypadku wdrożenia zależnego od platformy:</span><span class="sxs-lookup"><span data-stu-id="cf691-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="cf691-165">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="cf691-165">Create the project.</span></span>

   <span data-ttu-id="cf691-166">Wybierz pozycję **plik** > **Nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="cf691-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="cf691-167">W oknie dialogowym **Nowy projekt** C# rozwiń kategorie projektu języka (lub Visual Basic) w okienku **zainstalowane** typy projektów, wybierz pozycję **.NET Core**, a następnie w środkowym okienku wybierz szablon **Aplikacja konsolowa (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="cf691-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="cf691-168">Wprowadź nazwę projektu, na przykład "SCD", w polu tekstowym **Nazwa** , a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="cf691-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="cf691-169">Dodaj kod źródłowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-169">Add the application's source code.</span></span>

   <span data-ttu-id="cf691-170">Otwórz plik *program.cs* lub *program. vb* w edytorze i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="cf691-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="cf691-171">Poprosi użytkownika o wprowadzenie tekstu i wyświetlenie pojedynczych słów wprowadzonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cf691-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="cf691-172">Używa wyrażenia `\w+` regularnego do rozdzielania słów w tekście wejściowym.</span><span class="sxs-lookup"><span data-stu-id="cf691-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="cf691-173">Określ, czy chcesz używać trybu niezmiennej globalizacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="cf691-174">Szczególnie jeśli aplikacja jest przeznaczona dla systemu Linux, można zmniejszyć łączny rozmiar wdrożenia, wykorzystując [tryb niezmienny globalizacji](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="cf691-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="cf691-175">Tryb niezmiennej globalizacji jest przydatny w przypadku aplikacji, które nie są ogólnie obsługiwane i które mogą korzystać z Konwencji formatowania, konwencji dotyczących wielkości liter i porównywania ciągów oraz kolejności sortowania [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="cf691-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="cf691-176">Aby włączyć tryb niezmienny, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksplorator rozwiązań**i wybierz polecenie **Edytuj SCD. csproj** lub **Edytuj SCD. vbproj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="cf691-177">Następnie Dodaj następujące wyróżnione wiersze do pliku:</span><span class="sxs-lookup"><span data-stu-id="cf691-177">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="cf691-178">Utwórz kompilację debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="cf691-179">Wybierz pozycję **kompilacja** > Kompiluj**rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="cf691-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="cf691-180">Możesz również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **Debuguj** > **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="cf691-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="cf691-181">Ten krok debugowania pozwala identyfikować problemy z aplikacją, gdy jest ona uruchomiona na platformie hosta.</span><span class="sxs-lookup"><span data-stu-id="cf691-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="cf691-182">Nadal będzie konieczne przetestowanie go na każdej platformie docelowej.</span><span class="sxs-lookup"><span data-stu-id="cf691-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="cf691-183">Jeśli włączono tryb niezmienny globalizacji, należy sprawdzić, czy brak danych wrażliwych na kulturę jest odpowiednie dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="cf691-184">Po zakończeniu debugowania można opublikować własne wdrożenie:</span><span class="sxs-lookup"><span data-stu-id="cf691-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="cf691-185">Visual Studio 15,6 i starsze</span><span class="sxs-lookup"><span data-stu-id="cf691-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="cf691-186">Po debugowaniu i przetestowaniu programu Utwórz pliki, które mają zostać wdrożone wraz z aplikacją dla każdej platformy, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="cf691-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="cf691-187">Aby opublikować aplikację z poziomu programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cf691-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="cf691-188">Zdefiniuj platformy, dla których aplikacja będzie docelowa.</span><span class="sxs-lookup"><span data-stu-id="cf691-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="cf691-189">Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksplorator rozwiązań** i wybierz polecenie **Edytuj SCD. csproj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="cf691-190">Utwórz tag w sekcji pliku csproj, który definiuje platformy, do których odwołuje się aplikacja, i określ identyfikator czasu wykonywania (RID) dla każdej platformy docelowej. `<PropertyGroup>` `<RuntimeIdentifiers>`</span><span class="sxs-lookup"><span data-stu-id="cf691-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="cf691-191">Należy pamiętać, że należy również dodać średnik, aby oddzielić RID.</span><span class="sxs-lookup"><span data-stu-id="cf691-191">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="cf691-192">Listę identyfikatorów środowiska uruchomieniowego można znaleźć w [katalogu identyfikatorów środowiska uruchomieniowego](../rid-catalog.md) .</span><span class="sxs-lookup"><span data-stu-id="cf691-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="cf691-193">Na przykład poniższy przykład wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowy OS X Version 10,11 system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="cf691-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="cf691-194">Należy zauważyć, `<RuntimeIdentifiers>` że element może przejść do `<PropertyGroup>` dowolnego elementu, który znajduje się w pliku *csproj* .</span><span class="sxs-lookup"><span data-stu-id="cf691-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="cf691-195">Pełny przykładowy plik *csproj* pojawia się w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="cf691-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="cf691-196">Opublikuj aplikację.</span><span class="sxs-lookup"><span data-stu-id="cf691-196">Publish your app.</span></span>

   <span data-ttu-id="cf691-197">Po debugowaniu i przetestowaniu programu Utwórz pliki, które mają zostać wdrożone wraz z aplikacją dla każdej platformy, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="cf691-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="cf691-198">Aby opublikować aplikację z poziomu programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cf691-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="cf691-199">Zmień konfigurację rozwiązania z **Debuguj** na **Release** na pasku narzędzi, aby utworzyć wydanie (a nie debugowanie) wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="cf691-200">Kliknij prawym przyciskiem myszy projekt (a nie rozwiązanie) w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="cf691-201">Na karcie **Publikowanie** wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="cf691-202">Program Visual Studio zapisuje pliki wchodzące w skład aplikacji w lokalnym systemie plików.</span><span class="sxs-lookup"><span data-stu-id="cf691-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="cf691-203">Karta **Publikowanie** zawiera teraz pojedynczy profil, **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="cf691-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="cf691-204">Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** karty. **Docelowa wersja środowiska uruchomieniowego** określa, które środowisko uruchomieniowe zostało opublikowane, a **Lokalizacja docelowa** wskazuje miejsce zapisania plików dla wdrożenia samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="cf691-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="cf691-205">Program Visual Studio domyślnie zapisuje wszystkie pliki opublikowane w jednym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cf691-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="cf691-206">Dla wygody najlepiej utworzyć osobne profile dla każdego docelowego środowiska uruchomieniowego i umieścić pliki opublikowane w katalogu specyficznym dla platformy.</span><span class="sxs-lookup"><span data-stu-id="cf691-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="cf691-207">Obejmuje to utworzenie osobnego profilu publikowania dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="cf691-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="cf691-208">Teraz należy ponownie skompilować aplikację dla każdej platformy, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cf691-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="cf691-209">Wybierz pozycję **Utwórz nowy profil** w oknie dialogowym **publikowania** .</span><span class="sxs-lookup"><span data-stu-id="cf691-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="cf691-210">W oknie dialogowym **Wybieranie elementu docelowego publikowania** Zmień lokalizację **Wybieranie lokalizacji folderu** na *bin\Release\PublishOutput\win10-x64*.</span><span class="sxs-lookup"><span data-stu-id="cf691-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="cf691-211">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf691-211">Select **OK**.</span></span>

         1. <span data-ttu-id="cf691-212">Wybierz nowy profil (**FolderProfile1**) z listy profilów i upewnij się, że **docelowe środowisko uruchomieniowe** to `win10-x64`.</span><span class="sxs-lookup"><span data-stu-id="cf691-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="cf691-213">Jeśli nie, wybierz pozycję **Ustawienia**.</span><span class="sxs-lookup"><span data-stu-id="cf691-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="cf691-214">W oknie dialogowym **Ustawienia profilu** Zmień **docelowy środowisko uruchomieniowe** na `win10-x64` i wybierz pozycję **Zapisz**.</span><span class="sxs-lookup"><span data-stu-id="cf691-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="cf691-215">W przeciwnym razie wybierz pozycję **Anuluj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="cf691-216">Wybierz pozycję **Publikuj** , aby opublikować aplikację dla 64-bitowych platform Windows 10.</span><span class="sxs-lookup"><span data-stu-id="cf691-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="cf691-217">Wykonaj ponownie powyższe kroki, aby utworzyć profil dla `osx.10.11-x64` platformy.</span><span class="sxs-lookup"><span data-stu-id="cf691-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="cf691-218">**Lokalizacja docelowa** to *Bin\Release\PublishOutput\osx.10.11-x64*, a **docelowy środowisko uruchomieniowe** to `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="cf691-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="cf691-219">Nazwa, którą program Visual Studio przypisuje do tego profilu, to **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="cf691-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="cf691-220">Należy pamiętać, że każda lokalizacja docelowa zawiera pełny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików platformy .NET Core) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="cf691-221">Podobnie jak w przypadku plików aplikacji, proces publikowania emituje plik bazy danych programu (. pdb), który zawiera informacje o debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="cf691-222">Plik jest przydatny głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="cf691-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="cf691-223">Możesz zrezygnować z spakowania go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="cf691-224">Należy jednak zapisać ją w zdarzeniu, które chcesz debugować kompilację wydania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="cf691-225">Wdróż opublikowane pliki w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="cf691-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="cf691-226">Na przykład możesz spakować je w pliku zip, użyć prostego `copy` polecenia lub wdrożyć je przy użyciu dowolnego wybranego pakietu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="cf691-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="cf691-227">Poniżej znajduje się kompletny plik *csproj* dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="cf691-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="cf691-228">Program Visual Studio 15,7 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="cf691-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="cf691-229">Po debugowaniu i przetestowaniu programu Utwórz pliki, które mają zostać wdrożone wraz z aplikacją dla każdej platformy, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="cf691-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="cf691-230">Obejmuje to utworzenie osobnego profilu dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="cf691-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="cf691-231">Dla każdej platformy, która jest przeznaczona dla aplikacji, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cf691-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="cf691-232">Utwórz profil dla platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="cf691-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="cf691-233">Jeśli jest to pierwszy utworzony profil, kliknij prawym przyciskiem myszy projekt (a nie rozwiązanie) w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="cf691-234">Jeśli utworzono już profil, kliknij prawym przyciskiem myszy projekt, aby otworzyć okno dialogowe **publikowania** , jeśli nie jest jeszcze otwarte.</span><span class="sxs-lookup"><span data-stu-id="cf691-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="cf691-235">Następnie wybierz pozycję **Nowy profil**.</span><span class="sxs-lookup"><span data-stu-id="cf691-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="cf691-236">Zostanie otwarte okno dialogowe **Wybieranie elementu docelowego publikowania** .</span><span class="sxs-lookup"><span data-stu-id="cf691-236">The **Pick a Publish Target** dialog box opens.</span></span>
  
1. <span data-ttu-id="cf691-237">Wybierz lokalizację, w której program Visual Studio opublikuje aplikację.</span><span class="sxs-lookup"><span data-stu-id="cf691-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="cf691-238">W przypadku publikowania tylko na jednej platformie można zaakceptować wartość domyślną w polu tekstowym **Wybierz folder** . spowoduje to opublikowanie zależnego od platformy wdrożenia aplikacji w katalogu \*\<Project-Directory > \bin\Release\netcoreapp2.1\publish\* .</span><span class="sxs-lookup"><span data-stu-id="cf691-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the \*\<project-directory>\bin\Release\netcoreapp2.1\publish\* directory.</span></span>

   <span data-ttu-id="cf691-239">Jeśli publikujesz na więcej niż jednej platformie, dołącz ciąg, który identyfikuje platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="cf691-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="cf691-240">Na przykład jeśli dołączysz ciąg "Linux" do ścieżki pliku, program Visual Studio opublikuje zależne od platformy wdrożenie aplikacji do  *\<katalogu projektu > \bin\Release\netcoreapp2.1\publish\linux* .</span><span class="sxs-lookup"><span data-stu-id="cf691-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="cf691-241">Utwórz profil, wybierając ikonę listy rozwijanej obok przycisku **Publikuj** i wybierając pozycję **Utwórz profil**.</span><span class="sxs-lookup"><span data-stu-id="cf691-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="cf691-242">Następnie wybierz przycisk **Utwórz profil** , aby utworzyć profil.</span><span class="sxs-lookup"><span data-stu-id="cf691-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="cf691-243">Wskaż, że publikujesz wdrożenie samodzielne i zdefiniujesz platformę, w której aplikacja będzie docelowa.</span><span class="sxs-lookup"><span data-stu-id="cf691-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="cf691-244">W oknie dialogowym **Publikowanie** wybierz link **Konfiguruj** , aby otworzyć okno dialogowe **Ustawienia profilu** .</span><span class="sxs-lookup"><span data-stu-id="cf691-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="cf691-245">W polu listy **Tryb wdrożenia** wybierz pozycję **samodzielna** .</span><span class="sxs-lookup"><span data-stu-id="cf691-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="cf691-246">W polu listy **cel środowiska uruchomieniowego** wybierz jedną z platform, do której należy aplikacja.</span><span class="sxs-lookup"><span data-stu-id="cf691-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="cf691-247">Wybierz pozycję **Zapisz** , aby zaakceptować zmiany i zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="cf691-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="cf691-248">Nazwij swój profil.</span><span class="sxs-lookup"><span data-stu-id="cf691-248">Name your profile.</span></span>

   1. <span data-ttu-id="cf691-249">Wybierz **Akcje** > **Zmień nazwę profilu** , aby nawiązać nazwę profilu.</span><span class="sxs-lookup"><span data-stu-id="cf691-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="cf691-250">Przypisz do profilu nazwę identyfikującą platformę docelową, a następnie wybierz pozycję \**Zapisz*.</span><span class="sxs-lookup"><span data-stu-id="cf691-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="cf691-251">Powtórz te kroki, aby zdefiniować wszelkie dodatkowe Platformy docelowe, do których odwołuje się aplikacja.</span><span class="sxs-lookup"><span data-stu-id="cf691-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="cf691-252">Twoje profile zostały skonfigurowane i są teraz gotowe do opublikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="cf691-253">W tym celu:</span><span class="sxs-lookup"><span data-stu-id="cf691-253">To do this:</span></span>

   1. <span data-ttu-id="cf691-254">Jeśli okno **publikowania** nie jest aktualnie otwarte, kliknij prawym przyciskiem myszy projekt (a nie rozwiązanie) w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="cf691-255">Wybierz profil, który chcesz opublikować, a następnie wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="cf691-256">Zrób to dla każdego profilu do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="cf691-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="cf691-257">Należy pamiętać, że każda lokalizacja docelowa (w przypadku naszego przykładu bin\release\netcoreapp2.1\publish\\*profil-Name* zawiera kompletny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików platformy .NET Core) potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="cf691-258">Podobnie jak w przypadku plików aplikacji, proces publikowania emituje plik bazy danych programu (. pdb), który zawiera informacje o debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="cf691-259">Plik jest przydatny głównie do debugowania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="cf691-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="cf691-260">Możesz zrezygnować z spakowania go z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="cf691-261">Należy jednak zapisać ją w zdarzeniu, które chcesz debugować kompilację wydania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="cf691-262">Wdróż opublikowane pliki w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="cf691-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="cf691-263">Na przykład możesz spakować je w pliku zip, użyć prostego `copy` polecenia lub wdrożyć je przy użyciu dowolnego wybranego pakietu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="cf691-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="cf691-264">Poniżej znajduje się kompletny plik *csproj* dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="cf691-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="cf691-265">Ponadto program Visual Studio tworzy oddzielny profil publikacji (\*. pubxml) dla każdej platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="cf691-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="cf691-266">Na przykład plik z naszym profilem systemu Linux (Linux. pubxml) jest wyświetlany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cf691-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

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

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="cf691-267">Samodzielne wdrożenie z zależnościami innych firm</span><span class="sxs-lookup"><span data-stu-id="cf691-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="cf691-268">Wdrożenie samodzielnego wdrożenia z co najmniej jedną zależnością innych firm obejmuje dodanie zależności.</span><span class="sxs-lookup"><span data-stu-id="cf691-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="cf691-269">Aby można było skompilować aplikację, wymagane są następujące dodatkowe kroki:</span><span class="sxs-lookup"><span data-stu-id="cf691-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="cf691-270">Użyj **Menedżera pakietów NuGet** , aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="cf691-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="cf691-271">Aby otworzyć Menedżera pakietów, wybierz kolejno pozycje **Narzędzia** >  > **Menedżer pakietów NuGet**zarządzanie pakietami**NuGet dla rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="cf691-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="cf691-272">Upewnij się `Newtonsoft.Json` , że program jest zainstalowany w systemie i, jeśli nie, zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="cf691-272">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="cf691-273">Karta **zainstalowane** zawiera listę pakietów NuGet zainstalowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="cf691-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="cf691-274">Jeśli `Newtonsoft.Json` nie ma go na liście, wybierz kartę **Przeglądaj** i w polu wyszukiwania wprowadź ciąg "Newtonsoft. JSON".</span><span class="sxs-lookup"><span data-stu-id="cf691-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="cf691-275">Wybierz `Newtonsoft.Json` i, w okienku po prawej stronie, wybierz swój projekt przed wybraniem opcji **Zainstaluj**.</span><span class="sxs-lookup"><span data-stu-id="cf691-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="cf691-276">Jeśli `Newtonsoft.Json` program jest już zainstalowany w systemie, Dodaj go do projektu, wybierając projekt w prawym okienku na karcie **Zarządzaj pakietami dla rozwiązania** .</span><span class="sxs-lookup"><span data-stu-id="cf691-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="cf691-277">Poniżej znajduje się kompletny plik *csproj* dla tego projektu:</span><span class="sxs-lookup"><span data-stu-id="cf691-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="cf691-278">Visual Studio 15,6 i starsze</span><span class="sxs-lookup"><span data-stu-id="cf691-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

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

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="cf691-279">Program Visual Studio 15,7 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="cf691-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

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

<span data-ttu-id="cf691-280">Podczas wdrażania aplikacji wszystkie zależności innych firm używane w aplikacji również są zawarte w plikach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf691-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="cf691-281">Biblioteki innych firm nie są wymagane w systemie, w którym jest uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="cf691-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="cf691-282">Należy pamiętać, że wdrożenie z niezależnym programem można wdrożyć tylko z bibliotekami innych firm na platformach obsługiwanych przez tę bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="cf691-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="cf691-283">Jest to podobne do występowania zależności innych firm z natywnymi zależnościami w ramach wdrożenia zależnego od platformy, w przypadku których natywne zależności nie będą istniały na platformie docelowej, chyba że zostały wcześniej zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="cf691-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf691-284">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf691-284">See also</span></span>

- [<span data-ttu-id="cf691-285">Wdrażanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="cf691-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="cf691-286">Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="cf691-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
