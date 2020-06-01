---
title: Publikowanie aplikacji Hello world .NET Core przy użyciu programu Visual Studio
description: Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 745fb2af332afa278c78ec9baeea7230fe725c02
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241500"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio"></a><span data-ttu-id="09e25-103">Samouczek: publikowanie aplikacji konsolowej .NET Core za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="09e25-103">Tutorial: Publish a .NET Core console application with Visual Studio</span></span>

<span data-ttu-id="09e25-104">W tym samouczku pokazano, jak opublikować aplikację konsolową, tak aby inni użytkownicy mogli ją uruchomić.</span><span class="sxs-lookup"><span data-stu-id="09e25-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="09e25-105">Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09e25-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="09e25-106">Aby wdrożyć pliki, skopiuj je na maszynę docelową.</span><span class="sxs-lookup"><span data-stu-id="09e25-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="09e25-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="09e25-107">Prerequisites</span></span>

- <span data-ttu-id="09e25-108">Ten samouczek współpracuje z aplikacją konsolową utworzoną w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w programie Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="09e25-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="09e25-109">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="09e25-109">Publish the app</span></span>

1. <span data-ttu-id="09e25-110">Upewnij się, że program Visual Studio kompiluje wydaną wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09e25-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="09e25-111">W razie potrzeby zmień ustawienie konfiguracji kompilacji na pasku narzędzi z **Debuguj** na **Release**.</span><span class="sxs-lookup"><span data-stu-id="09e25-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Program Visual Studio Toolbar z wybraną kompilacją wydania](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="09e25-113">Kliknij prawym przyciskiem myszy projekt **HelloWorld** (nie rozwiązanie HelloWorld) i wybierz polecenie **Publikuj** z menu.</span><span class="sxs-lookup"><span data-stu-id="09e25-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Menu kontekstowe publikacji programu Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="09e25-115">Na karcie **Target** strony **Publikowanie** wybierz pozycję **folder**, a następnie wybierz pozycję **dalej**.</span><span class="sxs-lookup"><span data-stu-id="09e25-115">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![Wybieranie elementu docelowego publikowania w programie Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="09e25-117">Na karcie **Lokalizacja** strony **Publikowanie** wybierz pozycję **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="09e25-117">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Karta Lokalizacja strony publikacji programu Visual Studio](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="09e25-119">Na karcie **Publikowanie** okna **Publikowanie** wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="09e25-119">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Okno publikowania programu Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="09e25-121">Inspekcja plików</span><span class="sxs-lookup"><span data-stu-id="09e25-121">Inspect the files</span></span>

<span data-ttu-id="09e25-122">Proces publikowania tworzy wdrożenie zależne od platformy, które jest typem wdrożenia, w którym jest uruchomiona opublikowana aplikacja na komputerze z zainstalowanym środowiskiem uruchomieniowym .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09e25-122">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="09e25-123">Użytkownicy mogą uruchamiać opublikowaną aplikację przez dwukrotne kliknięcie pliku wykonywalnego lub wydawanie `dotnet HelloWorld.dll` polecenia z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="09e25-123">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="09e25-124">W poniższych krokach zawarto Podgląd plików utworzonych przez proces publikowania.</span><span class="sxs-lookup"><span data-stu-id="09e25-124">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="09e25-125">W **Eksplorator rozwiązań**wybierz opcję **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="09e25-125">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="09e25-126">W folderze projektu rozwiń węzeł *bin/Release/netcoreapp 3.1/Publish*.</span><span class="sxs-lookup"><span data-stu-id="09e25-126">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Eksplorator rozwiązań wyświetlania opublikowanych plików":::

   <span data-ttu-id="09e25-128">W miarę wyświetlania obrazu opublikowane dane wyjściowe zawierają następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="09e25-128">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="09e25-129">*HelloWorld. deps. JSON*</span><span class="sxs-lookup"><span data-stu-id="09e25-129">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="09e25-130">Jest to plik zależności środowiska uruchomieniowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09e25-130">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="09e25-131">Definiuje składniki programu .NET Core i biblioteki (w tym bibliotekę dołączaną dynamicznie, która zawiera aplikację) potrzebną do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09e25-131">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="09e25-132">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="09e25-132">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="09e25-133">*HelloWorld. dll*</span><span class="sxs-lookup"><span data-stu-id="09e25-133">*HelloWorld.dll*</span></span>

      <span data-ttu-id="09e25-134">Jest to [zależna od platformy wersja wdrożenia](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09e25-134">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="09e25-135">Aby wykonać tę bibliotekę dołączaną dynamicznie, wprowadź `dotnet HelloWorld.dll` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="09e25-135">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="09e25-136">Ta metoda uruchamiania aplikacji działa na dowolnej platformie, na której zainstalowano środowisko uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09e25-136">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="09e25-137">*HelloWorld. exe*</span><span class="sxs-lookup"><span data-stu-id="09e25-137">*HelloWorld.exe*</span></span>

      <span data-ttu-id="09e25-138">Jest to [zależna od struktury wersja pliku wykonywalnego](../deploying/deploy-with-cli.md#framework-dependent-executable) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09e25-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="09e25-139">Aby uruchomić tę opcję, wprowadź `HelloWorld.exe` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="09e25-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="09e25-140">Plik działa w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="09e25-140">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="09e25-141">*HelloWorld. pdb* (opcjonalnie dla wdrożenia)</span><span class="sxs-lookup"><span data-stu-id="09e25-141">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="09e25-142">Jest to plik symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="09e25-142">This is the debug symbols file.</span></span> <span data-ttu-id="09e25-143">Nie musisz wdrażać tego pliku wraz z aplikacją, chociaż należy je zapisać w zdarzeniu, które trzeba debugować opublikowaną wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09e25-143">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="09e25-144">*HelloWorld. runtimeconfig. JSON*</span><span class="sxs-lookup"><span data-stu-id="09e25-144">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="09e25-145">To jest plik konfiguracji czasu wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09e25-145">This is the application's run-time configuration file.</span></span> <span data-ttu-id="09e25-146">Identyfikuje wersję platformy .NET Core, w której aplikacja została skompilowana.</span><span class="sxs-lookup"><span data-stu-id="09e25-146">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="09e25-147">Możesz również dodać do niej opcje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09e25-147">You can also add configuration options to it.</span></span> <span data-ttu-id="09e25-148">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="09e25-148">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="09e25-149">Uruchom opublikowaną aplikację</span><span class="sxs-lookup"><span data-stu-id="09e25-149">Run the published app</span></span>

1. <span data-ttu-id="09e25-150">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder *Publikowanie* , a następnie wybierz polecenie **Kopiuj pełną ścieżkę**.</span><span class="sxs-lookup"><span data-stu-id="09e25-150">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="09e25-151">Otwórz wiersz polecenia i przejdź do folderu *Publikowanie* .</span><span class="sxs-lookup"><span data-stu-id="09e25-151">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="09e25-152">Wprowadź `cd` i wklej pełną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="09e25-152">Enter `cd` and then paste the full path.</span></span> <span data-ttu-id="09e25-153">Przykład:</span><span class="sxs-lookup"><span data-stu-id="09e25-153">For example:</span></span>

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="09e25-154">Uruchom aplikację przy użyciu pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="09e25-154">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="09e25-155">Wprowadź `HelloWorld.exe` i naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="09e25-155">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="09e25-156">Wprowadź nazwę w odpowiedzi na monit, a następnie naciśnij dowolny klawisz, aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="09e25-156">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="09e25-157">Uruchom aplikację za pomocą `dotnet` polecenia:</span><span class="sxs-lookup"><span data-stu-id="09e25-157">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="09e25-158">Wprowadź `dotnet HelloWorld.dll` i naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="09e25-158">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="09e25-159">Wprowadź nazwę w odpowiedzi na monit, a następnie naciśnij dowolny klawisz, aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="09e25-159">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="09e25-160">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="09e25-160">Additional resources</span></span>

- [<span data-ttu-id="09e25-161">Wdrażanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="09e25-161">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="09e25-162">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="09e25-162">Next steps</span></span>

<span data-ttu-id="09e25-163">W tym samouczku opublikowano aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="09e25-163">In this tutorial, you published a console app.</span></span> <span data-ttu-id="09e25-164">W następnym samouczku utworzysz bibliotekę klas.</span><span class="sxs-lookup"><span data-stu-id="09e25-164">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="09e25-165">Tworzenie biblioteki .NET Standard w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="09e25-165">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
