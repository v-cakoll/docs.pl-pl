---
title: Publikowanie aplikacji .NET Core Hello World za pomocą programu Visual Studio
description: Publikowanie tworzy zestaw plików, które są potrzebne do uruchomienia aplikacji .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156637"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="759aa-103">Publikowanie aplikacji .NET Core Hello World za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="759aa-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="759aa-104">W [programie Tworzenie aplikacji Hello World z usługą .NET Core w programie Visual Studio](with-visual-studio.md)utworzono aplikację konsoli Hello World.</span><span class="sxs-lookup"><span data-stu-id="759aa-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="759aa-105">W [debugowania aplikacji Hello World za pomocą programu Visual Studio](debugging-with-visual-studio.md)przetestowano ją przy użyciu debugera Programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="759aa-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="759aa-106">Teraz, gdy masz pewność, że działa zgodnie z oczekiwaniami, możesz go opublikować, aby inni użytkownicy mogli go uruchomić.</span><span class="sxs-lookup"><span data-stu-id="759aa-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="759aa-107">Publikowanie tworzy zestaw plików, które są potrzebne do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="759aa-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="759aa-108">Aby wdrożyć pliki, skopiuj je na komputer docelowy.</span><span class="sxs-lookup"><span data-stu-id="759aa-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="759aa-109">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="759aa-109">Publish the app</span></span>

1. <span data-ttu-id="759aa-110">Upewnij się, że program Visual Studio jest tworzenie wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="759aa-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="759aa-111">W razie potrzeby zmień ustawienie konfiguracji kompilacji na pasku narzędzi z **Debug** na **Release**.</span><span class="sxs-lookup"><span data-stu-id="759aa-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Pasek narzędzi programu Visual Studio z wybraną kompilacją wersji](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="759aa-113">Kliknij prawym przyciskiem myszy projekt **HelloWorld** (nie rozwiązanie HelloWorld) i wybierz **polecenie Publikuj** z menu.</span><span class="sxs-lookup"><span data-stu-id="759aa-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="759aa-114">(Możesz również wybrać **opcję Publikuj HelloWorld** z głównego menu **Kompilacja).**</span><span class="sxs-lookup"><span data-stu-id="759aa-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Visual Studio Publikowanie menu kontekstowe](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="759aa-116">Na stronie **Wybierz obiekt docelowy publikowania** wybierz pozycję **Folder**, a następnie wybierz pozycję **Utwórz profil**.</span><span class="sxs-lookup"><span data-stu-id="759aa-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![Wybieranie obiektu docelowego publikowania w programie Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="759aa-118">Na stronie **Publikowanie** wybierz pozycję **Publikuj**.</span><span class="sxs-lookup"><span data-stu-id="759aa-118">On the **Publish** page, select **Publish**.</span></span>

   ![Okno Publikowania w programie Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="759aa-120">Sprawdzanie plików</span><span class="sxs-lookup"><span data-stu-id="759aa-120">Inspect the files</span></span>

<span data-ttu-id="759aa-121">Proces publikowania tworzy wdrożenie zależne od struktury, które jest typem wdrożenia, w którym opublikowana aplikacja jest uruchamiana na dowolnej platformie obsługiwanej przez program .NET Core z zainstalowanym w systemie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="759aa-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="759aa-122">Użytkownicy mogą uruchomić opublikowaną aplikację, klikając dwukrotnie plik wykonywalny lub wydając `dotnet HelloWorld.dll` polecenie z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="759aa-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="759aa-123">W poniższych krokach przyjrzysz się plikom utworzonym przez proces publikowania.</span><span class="sxs-lookup"><span data-stu-id="759aa-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="759aa-124">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="759aa-124">Open a command prompt.</span></span>

   <span data-ttu-id="759aa-125">Jednym ze sposobów otwarcia wiersza polecenia jest wprowadzenie **wiersza polecenia** (lub **skrótu cmd)** w polu wyszukiwania na pasku zadań systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="759aa-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="759aa-126">Wybierz aplikację **klasyczną Wiersz polecenia** lub naciśnij klawisz **Enter,** jeśli jest już zaznaczona w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="759aa-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="759aa-127">Przejdź do opublikowanej aplikacji w *katalogu bin\Release\netcoreapp3.1\publish* katalogu projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="759aa-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![Okno konsoli z wyświetlonymi opublikowanymi plikami](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="759aa-129">Jak pokazano na obrazie, opublikowane dane wyjściowe zawierają następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="759aa-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="759aa-130">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="759aa-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="759aa-131">Jest to plik zależności w czasie wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="759aa-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="759aa-132">Definiuje składniki .NET Core i biblioteki (w tym biblioteki łączy dynamicznych, która zawiera aplikację) potrzebne do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="759aa-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="759aa-133">Aby uzyskać więcej informacji, zobacz [Pliki konfiguracyjne czasu wykonywania](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="759aa-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="759aa-134">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="759aa-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="759aa-135">Jest to wersja [wdrożenia zależna od struktury](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="759aa-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="759aa-136">Aby wykonać tę bibliotekę `dotnet HelloWorld.dll` łączy dynamicznych, wprowadź w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="759aa-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="759aa-137">*HelloWorld.exe (HelloWorld.exe)*</span><span class="sxs-lookup"><span data-stu-id="759aa-137">*HelloWorld.exe*</span></span>

         <span data-ttu-id="759aa-138">Jest to [zależna od struktury wykonywalna](../deploying/deploy-with-cli.md#framework-dependent-executable) wersja aplikacji.</span><span class="sxs-lookup"><span data-stu-id="759aa-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="759aa-139">Aby go uruchomić, wprowadź `HelloWorld.exe` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="759aa-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="759aa-140">*HelloWorld.pdb* (opcjonalnie do wdrożenia)</span><span class="sxs-lookup"><span data-stu-id="759aa-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="759aa-141">Jest to plik symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="759aa-141">This is the debug symbols file.</span></span> <span data-ttu-id="759aa-142">Nie są wymagane do wdrożenia tego pliku wraz z aplikacją, chociaż należy zapisać go w przypadku, gdy trzeba debugować opublikowaną wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="759aa-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="759aa-143">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="759aa-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="759aa-144">Jest to plik konfiguracyjny aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="759aa-144">This is the application's run-time configuration file.</span></span> <span data-ttu-id="759aa-145">Identyfikuje wersję programu .NET Core, na którą została zbudowana aplikacja.</span><span class="sxs-lookup"><span data-stu-id="759aa-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="759aa-146">Można również dodać do niego opcje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="759aa-146">You can also add configuration options to it.</span></span> <span data-ttu-id="759aa-147">Aby uzyskać więcej informacji, zobacz [ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="759aa-147">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="759aa-148">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="759aa-148">Additional resources</span></span>

- [<span data-ttu-id="759aa-149">Wdrażanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="759aa-149">.NET Core application deployment</span></span>](../deploying/index.md)
