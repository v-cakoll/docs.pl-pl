---
title: Instalowanie zlokalizowanych plików IntelliSense
description: Dowiedz się, jak skonfigurować komputer deweloperski do korzystania z zlokalizowanych plików IntelliSense dla projektów .NET Core w programie Visual Studio.
author: mairaw
ms.author: mairaw
ms.date: 12/18/2019
ms.openlocfilehash: 98d75544ab853e75c175dd2919991b250cfaa3b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443478"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="26457-103">Jak zainstalować zlokalizowane pliki IntelliSense dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="26457-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="26457-104">[IntelliSense](/visualstudio/ide/using-intellisense) to pomoc dla uzupełniania kodu, która jest dostępna w różnych zintegrowanych środowiskach programistycznych (środowisk IDE), takich jak program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26457-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="26457-105">Domyślnie podczas tworzenia projektów programu .NET Core zestaw SDK zawiera tylko angielską wersję plików IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="26457-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="26457-106">W tym artykule wyjaśniono:</span><span class="sxs-lookup"><span data-stu-id="26457-106">This article explains:</span></span>

- <span data-ttu-id="26457-107">Jak zainstalować zlokalizowaną wersję tych plików.</span><span class="sxs-lookup"><span data-stu-id="26457-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="26457-108">Jak zmodyfikować instalację programu Visual Studio tak, aby korzystała z innego języka.</span><span class="sxs-lookup"><span data-stu-id="26457-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26457-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="26457-109">Prerequisites</span></span>

- <span data-ttu-id="26457-110">[.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="26457-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="26457-111">[Program Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="26457-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="26457-112">Pobieranie i Instalowanie zlokalizowanych plików IntelliSense</span><span class="sxs-lookup"><span data-stu-id="26457-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26457-113">Ta procedura wymaga uprawnień administratora do kopiowania plików IntelliSense do folderu instalacji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="26457-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="26457-114">Przejdź do strony [pobieranie plików IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense) .</span><span class="sxs-lookup"><span data-stu-id="26457-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="26457-115">Pobierz plik IntelliSense dla języka i wersji, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="26457-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="26457-116">Wyodrębnij zawartość pliku zip.</span><span class="sxs-lookup"><span data-stu-id="26457-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="26457-117">Przejdź do folderu instalacji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="26457-117">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="26457-118">Domyślnie jest to w obszarze *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="26457-118">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>

   - <span data-ttu-id="26457-119">Wybierz zestaw SDK, dla którego chcesz zainstalować funkcję IntelliSense, i przejdź do skojarzonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="26457-119">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="26457-120">Do wyboru są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="26457-120">You have the following options:</span></span>

      | <span data-ttu-id="26457-121">Typ zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="26457-121">SDK type</span></span>        | <span data-ttu-id="26457-122">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="26457-122">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="26457-123">.NET Core</span><span class="sxs-lookup"><span data-stu-id="26457-123">.NET Core</span></span>       | <span data-ttu-id="26457-124">*Microsoft. servicecore. app. ref*</span><span class="sxs-lookup"><span data-stu-id="26457-124">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="26457-125">System Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="26457-125">Windows Desktop</span></span> | <span data-ttu-id="26457-126">*Microsoft. WindowsDesktop. app. ref*</span><span class="sxs-lookup"><span data-stu-id="26457-126">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="26457-127">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="26457-127">.NET Standard</span></span>   | <span data-ttu-id="26457-128">*Standard. Library. ref*</span><span class="sxs-lookup"><span data-stu-id="26457-128">*NETStandard.Library.Ref*</span></span>          |
   
   - <span data-ttu-id="26457-129">Przejdź do wersji, w której chcesz zainstalować zlokalizowaną funkcję IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="26457-129">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="26457-130">Na przykład *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="26457-130">For example, *3.1.0*.</span></span>
   - <span data-ttu-id="26457-131">Otwórz folder *ref* .</span><span class="sxs-lookup"><span data-stu-id="26457-131">Open the *ref* folder.</span></span>
   - <span data-ttu-id="26457-132">Otwórz folder moniker.</span><span class="sxs-lookup"><span data-stu-id="26457-132">Open the moniker folder.</span></span> <span data-ttu-id="26457-133">Na przykład *netcoreapp 3.1*.</span><span class="sxs-lookup"><span data-stu-id="26457-133">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="26457-134">Dlatego pełna ścieżka, która będzie wyglądała, wygląda podobnie do *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="26457-134">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="26457-135">Utwórz podfolder w folderze moniker, który właśnie został otwarty.</span><span class="sxs-lookup"><span data-stu-id="26457-135">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="26457-136">Nazwa folderu wskazuje język, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="26457-136">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="26457-137">W poniższej tabeli określono różne opcje:</span><span class="sxs-lookup"><span data-stu-id="26457-137">The following table specifies the different options:</span></span>

   | <span data-ttu-id="26457-138">Język</span><span class="sxs-lookup"><span data-stu-id="26457-138">Language</span></span>              | <span data-ttu-id="26457-139">Nazwa folderu</span><span class="sxs-lookup"><span data-stu-id="26457-139">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="26457-140">Portugalski (Brazylia)</span><span class="sxs-lookup"><span data-stu-id="26457-140">Brazilian Portuguese</span></span>  | <span data-ttu-id="26457-141">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="26457-141">*pt-br*</span></span>     |
   | <span data-ttu-id="26457-142">Chiński (uproszczony)</span><span class="sxs-lookup"><span data-stu-id="26457-142">Chinese (simplified)</span></span>  | <span data-ttu-id="26457-143">*zh-Hans*</span><span class="sxs-lookup"><span data-stu-id="26457-143">*zh-hans*</span></span>   |
   | <span data-ttu-id="26457-144">Chiński (tradycyjny)</span><span class="sxs-lookup"><span data-stu-id="26457-144">Chinese (traditional)</span></span> | <span data-ttu-id="26457-145">*zh-Hant*</span><span class="sxs-lookup"><span data-stu-id="26457-145">*zh-hant*</span></span>   |
   | <span data-ttu-id="26457-146">francuski</span><span class="sxs-lookup"><span data-stu-id="26457-146">French</span></span>                | <span data-ttu-id="26457-147">*fr*</span><span class="sxs-lookup"><span data-stu-id="26457-147">*fr*</span></span>        |
   | <span data-ttu-id="26457-148">niemiecki</span><span class="sxs-lookup"><span data-stu-id="26457-148">German</span></span>                | <span data-ttu-id="26457-149">*Ukryj*</span><span class="sxs-lookup"><span data-stu-id="26457-149">*de*</span></span>        |
   | <span data-ttu-id="26457-150">Włoski</span><span class="sxs-lookup"><span data-stu-id="26457-150">Italian</span></span>               | <span data-ttu-id="26457-151">*go*</span><span class="sxs-lookup"><span data-stu-id="26457-151">*it*</span></span>        |
   | <span data-ttu-id="26457-152">japoński</span><span class="sxs-lookup"><span data-stu-id="26457-152">Japanese</span></span>              | <span data-ttu-id="26457-153">*Japonia*</span><span class="sxs-lookup"><span data-stu-id="26457-153">*ja*</span></span>        |
   | <span data-ttu-id="26457-154">koreański</span><span class="sxs-lookup"><span data-stu-id="26457-154">Korean</span></span>                | <span data-ttu-id="26457-155">*Ko*</span><span class="sxs-lookup"><span data-stu-id="26457-155">*ko*</span></span>        |
   | <span data-ttu-id="26457-156">rosyjski</span><span class="sxs-lookup"><span data-stu-id="26457-156">Russian</span></span>               | <span data-ttu-id="26457-157">*ru*</span><span class="sxs-lookup"><span data-stu-id="26457-157">*ru*</span></span>        |
   | <span data-ttu-id="26457-158">Hiszpański</span><span class="sxs-lookup"><span data-stu-id="26457-158">Spanish</span></span>               | <span data-ttu-id="26457-159">*AK*</span><span class="sxs-lookup"><span data-stu-id="26457-159">*es*</span></span>        |

1. <span data-ttu-id="26457-160">Skopiuj pliki *. XML* wyodrębnione w kroku 3 do tego nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="26457-160">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="26457-161">Pliki *. XML* są podzielone na foldery zestawu SDK, dlatego skopiuj je do zgodnego zestawu SDK, który został wybrany w kroku 4.</span><span class="sxs-lookup"><span data-stu-id="26457-161">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="26457-162">Modyfikuj język programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26457-162">Modify Visual Studio language</span></span>

<span data-ttu-id="26457-163">Aby program Visual Studio używał innego języka dla technologii IntelliSense, zainstaluj odpowiedni pakiet językowy.</span><span class="sxs-lookup"><span data-stu-id="26457-163">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="26457-164">Można to zrobić [podczas instalacji](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) lub w późniejszym czasie, modyfikując instalację programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26457-164">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="26457-165">Jeśli masz już program Visual Studio skonfigurowany w wybranym języku, instalacja technologii IntelliSense jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="26457-165">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="26457-166">Instalowanie pakietu językowego</span><span class="sxs-lookup"><span data-stu-id="26457-166">Install the language pack</span></span>

<span data-ttu-id="26457-167">Jeśli podczas instalacji nie został zainstalowany odpowiedni pakiet językowy, zaktualizuj program Visual Studio w następujący sposób, aby zainstalować pakiet językowy:</span><span class="sxs-lookup"><span data-stu-id="26457-167">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26457-168">Aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio, musisz zalogować się przy użyciu konta z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="26457-168">To install, update, or modify Visual Studio, you must log on with an account that has administrative permissions.</span></span> <span data-ttu-id="26457-169">Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="26457-169">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="26457-170">Znajdowanie Instalatora programu Visual Studio na komputerze.</span><span class="sxs-lookup"><span data-stu-id="26457-170">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="26457-171">Na przykład na komputerze z systemem Windows 10, wybierz pozycję **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="26457-171">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Otwórz Instalator programu Visual Studio z systemu Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="26457-173">Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="26457-173">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="26457-174">Może być konieczne zaktualizowanie Instalatora przed kontynuowaniem.</span><span class="sxs-lookup"><span data-stu-id="26457-174">You might have to update the installer before continuing.</span></span> <span data-ttu-id="26457-175">Jeśli tak, postępuj zgodnie z monitami.</span><span class="sxs-lookup"><span data-stu-id="26457-175">If so, follow the prompts.</span></span>

1. <span data-ttu-id="26457-176">W instalatorze poszukaj wersji programu Visual Studio, do której chcesz dodać pakiet językowy, a następnie wybierz **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="26457-176">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Aktualizowanie lub modyfikowanie programu Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="26457-178">Jeśli nie widzisz przycisku **Modyfikuj** , ale zamiast tego zobaczysz **aktualizację** , musisz zaktualizować program Visual Studio przed zmodyfikowaniem instalacji.</span><span class="sxs-lookup"><span data-stu-id="26457-178">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="26457-179">Po zakończeniu aktualizacji powinien zostać wyświetlony przycisk **Modyfikuj** .</span><span class="sxs-lookup"><span data-stu-id="26457-179">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="26457-180">Na karcie **pakiety językowe** zaznacz lub odznacz Języki, które chcesz zainstalować lub odinstalować.</span><span class="sxs-lookup"><span data-stu-id="26457-180">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Karta pakiety językowe programu Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="26457-182">Wybierz **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="26457-182">Choose **Modify**.</span></span> <span data-ttu-id="26457-183">Rozpocznie się aktualizacja.</span><span class="sxs-lookup"><span data-stu-id="26457-183">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="26457-184">Modyfikowanie ustawień języka w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26457-184">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="26457-185">Po zainstalowaniu żądanych pakietów językowych zmodyfikuj ustawienia programu Visual Studio tak, aby korzystały z innego języka:</span><span class="sxs-lookup"><span data-stu-id="26457-185">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="26457-186">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26457-186">Open Visual Studio.</span></span>

1. <span data-ttu-id="26457-187">W oknie uruchamiania wybierz pozycję **Kontynuuj bez kodu**.</span><span class="sxs-lookup"><span data-stu-id="26457-187">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="26457-188">W menu głównym wybierz pozycję **narzędzia** > **Opcje**.</span><span class="sxs-lookup"><span data-stu-id="26457-188">On the main menu, select **Tools** > **Options**.</span></span> <span data-ttu-id="26457-189">Zostanie otwarte okno dialogowe Opcje.</span><span class="sxs-lookup"><span data-stu-id="26457-189">The Options dialog opens.</span></span>

1. <span data-ttu-id="26457-190">W obszarze folder **środowiska** wybierz pozycję **Ustawienia międzynarodowe**.</span><span class="sxs-lookup"><span data-stu-id="26457-190">Under the **Environment** folder, choose **International Settings**.</span></span>

1. <span data-ttu-id="26457-191">Z listy rozwijanej **Język** wybierz odpowiedni język.</span><span class="sxs-lookup"><span data-stu-id="26457-191">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="26457-192">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="26457-192">Choose **OK**.</span></span> 

1. <span data-ttu-id="26457-193">Zostanie wyświetlone okno dialogowe z informacją, że musisz ponownie uruchomić program Visual Studio, aby zmiany zaczęły obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="26457-193">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="26457-194">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="26457-194">Choose **OK**.</span></span>

1. <span data-ttu-id="26457-195">Uruchom ponownie program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26457-195">Restart Visual Studio.</span></span>

<span data-ttu-id="26457-196">Po wykonaniu tej czynności funkcja IntelliSense powinna działać zgodnie z oczekiwaniami w przypadku otwarcia projektu .NET Core, który jest przeznaczony dla wersji zainstalowanych plików IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="26457-196">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="26457-197">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26457-197">See also</span></span>

- [<span data-ttu-id="26457-198">Technologia IntelliSense w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26457-198">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
