---
title: Publikowanie aplikacji konsolowej .NET Core przy użyciu programu Visual Studio
description: Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji .NET Core.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 44646a307d230db395b55b9dec5acfd168605940
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701287"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="d0016-103">Samouczek: publikowanie aplikacji konsolowej .NET Core przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d0016-103">Tutorial: Publish a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="d0016-104">W tym samouczku pokazano, jak opublikować aplikację konsolową, tak aby inni użytkownicy mogli ją uruchomić.</span><span class="sxs-lookup"><span data-stu-id="d0016-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="d0016-105">Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0016-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="d0016-106">Aby wdrożyć pliki, skopiuj je na maszynę docelową.</span><span class="sxs-lookup"><span data-stu-id="d0016-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d0016-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d0016-107">Prerequisites</span></span>

- <span data-ttu-id="d0016-108">Ten samouczek współpracuje z aplikacją konsolową utworzoną w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w programie Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d0016-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="d0016-109">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="d0016-109">Publish the app</span></span>

1. <span data-ttu-id="d0016-110">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0016-110">Start Visual Studio.</span></span>

1. <span data-ttu-id="d0016-111">Otwórz projekt *HelloWorld* , który został utworzony w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w programie Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d0016-111">Open the *HelloWorld* project that you created in [Create a .NET Core console application in Visual Studio](with-visual-studio.md).</span></span>

1. <span data-ttu-id="d0016-112">Upewnij się, że program Visual Studio używa konfiguracji kompilacji wydania.</span><span class="sxs-lookup"><span data-stu-id="d0016-112">Make sure that Visual Studio is using the Release build configuration.</span></span> <span data-ttu-id="d0016-113">W razie potrzeby zmień ustawienie konfiguracji kompilacji na pasku narzędzi z **Debuguj** na **Release**.</span><span class="sxs-lookup"><span data-stu-id="d0016-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Program Visual Studio Toolbar z wybraną kompilacją wydania](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="d0016-115">Kliknij prawym przyciskiem myszy projekt **HelloWorld** (nie rozwiązanie HelloWorld) i wybierz polecenie **Publikuj** z menu.</span><span class="sxs-lookup"><span data-stu-id="d0016-115">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Menu kontekstowe publikacji programu Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="d0016-117">Na karcie **Target** strony **Publikowanie** wybierz pozycję **folder**, a następnie wybierz pozycję **dalej**.</span><span class="sxs-lookup"><span data-stu-id="d0016-117">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![Wybieranie elementu docelowego publikowania w programie Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="d0016-119">Na karcie **Lokalizacja** strony **Publikowanie** wybierz pozycję **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="d0016-119">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Karta Lokalizacja strony publikacji programu Visual Studio](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="d0016-121">Na karcie **Publikowanie** okna **Publikowanie** wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="d0016-121">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Okno publikowania programu Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="d0016-123">Inspekcja plików</span><span class="sxs-lookup"><span data-stu-id="d0016-123">Inspect the files</span></span>

<span data-ttu-id="d0016-124">Domyślnie proces publikowania tworzy wdrożenie zależne od platformy, które jest typem wdrożenia, w którym jest uruchomiona opublikowana aplikacja na komputerze z zainstalowanym środowiskiem uruchomieniowym .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d0016-124">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="d0016-125">Użytkownicy mogą uruchamiać opublikowaną aplikację przez dwukrotne kliknięcie pliku wykonywalnego lub wydawanie `dotnet HelloWorld.dll` polecenia z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d0016-125">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="d0016-126">W poniższych krokach zawarto Podgląd plików utworzonych przez proces publikowania.</span><span class="sxs-lookup"><span data-stu-id="d0016-126">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="d0016-127">W **Eksplorator rozwiązań**wybierz opcję **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="d0016-127">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="d0016-128">W folderze projektu rozwiń węzeł *bin/Release/netcoreapp 3.1/Publish*.</span><span class="sxs-lookup"><span data-stu-id="d0016-128">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Eksplorator rozwiązań wyświetlania opublikowanych plików":::

   <span data-ttu-id="d0016-130">W miarę wyświetlania obrazu opublikowane dane wyjściowe zawierają następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="d0016-130">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="d0016-131">*HelloWorld.deps.jsna*</span><span class="sxs-lookup"><span data-stu-id="d0016-131">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="d0016-132">Jest to plik zależności środowiska uruchomieniowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0016-132">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="d0016-133">Definiuje składniki programu .NET Core i biblioteki (w tym bibliotekę dołączaną dynamicznie, która zawiera aplikację) potrzebną do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0016-133">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="d0016-134">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="d0016-134">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="d0016-135">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="d0016-135">*HelloWorld.dll*</span></span>

      <span data-ttu-id="d0016-136">Jest to [zależna od platformy wersja wdrożenia](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0016-136">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="d0016-137">Aby wykonać tę bibliotekę dołączaną dynamicznie, wprowadź `dotnet HelloWorld.dll` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d0016-137">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="d0016-138">Ta metoda uruchamiania aplikacji działa na dowolnej platformie, na której zainstalowano środowisko uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d0016-138">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="d0016-139">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="d0016-139">*HelloWorld.exe*</span></span>

      <span data-ttu-id="d0016-140">Jest to [zależna od struktury wersja pliku wykonywalnego](../deploying/deploy-with-cli.md#framework-dependent-executable) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0016-140">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="d0016-141">Aby uruchomić tę opcję, wprowadź `HelloWorld.exe` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d0016-141">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="d0016-142">Plik działa w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="d0016-142">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="d0016-143">*HelloWorld. pdb* (opcjonalnie dla wdrożenia)</span><span class="sxs-lookup"><span data-stu-id="d0016-143">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="d0016-144">Jest to plik symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="d0016-144">This is the debug symbols file.</span></span> <span data-ttu-id="d0016-145">Nie musisz wdrażać tego pliku wraz z aplikacją, chociaż należy je zapisać w zdarzeniu, które trzeba debugować opublikowaną wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0016-145">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="d0016-146">*HelloWorld.runtimeconfig.jsna*</span><span class="sxs-lookup"><span data-stu-id="d0016-146">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="d0016-147">To jest plik konfiguracji czasu wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0016-147">This is the application's run-time configuration file.</span></span> <span data-ttu-id="d0016-148">Identyfikuje wersję platformy .NET Core, w której aplikacja została skompilowana.</span><span class="sxs-lookup"><span data-stu-id="d0016-148">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="d0016-149">Możesz również dodać do niej opcje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d0016-149">You can also add configuration options to it.</span></span> <span data-ttu-id="d0016-150">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="d0016-150">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="d0016-151">Uruchom opublikowaną aplikację</span><span class="sxs-lookup"><span data-stu-id="d0016-151">Run the published app</span></span>

1. <span data-ttu-id="d0016-152">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder *Publikowanie* , a następnie wybierz polecenie **Kopiuj pełną ścieżkę**.</span><span class="sxs-lookup"><span data-stu-id="d0016-152">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="d0016-153">Otwórz wiersz polecenia i przejdź do folderu *Publikowanie* .</span><span class="sxs-lookup"><span data-stu-id="d0016-153">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="d0016-154">W tym celu wprowadź, `cd` a następnie wklej pełną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="d0016-154">To do that, enter `cd` and then paste the full path.</span></span> <span data-ttu-id="d0016-155">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d0016-155">For example:</span></span>

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="d0016-156">Uruchom aplikację przy użyciu pliku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="d0016-156">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="d0016-157">Wprowadź `HelloWorld.exe` i naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d0016-157">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="d0016-158">Wprowadź nazwę w odpowiedzi na monit, a następnie naciśnij dowolny klawisz, aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="d0016-158">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="d0016-159">Uruchom aplikację za pomocą `dotnet` polecenia:</span><span class="sxs-lookup"><span data-stu-id="d0016-159">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="d0016-160">Wprowadź `dotnet HelloWorld.dll` i naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d0016-160">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="d0016-161">Wprowadź nazwę w odpowiedzi na monit, a następnie naciśnij dowolny klawisz, aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="d0016-161">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d0016-162">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="d0016-162">Additional resources</span></span>

- [<span data-ttu-id="d0016-163">Wdrażanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="d0016-163">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="d0016-164">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d0016-164">Next steps</span></span>

<span data-ttu-id="d0016-165">W tym samouczku opublikowano aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="d0016-165">In this tutorial, you published a console app.</span></span> <span data-ttu-id="d0016-166">W następnym samouczku utworzysz bibliotekę klas.</span><span class="sxs-lookup"><span data-stu-id="d0016-166">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d0016-167">Tworzenie biblioteki .NET Standard w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d0016-167">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
