---
title: Publikowanie aplikacji Hello world .NET Core przy użyciu programu Visual Studio
description: Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: a82934fd2ea9568681a3bec82c3b15513decc926
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741569"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="41bf8-103">Publikowanie aplikacji Hello world .NET Core przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="41bf8-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="41bf8-104">W obszarze [Tworzenie aplikacji Hello World przy użyciu platformy .NET Core w programie Visual Studio](with-visual-studio.md)utworzono aplikację konsolową Hello World.</span><span class="sxs-lookup"><span data-stu-id="41bf8-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="41bf8-105">W [debugowaniu aplikacji Hello World za pomocą programu Visual Studio](debugging-with-visual-studio.md)przetestowano ją przy użyciu debugera programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41bf8-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="41bf8-106">Teraz, gdy masz pewność, że działa zgodnie z oczekiwaniami, możesz ją opublikować, tak aby inni użytkownicy mogli ją uruchamiać.</span><span class="sxs-lookup"><span data-stu-id="41bf8-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="41bf8-107">Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41bf8-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="41bf8-108">Aby wdrożyć pliki, skopiuj je na maszynę docelową.</span><span class="sxs-lookup"><span data-stu-id="41bf8-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="41bf8-109">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="41bf8-109">Publish the app</span></span>

1. <span data-ttu-id="41bf8-110">Upewnij się, że program Visual Studio kompiluje wydaną wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41bf8-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="41bf8-111">W razie potrzeby zmień ustawienie konfiguracji kompilacji na pasku narzędzi z **Debuguj** na **Release**.</span><span class="sxs-lookup"><span data-stu-id="41bf8-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Program Visual Studio Toolbar z wybraną kompilacją wydania](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="41bf8-113">Kliknij prawym przyciskiem myszy projekt **HelloWorld** (nie rozwiązanie HelloWorld) i wybierz polecenie **Publikuj** z menu.</span><span class="sxs-lookup"><span data-stu-id="41bf8-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="41bf8-114">(Możesz również wybrać opcję **Publikuj HelloWorld** z głównego menu **kompilacji** ).</span><span class="sxs-lookup"><span data-stu-id="41bf8-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Menu kontekstowe publikacji programu Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)
   
1. <span data-ttu-id="41bf8-116">Na stronie **Wybierz miejsce docelowe publikowania** wybierz pozycję **folder**, a następnie wybierz pozycję **Utwórz profil**.</span><span class="sxs-lookup"><span data-stu-id="41bf8-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![Wybieranie elementu docelowego publikowania w programie Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)
   
1. <span data-ttu-id="41bf8-118">Na stronie **Publikowanie** wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="41bf8-118">On the **Publish** page, select **Publish**.</span></span>

   ![Okno publikowania programu Visual Studio](media/publishing-with-visual-studio/publish-page.png)
   
## <a name="inspect-the-files"></a><span data-ttu-id="41bf8-120">Inspekcja plików</span><span class="sxs-lookup"><span data-stu-id="41bf8-120">Inspect the files</span></span>

<span data-ttu-id="41bf8-121">Proces publikowania tworzy wdrożenie zależne od platformy, które jest typem wdrożenia, w którym opublikowana aplikacja działa na dowolnej platformie obsługiwanej przez platformę .NET Core z zainstalowanym systemem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41bf8-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="41bf8-122">Użytkownicy mogą uruchamiać opublikowaną aplikację przez dwukrotne kliknięcie pliku wykonywalnego lub wydawanie `dotnet HelloWorld.dll` polecenia z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="41bf8-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="41bf8-123">W poniższych krokach zawarto Podgląd plików utworzonych przez proces publikowania.</span><span class="sxs-lookup"><span data-stu-id="41bf8-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="41bf8-124">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="41bf8-124">Open a command prompt.</span></span>

   <span data-ttu-id="41bf8-125">Jednym ze sposobów, aby otworzyć wiersz polecenia, jest wprowadzenie **wiersza polecenia** (lub **cmd** for Short) w polu wyszukiwania na pasku zadań systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="41bf8-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="41bf8-126">Wybierz pozycję **wiersz polecenia** aplikacja klasyczna lub naciśnij klawisz **Enter** , jeśli jest już zaznaczona w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="41bf8-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="41bf8-127">Przejdź do opublikowanej aplikacji w podkatalogu *bin\Release\netcoreapp3.1\publish* w katalogu projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41bf8-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![Okno konsoli przedstawiające pliki opublikowane](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="41bf8-129">W miarę wyświetlania obrazu opublikowane dane wyjściowe zawierają następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="41bf8-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="41bf8-130">*HelloWorld. deps. JSON*</span><span class="sxs-lookup"><span data-stu-id="41bf8-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="41bf8-131">Jest to plik zależności środowiska uruchomieniowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41bf8-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="41bf8-132">Definiuje składniki programu .NET Core i biblioteki (w tym bibliotekę dołączaną dynamicznie, która zawiera aplikację) potrzebną do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41bf8-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="41bf8-133">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="41bf8-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="41bf8-134">*HelloWorld. dll*</span><span class="sxs-lookup"><span data-stu-id="41bf8-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="41bf8-135">Jest to [zależna od platformy wersja wdrożenia](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41bf8-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="41bf8-136">Aby wykonać tę bibliotekę dołączaną dynamicznie, wprowadź `dotnet HelloWorld.dll` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="41bf8-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="41bf8-137">*HelloWorld. exe*</span><span class="sxs-lookup"><span data-stu-id="41bf8-137">*HelloWorld.exe*</span></span>
      
         <span data-ttu-id="41bf8-138">Jest to [zależna od struktury wersja pliku wykonywalnego](../deploying/deploy-with-cli.md#framework-dependent-executable) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41bf8-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="41bf8-139">Aby go uruchomić, wprowadź `HelloWorld.exe` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="41bf8-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="41bf8-140">*HelloWorld. pdb* (opcjonalnie dla wdrożenia)</span><span class="sxs-lookup"><span data-stu-id="41bf8-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="41bf8-141">Jest to plik symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="41bf8-141">This is the debug symbols file.</span></span> <span data-ttu-id="41bf8-142">Nie musisz wdrażać tego pliku wraz z aplikacją, chociaż należy je zapisać w zdarzeniu, które trzeba debugować opublikowaną wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41bf8-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="41bf8-143">*HelloWorld. runtimeconfig. JSON*</span><span class="sxs-lookup"><span data-stu-id="41bf8-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="41bf8-144">To jest plik konfiguracji czasu wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41bf8-144">This is the application's run-time configuration file.</span></span> <span data-ttu-id="41bf8-145">Identyfikuje wersję platformy .NET Core, w której aplikacja została skompilowana.</span><span class="sxs-lookup"><span data-stu-id="41bf8-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="41bf8-146">Możesz również dodać do niej opcje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="41bf8-146">You can also add configuration options to it.</span></span> <span data-ttu-id="41bf8-147">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="41bf8-147">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="41bf8-148">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="41bf8-148">Additional resources</span></span>

- [<span data-ttu-id="41bf8-149">Wdrażanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="41bf8-149">.NET Core application deployment</span></span>](../deploying/index.md)
