---
title: Publikowanie aplikacji konsolowej .NET Core przy użyciu Visual Studio Code
description: Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji .NET Core.
ms.date: 07/04/2020
ms.openlocfilehash: 8fd9975e8a88704b9dea45b40127c8dc03f7d09f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051886"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="f3c06-103">Samouczek: publikowanie aplikacji konsolowej .NET Core przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f3c06-103">Tutorial: Publish a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="f3c06-104">W tym samouczku pokazano, jak opublikować aplikację konsolową, tak aby inni użytkownicy mogli ją uruchomić.</span><span class="sxs-lookup"><span data-stu-id="f3c06-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="f3c06-105">Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3c06-105">Publishing creates the set of files that are needed to run an application.</span></span> <span data-ttu-id="f3c06-106">Aby wdrożyć pliki, skopiuj je na maszynę docelową.</span><span class="sxs-lookup"><span data-stu-id="f3c06-106">To deploy the files, copy them to the target machine.</span></span>

<span data-ttu-id="f3c06-107">Interfejs wiersza polecenia platformy .NET Core jest używany do publikowania aplikacji, więc możesz wykonać czynności opisane w tym samouczku z edytorem kodu innym niż Visual Studio Code, jeśli wolisz.</span><span class="sxs-lookup"><span data-stu-id="f3c06-107">The .NET Core CLI is used to publish the app, so you can follow this tutorial with a code editor other than Visual Studio Code if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f3c06-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f3c06-108">Prerequisites</span></span>

- <span data-ttu-id="f3c06-109">Ten samouczek współpracuje z aplikacją konsolową utworzoną w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="f3c06-109">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="f3c06-110">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="f3c06-110">Publish the app</span></span>

1. <span data-ttu-id="f3c06-111">Uruchom program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f3c06-111">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="f3c06-112">Otwórz folder projektu *HelloWorld* , który został utworzony w temacie [Tworzenie aplikacji konsolowej platformy .net Core w Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="f3c06-112">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="f3c06-113">Wybierz pozycję **Wyświetl**  >  **Terminal** z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="f3c06-113">Choose **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="f3c06-114">Terminal zostanie otwarty w folderze *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="f3c06-114">The terminal opens in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="f3c06-115">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f3c06-115">Run the following command:</span></span>

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   <span data-ttu-id="f3c06-116">Domyślną konfiguracją kompilacji jest *debugowanie*, dlatego to polecenie określa konfigurację kompilacji *wydania* .</span><span class="sxs-lookup"><span data-stu-id="f3c06-116">The default build configuration is *Debug*, so this command specifies the *Release* build configuration.</span></span> <span data-ttu-id="f3c06-117">Dane wyjściowe z konfiguracji kompilacji wydania zawierają minimalne informacje dotyczące debugowania symbolicznego i są w pełni zoptymalizowane.</span><span class="sxs-lookup"><span data-stu-id="f3c06-117">The output from the Release build configuration has minimal symbolic debug information and is fully optimized.</span></span>

   <span data-ttu-id="f3c06-118">Dane wyjściowe polecenia są podobne do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="f3c06-118">The command output is similar to the following example:</span></span>

   ```
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

   Determining projects to restore...
   All projects are up-to-date for restore.
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a><span data-ttu-id="f3c06-119">Inspekcja plików</span><span class="sxs-lookup"><span data-stu-id="f3c06-119">Inspect the files</span></span>

<span data-ttu-id="f3c06-120">Domyślnie proces publikowania tworzy wdrożenie zależne od platformy, które jest typem wdrożenia, w którym jest uruchomiona opublikowana aplikacja na komputerze z zainstalowanym środowiskiem uruchomieniowym .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f3c06-120">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="f3c06-121">Aby uruchomić opublikowaną aplikację, można użyć pliku wykonywalnego lub uruchomić `dotnet HelloWorld.dll` polecenie z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f3c06-121">To run the published app you can use the executable file or run the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="f3c06-122">W poniższych krokach zawarto Podgląd plików utworzonych przez proces publikowania.</span><span class="sxs-lookup"><span data-stu-id="f3c06-122">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="f3c06-123">Wybierz **Eksploratora** na lewym pasku nawigacyjnym.</span><span class="sxs-lookup"><span data-stu-id="f3c06-123">Select the **Explorer** in the left navigation bar.</span></span>

1. <span data-ttu-id="f3c06-124">Rozwiń gałąź *bin/Release/netcoreapp 3.1/Publish*.</span><span class="sxs-lookup"><span data-stu-id="f3c06-124">Expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Eksplorator przedstawiający opublikowane pliki":::

   <span data-ttu-id="f3c06-126">W miarę wyświetlania obrazu opublikowane dane wyjściowe zawierają następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="f3c06-126">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="f3c06-127">*HelloWorld.deps.jsna*</span><span class="sxs-lookup"><span data-stu-id="f3c06-127">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="f3c06-128">Jest to plik zależności środowiska uruchomieniowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3c06-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="f3c06-129">Definiuje składniki programu .NET Core i biblioteki (w tym bibliotekę dołączaną dynamicznie, która zawiera aplikację) potrzebną do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3c06-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="f3c06-130">Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="f3c06-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="f3c06-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="f3c06-131">*HelloWorld.dll*</span></span>

      <span data-ttu-id="f3c06-132">Jest to [zależna od platformy wersja wdrożenia](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3c06-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="f3c06-133">Aby wykonać tę bibliotekę dołączaną dynamicznie, wprowadź `dotnet HelloWorld.dll` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f3c06-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="f3c06-134">Ta metoda uruchamiania aplikacji działa na dowolnej platformie, na której zainstalowano środowisko uruchomieniowe platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f3c06-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="f3c06-135">*HelloWorld.exe* (*HelloWorld* w systemie Linux, nie utworzono w witrynie macOS).</span><span class="sxs-lookup"><span data-stu-id="f3c06-135">*HelloWorld.exe* (*HelloWorld* on Linux, not created on macOS.)</span></span>

      <span data-ttu-id="f3c06-136">Jest to [zależna od struktury wersja pliku wykonywalnego](../deploying/deploy-with-cli.md#framework-dependent-executable) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3c06-136">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="f3c06-137">Plik działa w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="f3c06-137">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="f3c06-138">*HelloWorld. pdb* (opcjonalnie dla wdrożenia)</span><span class="sxs-lookup"><span data-stu-id="f3c06-138">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="f3c06-139">Jest to plik symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="f3c06-139">This is the debug symbols file.</span></span> <span data-ttu-id="f3c06-140">Nie musisz wdrażać tego pliku wraz z aplikacją, chociaż należy je zapisać w zdarzeniu, które trzeba debugować opublikowaną wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3c06-140">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="f3c06-141">*HelloWorld.runtimeconfig.jsna*</span><span class="sxs-lookup"><span data-stu-id="f3c06-141">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="f3c06-142">To jest plik konfiguracji czasu wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3c06-142">This is the application's run-time configuration file.</span></span> <span data-ttu-id="f3c06-143">Identyfikuje wersję platformy .NET Core, w której aplikacja została skompilowana.</span><span class="sxs-lookup"><span data-stu-id="f3c06-143">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="f3c06-144">Możesz również dodać do niej opcje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f3c06-144">You can also add configuration options to it.</span></span> <span data-ttu-id="f3c06-145">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="f3c06-145">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="f3c06-146">Uruchom opublikowaną aplikację</span><span class="sxs-lookup"><span data-stu-id="f3c06-146">Run the published app</span></span>

1. <span data-ttu-id="f3c06-147">W **Eksploratorze**kliknij prawym przyciskiem myszy folder *Publikowanie* (<kbd>kliknij</kbd>pozycję macOS), a następnie wybierz pozycję **Otwórz w terminalu**.</span><span class="sxs-lookup"><span data-stu-id="f3c06-147">In **Explorer**, right-click the *publish* folder (<kbd>Ctrl</kbd>-click on macOS), and select **Open in Terminal**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Menu kontekstowe pokazujące otwarty w terminalu":::

1. <span data-ttu-id="f3c06-149">W systemie Windows lub Linux Uruchom aplikację przy użyciu pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="f3c06-149">On Windows or Linux, run the app by using the executable.</span></span>

   1. <span data-ttu-id="f3c06-150">W systemie Windows wpisz `.\HelloWorld.exe` i naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f3c06-150">On Windows, enter `.\HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="f3c06-151">W systemie Linux wpisz `./HelloWorld` i naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f3c06-151">On Linux, enter `./HelloWorld` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="f3c06-152">Wprowadź nazwę w odpowiedzi na monit, a następnie naciśnij dowolny klawisz, aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="f3c06-152">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="f3c06-153">Na dowolnej platformie Uruchom aplikację za pomocą [`dotnet`](../tools/dotnet.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="f3c06-153">On any platform, run the app by using the  [`dotnet`](../tools/dotnet.md) command:</span></span>

   1. <span data-ttu-id="f3c06-154">Wprowadź `dotnet HelloWorld.dll` i naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f3c06-154">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="f3c06-155">Wprowadź nazwę w odpowiedzi na monit, a następnie naciśnij dowolny klawisz, aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="f3c06-155">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f3c06-156">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="f3c06-156">Additional resources</span></span>

- [<span data-ttu-id="f3c06-157">Wdrażanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="f3c06-157">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="f3c06-158">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f3c06-158">Next steps</span></span>

<span data-ttu-id="f3c06-159">W tym samouczku opublikowano aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="f3c06-159">In this tutorial, you published a console app.</span></span> <span data-ttu-id="f3c06-160">W następnym samouczku utworzysz bibliotekę klas.</span><span class="sxs-lookup"><span data-stu-id="f3c06-160">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f3c06-161">Utwórz bibliotekę .NET Standard w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f3c06-161">Create a .NET Standard library in Visual Studio Code</span></span>](library-with-visual-studio-code.md)
