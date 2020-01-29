---
title: Instalowanie zlokalizowanych plików IntelliSense
description: Dowiedz się, jak skonfigurować komputer deweloperski do korzystania z zlokalizowanych plików IntelliSense dla projektów .NET Core w programie Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: 58b462507edf953a6c28aadbb9e3239a5cbe05b2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733647"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="2a1b5-103">Jak zainstalować zlokalizowane pliki IntelliSense dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="2a1b5-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="2a1b5-104">[IntelliSense](/visualstudio/ide/using-intellisense) to pomoc dla uzupełniania kodu, która jest dostępna w różnych zintegrowanych środowiskach programistycznych (środowisk IDE), takich jak program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="2a1b5-105">Domyślnie podczas tworzenia projektów programu .NET Core zestaw SDK zawiera tylko angielską wersję plików IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="2a1b5-106">W tym artykule wyjaśniono:</span><span class="sxs-lookup"><span data-stu-id="2a1b5-106">This article explains:</span></span>

- <span data-ttu-id="2a1b5-107">Jak zainstalować zlokalizowaną wersję tych plików.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="2a1b5-108">Jak zmodyfikować instalację programu Visual Studio tak, aby korzystała z innego języka.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2a1b5-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2a1b5-109">Prerequisites</span></span>

- <span data-ttu-id="2a1b5-110">[.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="2a1b5-111">[Program Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="2a1b5-112">Pobieranie i Instalowanie zlokalizowanych plików IntelliSense</span><span class="sxs-lookup"><span data-stu-id="2a1b5-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a1b5-113">Ta procedura wymaga uprawnień administratora do kopiowania plików IntelliSense do folderu instalacji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="2a1b5-114">Przejdź do strony [pobieranie plików IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense) .</span><span class="sxs-lookup"><span data-stu-id="2a1b5-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="2a1b5-115">Pobierz plik IntelliSense dla języka i wersji, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="2a1b5-116">Wyodrębnij zawartość pliku zip.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="2a1b5-117">Przejdź do folderu IntelliSense platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="2a1b5-118">Przejdź do folderu instalacji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="2a1b5-119">Domyślnie jest to w obszarze *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="2a1b5-120">Wybierz zestaw SDK, dla którego chcesz zainstalować funkcję IntelliSense, i przejdź do skojarzonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="2a1b5-121">Do wyboru są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="2a1b5-121">You have the following options:</span></span>

      | <span data-ttu-id="2a1b5-122">Typ zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="2a1b5-122">SDK type</span></span>        | <span data-ttu-id="2a1b5-123">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="2a1b5-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="2a1b5-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2a1b5-124">.NET Core</span></span>       | <span data-ttu-id="2a1b5-125">*Microsoft. servicecore. app. ref*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="2a1b5-126">System Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="2a1b5-126">Windows Desktop</span></span> | <span data-ttu-id="2a1b5-127">*Microsoft. WindowsDesktop. app. ref*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="2a1b5-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="2a1b5-128">.NET Standard</span></span>   | <span data-ttu-id="2a1b5-129">*Standard. Library. ref*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-129">*NETStandard.Library.Ref*</span></span>          |
   
   1. <span data-ttu-id="2a1b5-130">Przejdź do wersji, w której chcesz zainstalować zlokalizowaną funkcję IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="2a1b5-131">Na przykład *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="2a1b5-132">Otwórz folder *ref* .</span><span class="sxs-lookup"><span data-stu-id="2a1b5-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="2a1b5-133">Otwórz folder moniker.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-133">Open the moniker folder.</span></span> <span data-ttu-id="2a1b5-134">Na przykład *netcoreapp 3.1*.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="2a1b5-135">Dlatego pełna ścieżka, która będzie wyglądała, wygląda podobnie do *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="2a1b5-136">Utwórz podfolder w folderze moniker, który właśnie został otwarty.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="2a1b5-137">Nazwa folderu wskazuje język, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="2a1b5-138">W poniższej tabeli określono różne opcje:</span><span class="sxs-lookup"><span data-stu-id="2a1b5-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="2a1b5-139">Język</span><span class="sxs-lookup"><span data-stu-id="2a1b5-139">Language</span></span>              | <span data-ttu-id="2a1b5-140">Nazwa folderu</span><span class="sxs-lookup"><span data-stu-id="2a1b5-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="2a1b5-141">Portugalski (Brazylia)</span><span class="sxs-lookup"><span data-stu-id="2a1b5-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="2a1b5-142">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-142">*pt-br*</span></span>     |
   | <span data-ttu-id="2a1b5-143">Chiński (uproszczony)</span><span class="sxs-lookup"><span data-stu-id="2a1b5-143">Chinese (simplified)</span></span>  | <span data-ttu-id="2a1b5-144">*zh-Hans*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="2a1b5-145">Chiński (tradycyjny)</span><span class="sxs-lookup"><span data-stu-id="2a1b5-145">Chinese (traditional)</span></span> | <span data-ttu-id="2a1b5-146">*zh-Hant*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="2a1b5-147">francuski</span><span class="sxs-lookup"><span data-stu-id="2a1b5-147">French</span></span>                | <span data-ttu-id="2a1b5-148">*fr*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-148">*fr*</span></span>        |
   | <span data-ttu-id="2a1b5-149">niemiecki</span><span class="sxs-lookup"><span data-stu-id="2a1b5-149">German</span></span>                | <span data-ttu-id="2a1b5-150">*Ukryj*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-150">*de*</span></span>        |
   | <span data-ttu-id="2a1b5-151">Włoski</span><span class="sxs-lookup"><span data-stu-id="2a1b5-151">Italian</span></span>               | <span data-ttu-id="2a1b5-152">*go*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-152">*it*</span></span>        |
   | <span data-ttu-id="2a1b5-153">japoński</span><span class="sxs-lookup"><span data-stu-id="2a1b5-153">Japanese</span></span>              | <span data-ttu-id="2a1b5-154">*Japonia*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-154">*ja*</span></span>        |
   | <span data-ttu-id="2a1b5-155">koreański</span><span class="sxs-lookup"><span data-stu-id="2a1b5-155">Korean</span></span>                | <span data-ttu-id="2a1b5-156">*Ko*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-156">*ko*</span></span>        |
   | <span data-ttu-id="2a1b5-157">rosyjski</span><span class="sxs-lookup"><span data-stu-id="2a1b5-157">Russian</span></span>               | <span data-ttu-id="2a1b5-158">*ru*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-158">*ru*</span></span>        |
   | <span data-ttu-id="2a1b5-159">Hiszpański</span><span class="sxs-lookup"><span data-stu-id="2a1b5-159">Spanish</span></span>               | <span data-ttu-id="2a1b5-160">*AK*</span><span class="sxs-lookup"><span data-stu-id="2a1b5-160">*es*</span></span>        |

1. <span data-ttu-id="2a1b5-161">Skopiuj pliki *. XML* wyodrębnione w kroku 3 do tego nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="2a1b5-162">Pliki *. XML* są podzielone na foldery zestawu SDK, dlatego skopiuj je do zgodnego zestawu SDK, który został wybrany w kroku 4.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="2a1b5-163">Modyfikuj język programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2a1b5-163">Modify Visual Studio language</span></span>

<span data-ttu-id="2a1b5-164">Aby program Visual Studio używał innego języka dla technologii IntelliSense, zainstaluj odpowiedni pakiet językowy.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="2a1b5-165">Można to zrobić [podczas instalacji](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) lub w późniejszym czasie, modyfikując instalację programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="2a1b5-166">Jeśli masz już program Visual Studio skonfigurowany w wybranym języku, instalacja technologii IntelliSense jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="2a1b5-167">Instalowanie pakietu językowego</span><span class="sxs-lookup"><span data-stu-id="2a1b5-167">Install the language pack</span></span>

<span data-ttu-id="2a1b5-168">Jeśli podczas instalacji nie został zainstalowany odpowiedni pakiet językowy, zaktualizuj program Visual Studio w następujący sposób, aby zainstalować pakiet językowy:</span><span class="sxs-lookup"><span data-stu-id="2a1b5-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a1b5-169">Aby zainstalować, zaktualizować lub zmodyfikować program Visual Studio, należy zalogować się przy użyciu konta z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="2a1b5-170">Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="2a1b5-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="2a1b5-171">Znajdowanie Instalatora programu Visual Studio na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="2a1b5-172">Na przykład na komputerze z systemem Windows 10, wybierz pozycję **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Otwórz Instalator programu Visual Studio z systemu Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="2a1b5-174">Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="2a1b5-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="2a1b5-175">Może być konieczne zaktualizowanie Instalatora przed kontynuowaniem.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="2a1b5-176">Jeśli tak, postępuj zgodnie z monitami.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="2a1b5-177">W instalatorze poszukaj wersji programu Visual Studio, do której chcesz dodać pakiet językowy, a następnie wybierz **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Aktualizowanie lub modyfikowanie programu Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="2a1b5-179">Jeśli nie widzisz przycisku **Modyfikuj** , ale zamiast tego zobaczysz **aktualizację** , musisz zaktualizować program Visual Studio przed zmodyfikowaniem instalacji.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="2a1b5-180">Po zakończeniu aktualizacji powinien zostać wyświetlony przycisk **Modyfikuj** .</span><span class="sxs-lookup"><span data-stu-id="2a1b5-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="2a1b5-181">Na karcie **pakiety językowe** zaznacz lub odznacz Języki, które chcesz zainstalować lub odinstalować.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Karta pakiety językowe programu Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="2a1b5-183">Wybierz **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-183">Choose **Modify**.</span></span> <span data-ttu-id="2a1b5-184">Rozpocznie się aktualizacja.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="2a1b5-185">Modyfikowanie ustawień języka w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2a1b5-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="2a1b5-186">Po zainstalowaniu żądanych pakietów językowych zmodyfikuj ustawienia programu Visual Studio tak, aby korzystały z innego języka:</span><span class="sxs-lookup"><span data-stu-id="2a1b5-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="2a1b5-187">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="2a1b5-188">W oknie uruchamiania wybierz pozycję **Kontynuuj bez kodu**.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="2a1b5-189">Na pasku menu wybierz pozycję **narzędzia** > **Opcje**.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="2a1b5-190">Zostanie otwarte okno dialogowe Opcje.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="2a1b5-191">W węźle **środowisko** wybierz pozycję **Ustawienia międzynarodowe**.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="2a1b5-192">Z listy rozwijanej **Język** wybierz odpowiedni język.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="2a1b5-193">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-193">Choose **OK**.</span></span> 

1. <span data-ttu-id="2a1b5-194">Zostanie wyświetlone okno dialogowe z informacją, że musisz ponownie uruchomić program Visual Studio, aby zmiany zaczęły obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="2a1b5-195">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-195">Choose **OK**.</span></span>

1. <span data-ttu-id="2a1b5-196">Uruchom ponownie program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-196">Restart Visual Studio.</span></span>

<span data-ttu-id="2a1b5-197">Po wykonaniu tej czynności funkcja IntelliSense powinna działać zgodnie z oczekiwaniami w przypadku otwarcia projektu .NET Core, który jest przeznaczony dla wersji zainstalowanych plików IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2a1b5-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a1b5-198">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a1b5-198">See also</span></span>

- [<span data-ttu-id="2a1b5-199">Technologia IntelliSense w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2a1b5-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
