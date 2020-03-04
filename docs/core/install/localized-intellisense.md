---
title: Instalowanie zlokalizowanych plików IntelliSense
description: Dowiedz się, jak skonfigurować komputer deweloperski do korzystania z zlokalizowanych plików IntelliSense dla projektów .NET Core w programie Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157716"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="32751-103">Jak zainstalować zlokalizowane pliki IntelliSense dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="32751-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="32751-104">[IntelliSense](/visualstudio/ide/using-intellisense) to pomoc dla uzupełniania kodu, która jest dostępna w różnych zintegrowanych środowiskach programistycznych (środowisk IDE), takich jak program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32751-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="32751-105">Domyślnie podczas tworzenia projektów programu .NET Core zestaw SDK zawiera tylko angielską wersję plików IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="32751-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="32751-106">W tym artykule wyjaśniono:</span><span class="sxs-lookup"><span data-stu-id="32751-106">This article explains:</span></span>

- <span data-ttu-id="32751-107">Jak zainstalować zlokalizowaną wersję tych plików.</span><span class="sxs-lookup"><span data-stu-id="32751-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="32751-108">Jak zmodyfikować instalację programu Visual Studio tak, aby korzystała z innego języka.</span><span class="sxs-lookup"><span data-stu-id="32751-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="32751-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="32751-109">Prerequisites</span></span>

- <span data-ttu-id="32751-110">[.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="32751-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="32751-111">[Program Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="32751-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="32751-112">Pobieranie i Instalowanie zlokalizowanych plików IntelliSense</span><span class="sxs-lookup"><span data-stu-id="32751-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32751-113">Ta procedura wymaga uprawnień administratora do kopiowania plików IntelliSense do folderu instalacji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="32751-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="32751-114">Przejdź do strony [pobieranie plików IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense) .</span><span class="sxs-lookup"><span data-stu-id="32751-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="32751-115">Pobierz plik IntelliSense dla języka i wersji, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="32751-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="32751-116">Wyodrębnij zawartość pliku zip.</span><span class="sxs-lookup"><span data-stu-id="32751-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="32751-117">Przejdź do folderu IntelliSense platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="32751-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="32751-118">Przejdź do folderu instalacji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="32751-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="32751-119">Domyślnie jest to w obszarze *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="32751-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="32751-120">Wybierz zestaw SDK, dla którego chcesz zainstalować funkcję IntelliSense, i przejdź do skojarzonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="32751-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="32751-121">Istnieją następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="32751-121">You have the following options:</span></span>

      | <span data-ttu-id="32751-122">Typ zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="32751-122">SDK type</span></span>        | <span data-ttu-id="32751-123">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="32751-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="32751-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="32751-124">.NET Core</span></span>       | <span data-ttu-id="32751-125">*Microsoft. servicecore. app. ref*</span><span class="sxs-lookup"><span data-stu-id="32751-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="32751-126">Pulpit systemu Windows</span><span class="sxs-lookup"><span data-stu-id="32751-126">Windows Desktop</span></span> | <span data-ttu-id="32751-127">*Microsoft. WindowsDesktop. app. ref*</span><span class="sxs-lookup"><span data-stu-id="32751-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="32751-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="32751-128">.NET Standard</span></span>   | <span data-ttu-id="32751-129">*Standard. Library. ref*</span><span class="sxs-lookup"><span data-stu-id="32751-129">*NETStandard.Library.Ref*</span></span>          |

   1. <span data-ttu-id="32751-130">Przejdź do wersji, w której chcesz zainstalować zlokalizowaną funkcję IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="32751-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="32751-131">Na przykład *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="32751-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="32751-132">Otwórz folder *ref* .</span><span class="sxs-lookup"><span data-stu-id="32751-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="32751-133">Otwórz folder moniker.</span><span class="sxs-lookup"><span data-stu-id="32751-133">Open the moniker folder.</span></span> <span data-ttu-id="32751-134">Na przykład *netcoreapp 3.1*.</span><span class="sxs-lookup"><span data-stu-id="32751-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="32751-135">Dlatego pełna ścieżka, która będzie wyglądała, wygląda podobnie do *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="32751-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="32751-136">Utwórz podfolder w folderze moniker, który właśnie został otwarty.</span><span class="sxs-lookup"><span data-stu-id="32751-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="32751-137">Nazwa folderu wskazuje język, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="32751-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="32751-138">W poniższej tabeli określono różne opcje:</span><span class="sxs-lookup"><span data-stu-id="32751-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="32751-139">Język</span><span class="sxs-lookup"><span data-stu-id="32751-139">Language</span></span>              | <span data-ttu-id="32751-140">Nazwa folderu</span><span class="sxs-lookup"><span data-stu-id="32751-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="32751-141">Portugalski (Brazylia)</span><span class="sxs-lookup"><span data-stu-id="32751-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="32751-142">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="32751-142">*pt-br*</span></span>     |
   | <span data-ttu-id="32751-143">Chiński (uproszczony)</span><span class="sxs-lookup"><span data-stu-id="32751-143">Chinese (simplified)</span></span>  | <span data-ttu-id="32751-144">*zh-Hans*</span><span class="sxs-lookup"><span data-stu-id="32751-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="32751-145">Chiński (tradycyjny)</span><span class="sxs-lookup"><span data-stu-id="32751-145">Chinese (traditional)</span></span> | <span data-ttu-id="32751-146">*zh-Hant*</span><span class="sxs-lookup"><span data-stu-id="32751-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="32751-147">Francuski</span><span class="sxs-lookup"><span data-stu-id="32751-147">French</span></span>                | <span data-ttu-id="32751-148">*fr*</span><span class="sxs-lookup"><span data-stu-id="32751-148">*fr*</span></span>        |
   | <span data-ttu-id="32751-149">Niemiecki</span><span class="sxs-lookup"><span data-stu-id="32751-149">German</span></span>                | <span data-ttu-id="32751-150">*Ukryj*</span><span class="sxs-lookup"><span data-stu-id="32751-150">*de*</span></span>        |
   | <span data-ttu-id="32751-151">Włoski</span><span class="sxs-lookup"><span data-stu-id="32751-151">Italian</span></span>               | <span data-ttu-id="32751-152">*go*</span><span class="sxs-lookup"><span data-stu-id="32751-152">*it*</span></span>        |
   | <span data-ttu-id="32751-153">Japoński</span><span class="sxs-lookup"><span data-stu-id="32751-153">Japanese</span></span>              | <span data-ttu-id="32751-154">*Japonia*</span><span class="sxs-lookup"><span data-stu-id="32751-154">*ja*</span></span>        |
   | <span data-ttu-id="32751-155">Koreański</span><span class="sxs-lookup"><span data-stu-id="32751-155">Korean</span></span>                | <span data-ttu-id="32751-156">*Ko*</span><span class="sxs-lookup"><span data-stu-id="32751-156">*ko*</span></span>        |
   | <span data-ttu-id="32751-157">Rosyjski</span><span class="sxs-lookup"><span data-stu-id="32751-157">Russian</span></span>               | <span data-ttu-id="32751-158">*ru*</span><span class="sxs-lookup"><span data-stu-id="32751-158">*ru*</span></span>        |
   | <span data-ttu-id="32751-159">Hiszpański</span><span class="sxs-lookup"><span data-stu-id="32751-159">Spanish</span></span>               | <span data-ttu-id="32751-160">*AK*</span><span class="sxs-lookup"><span data-stu-id="32751-160">*es*</span></span>        |

1. <span data-ttu-id="32751-161">Skopiuj pliki *. XML* wyodrębnione w kroku 3 do tego nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="32751-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="32751-162">Pliki *. XML* są podzielone na foldery zestawu SDK, dlatego skopiuj je do zgodnego zestawu SDK, który został wybrany w kroku 4.</span><span class="sxs-lookup"><span data-stu-id="32751-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="32751-163">Modyfikuj język programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="32751-163">Modify Visual Studio language</span></span>

<span data-ttu-id="32751-164">Aby program Visual Studio używał innego języka dla technologii IntelliSense, zainstaluj odpowiedni pakiet językowy.</span><span class="sxs-lookup"><span data-stu-id="32751-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="32751-165">Można to zrobić [podczas instalacji](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) lub w późniejszym czasie, modyfikując instalację programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32751-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="32751-166">Jeśli masz już program Visual Studio skonfigurowany w wybranym języku, instalacja technologii IntelliSense jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="32751-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="32751-167">Instalowanie pakietu językowego</span><span class="sxs-lookup"><span data-stu-id="32751-167">Install the language pack</span></span>

<span data-ttu-id="32751-168">Jeśli podczas instalacji nie został zainstalowany odpowiedni pakiet językowy, zaktualizuj program Visual Studio w następujący sposób, aby zainstalować pakiet językowy:</span><span class="sxs-lookup"><span data-stu-id="32751-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32751-169">Aby zainstalować, zaktualizować lub zmodyfikować program Visual Studio, należy zalogować się przy użyciu konta z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="32751-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="32751-170">Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="32751-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="32751-171">Znajdowanie Instalatora programu Visual Studio na komputerze.</span><span class="sxs-lookup"><span data-stu-id="32751-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="32751-172">Na przykład na komputerze z systemem Windows 10 Wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wyświetlana jako **Instalator programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="32751-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Otwórz Instalator programu Visual Studio z systemu Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="32751-174">Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="32751-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="32751-175">Może być konieczne zaktualizowanie Instalatora przed kontynuowaniem.</span><span class="sxs-lookup"><span data-stu-id="32751-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="32751-176">Jeśli tak, postępuj zgodnie z monitami.</span><span class="sxs-lookup"><span data-stu-id="32751-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="32751-177">W instalatorze poszukaj wersji programu Visual Studio, do której chcesz dodać pakiet językowy, a następnie wybierz **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="32751-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Aktualizowanie lub modyfikowanie programu Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="32751-179">Jeśli nie widzisz przycisku **Modyfikuj** , ale zamiast tego zobaczysz **aktualizację** , musisz zaktualizować program Visual Studio przed zmodyfikowaniem instalacji.</span><span class="sxs-lookup"><span data-stu-id="32751-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="32751-180">Po zakończeniu aktualizacji powinien zostać wyświetlony przycisk **Modyfikuj** .</span><span class="sxs-lookup"><span data-stu-id="32751-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="32751-181">Na karcie **pakiety językowe** zaznacz lub odznacz Języki, które chcesz zainstalować lub odinstalować.</span><span class="sxs-lookup"><span data-stu-id="32751-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Karta pakiety językowe programu Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="32751-183">Wybierz **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="32751-183">Choose **Modify**.</span></span> <span data-ttu-id="32751-184">Rozpocznie się aktualizacja.</span><span class="sxs-lookup"><span data-stu-id="32751-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="32751-185">Modyfikowanie ustawień języka w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="32751-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="32751-186">Po zainstalowaniu żądanych pakietów językowych zmodyfikuj ustawienia programu Visual Studio tak, aby korzystały z innego języka:</span><span class="sxs-lookup"><span data-stu-id="32751-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="32751-187">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32751-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="32751-188">W oknie uruchamiania wybierz pozycję **Kontynuuj bez kodu**.</span><span class="sxs-lookup"><span data-stu-id="32751-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="32751-189">Na pasku menu wybierz pozycję **narzędzia** > **Opcje**.</span><span class="sxs-lookup"><span data-stu-id="32751-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="32751-190">Zostanie otwarte okno dialogowe Opcje.</span><span class="sxs-lookup"><span data-stu-id="32751-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="32751-191">W węźle **środowisko** wybierz pozycję **Ustawienia międzynarodowe**.</span><span class="sxs-lookup"><span data-stu-id="32751-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="32751-192">Z listy rozwijanej **Język** wybierz odpowiedni język.</span><span class="sxs-lookup"><span data-stu-id="32751-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="32751-193">Wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="32751-193">Choose **OK**.</span></span>

1. <span data-ttu-id="32751-194">Zostanie wyświetlone okno dialogowe z informacją, że musisz ponownie uruchomić program Visual Studio, aby zmiany zaczęły obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="32751-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="32751-195">Wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="32751-195">Choose **OK**.</span></span>

1. <span data-ttu-id="32751-196">Uruchom ponownie program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32751-196">Restart Visual Studio.</span></span>

<span data-ttu-id="32751-197">Po wykonaniu tej czynności funkcja IntelliSense powinna działać zgodnie z oczekiwaniami w przypadku otwarcia projektu .NET Core, który jest przeznaczony dla wersji zainstalowanych plików IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="32751-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="32751-198">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32751-198">See also</span></span>

- [<span data-ttu-id="32751-199">Technologia IntelliSense w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="32751-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
