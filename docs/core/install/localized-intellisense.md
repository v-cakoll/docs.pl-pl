---
title: Instalowanie zlokalizowanych plików IntelliSense
description: Dowiedz się, jak skonfigurować komputer deweloperski do używania zlokalizowanych plików IntelliSense dla projektów .NET Core w programie Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157716"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="6ff70-103">Jak zainstalować zlokalizowane pliki IntelliSense dla programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ff70-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="6ff70-104">[IntelliSense](/visualstudio/ide/using-intellisense) to pomoc uzupełniania kodu, która jest dostępna w różnych zintegrowanych środowiskach programistycznych (IDEs), takich jak Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ff70-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="6ff70-105">Domyślnie podczas opracowywania projektów .NET Core zestaw SDK zawiera tylko angielską wersję plików IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="6ff70-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="6ff70-106">W tym artykule wyjaśniono:</span><span class="sxs-lookup"><span data-stu-id="6ff70-106">This article explains:</span></span>

- <span data-ttu-id="6ff70-107">Jak zainstalować zlokalizowane wersje tych plików.</span><span class="sxs-lookup"><span data-stu-id="6ff70-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="6ff70-108">Jak zmodyfikować instalację programu Visual Studio, aby używać innego języka.</span><span class="sxs-lookup"><span data-stu-id="6ff70-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6ff70-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6ff70-109">Prerequisites</span></span>

- <span data-ttu-id="6ff70-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="6ff70-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="6ff70-111">[Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="6ff70-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="6ff70-112">Pobieranie i instalowanie zlokalizowanych plików IntelliSense</span><span class="sxs-lookup"><span data-stu-id="6ff70-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ff70-113">Ta procedura wymaga posiadania uprawnień administratora do kopiowania plików IntelliSense do folderu instalacyjnego .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ff70-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="6ff70-114">Przejdź do strony [Pobierz pliki IntelliSense.](https://dotnet.microsoft.com/download/dotnet-core/intellisense)</span><span class="sxs-lookup"><span data-stu-id="6ff70-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="6ff70-115">Pobierz plik IntelliSense dla języka i wersji, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="6ff70-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="6ff70-116">Wyodrębnij zawartość pliku zip.</span><span class="sxs-lookup"><span data-stu-id="6ff70-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="6ff70-117">Przejdź do folderu .NET Core Intellisense.</span><span class="sxs-lookup"><span data-stu-id="6ff70-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="6ff70-118">Przejdź do folderu instalacyjnego programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ff70-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="6ff70-119">Domyślnie znajduje się w obszarze *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="6ff70-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="6ff70-120">Wybierz zestaw SDK, dla którego chcesz zainstalować program IntelliSense, i przejdź do skojarzonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="6ff70-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="6ff70-121">Istnieją następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="6ff70-121">You have the following options:</span></span>

      | <span data-ttu-id="6ff70-122">Typ sdk</span><span class="sxs-lookup"><span data-stu-id="6ff70-122">SDK type</span></span>        | <span data-ttu-id="6ff70-123">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="6ff70-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="6ff70-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="6ff70-124">.NET Core</span></span>       | <span data-ttu-id="6ff70-125">*Plik Microsoft.NETCore.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="6ff70-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="6ff70-126">Pulpit systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6ff70-126">Windows Desktop</span></span> | <span data-ttu-id="6ff70-127">*Microsoft.WindowsDesktop.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="6ff70-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="6ff70-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="6ff70-128">.NET Standard</span></span>   | <span data-ttu-id="6ff70-129">*NETStandard.Library.Ref*</span><span class="sxs-lookup"><span data-stu-id="6ff70-129">*NETStandard.Library.Ref*</span></span>          |

   1. <span data-ttu-id="6ff70-130">Przejdź do wersji, dla której chcesz zainstalować zlokalizowany program IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="6ff70-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="6ff70-131">Na przykład *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="6ff70-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="6ff70-132">Otwórz folder *ref.*</span><span class="sxs-lookup"><span data-stu-id="6ff70-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="6ff70-133">Otwórz folder moniker.</span><span class="sxs-lookup"><span data-stu-id="6ff70-133">Open the moniker folder.</span></span> <span data-ttu-id="6ff70-134">Na przykład *netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="6ff70-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="6ff70-135">Tak więc pełna ścieżka, do której chcesz przejść, będzie wyglądać podobnie do *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="6ff70-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="6ff70-136">Utwórz podfolder wewnątrz właśnie otwartego folderu moniker.</span><span class="sxs-lookup"><span data-stu-id="6ff70-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="6ff70-137">Nazwa folderu wskazuje, którego języka chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="6ff70-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="6ff70-138">W poniższej tabeli określono różne opcje:</span><span class="sxs-lookup"><span data-stu-id="6ff70-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="6ff70-139">Język</span><span class="sxs-lookup"><span data-stu-id="6ff70-139">Language</span></span>              | <span data-ttu-id="6ff70-140">Nazwa folderu</span><span class="sxs-lookup"><span data-stu-id="6ff70-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="6ff70-141">Portugalski brazylijski</span><span class="sxs-lookup"><span data-stu-id="6ff70-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="6ff70-142">*pt-br (pt-br)*</span><span class="sxs-lookup"><span data-stu-id="6ff70-142">*pt-br*</span></span>     |
   | <span data-ttu-id="6ff70-143">Chiński (uproszczony)</span><span class="sxs-lookup"><span data-stu-id="6ff70-143">Chinese (simplified)</span></span>  | <span data-ttu-id="6ff70-144">*zh-hans (zh-hans)*</span><span class="sxs-lookup"><span data-stu-id="6ff70-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="6ff70-145">Chiński (tradycyjny)</span><span class="sxs-lookup"><span data-stu-id="6ff70-145">Chinese (traditional)</span></span> | <span data-ttu-id="6ff70-146">*zh-hant (zh-hant)*</span><span class="sxs-lookup"><span data-stu-id="6ff70-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="6ff70-147">Francuski</span><span class="sxs-lookup"><span data-stu-id="6ff70-147">French</span></span>                | <span data-ttu-id="6ff70-148">*O*</span><span class="sxs-lookup"><span data-stu-id="6ff70-148">*fr*</span></span>        |
   | <span data-ttu-id="6ff70-149">Niemiecki</span><span class="sxs-lookup"><span data-stu-id="6ff70-149">German</span></span>                | <span data-ttu-id="6ff70-150">*De*</span><span class="sxs-lookup"><span data-stu-id="6ff70-150">*de*</span></span>        |
   | <span data-ttu-id="6ff70-151">Włoski</span><span class="sxs-lookup"><span data-stu-id="6ff70-151">Italian</span></span>               | <span data-ttu-id="6ff70-152">*to*</span><span class="sxs-lookup"><span data-stu-id="6ff70-152">*it*</span></span>        |
   | <span data-ttu-id="6ff70-153">Japoński</span><span class="sxs-lookup"><span data-stu-id="6ff70-153">Japanese</span></span>              | <span data-ttu-id="6ff70-154">*ja*</span><span class="sxs-lookup"><span data-stu-id="6ff70-154">*ja*</span></span>        |
   | <span data-ttu-id="6ff70-155">Koreański</span><span class="sxs-lookup"><span data-stu-id="6ff70-155">Korean</span></span>                | <span data-ttu-id="6ff70-156">*Ko*</span><span class="sxs-lookup"><span data-stu-id="6ff70-156">*ko*</span></span>        |
   | <span data-ttu-id="6ff70-157">Rosyjski</span><span class="sxs-lookup"><span data-stu-id="6ff70-157">Russian</span></span>               | <span data-ttu-id="6ff70-158">*Ru*</span><span class="sxs-lookup"><span data-stu-id="6ff70-158">*ru*</span></span>        |
   | <span data-ttu-id="6ff70-159">Hiszpański</span><span class="sxs-lookup"><span data-stu-id="6ff70-159">Spanish</span></span>               | <span data-ttu-id="6ff70-160">*Es*</span><span class="sxs-lookup"><span data-stu-id="6ff70-160">*es*</span></span>        |

1. <span data-ttu-id="6ff70-161">Skopiuj pliki *xml* wyodrębnione w kroku 3 do tego nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="6ff70-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="6ff70-162">Pliki *xml* są podzielone według folderów SDK, więc skopiuj je do pasującego sdk wybranego w kroku 4.</span><span class="sxs-lookup"><span data-stu-id="6ff70-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="6ff70-163">Modyfikowanie języka programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ff70-163">Modify Visual Studio language</span></span>

<span data-ttu-id="6ff70-164">Aby program Visual Studio używał innego języka dla programu IntelliSense, zainstaluj odpowiedni pakiet językowy.</span><span class="sxs-lookup"><span data-stu-id="6ff70-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="6ff70-165">Można to zrobić [podczas instalacji](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) lub w późniejszym czasie, modyfikując instalację programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ff70-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="6ff70-166">Jeśli program Visual Studio jest już skonfigurowany do wybranego języka, instalacja intelliSense jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="6ff70-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="6ff70-167">Instalowanie pakietu językowego</span><span class="sxs-lookup"><span data-stu-id="6ff70-167">Install the language pack</span></span>

<span data-ttu-id="6ff70-168">Jeśli podczas instalacji nie zainstalowałeś żądanego pakietu językowego, zaktualizuj program Visual Studio w następujący sposób, aby zainstalować pakiet językowy:</span><span class="sxs-lookup"><span data-stu-id="6ff70-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ff70-169">Aby zainstalować, zaktualizować lub zmodyfikować program Visual Studio, należy zalogować się przy użyciu konta, które ma uprawnienia administratora.</span><span class="sxs-lookup"><span data-stu-id="6ff70-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="6ff70-170">Aby uzyskać więcej informacji, zobacz [Uprawnienia użytkownika i Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="6ff70-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="6ff70-171">Znajdź Instalatorprogramu Visual Studio na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6ff70-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="6ff70-172">Na przykład na komputerze z systemem Windows 10 wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wymieniona jako **Instalator programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6ff70-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Otwieranie Instalatora programu Visual Studio z systemu Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="6ff70-174">Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="6ff70-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="6ff70-175">Może być trzeba zaktualizować instalator przed kontynuowaniem.</span><span class="sxs-lookup"><span data-stu-id="6ff70-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="6ff70-176">Jeśli tak, postępuj zgodnie z instrukcjami.</span><span class="sxs-lookup"><span data-stu-id="6ff70-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="6ff70-177">W instalatorze poszukaj wersji programu Visual Studio, do której chcesz dodać pakiet językowy, a następnie wybierz pozycję **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="6ff70-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Aktualizowanie lub modyfikowanie programu Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="6ff70-179">Jeśli nie widzisz przycisku **Modyfikuj,** ale zamiast tego zostanie wyświetlony **przycisk Aktualizuj,** musisz zaktualizować program Visual Studio, zanim będzie można zmodyfikować instalację.</span><span class="sxs-lookup"><span data-stu-id="6ff70-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="6ff70-180">Po zakończeniu aktualizacji powinien pojawić się przycisk **Modyfikuj.**</span><span class="sxs-lookup"><span data-stu-id="6ff70-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="6ff70-181">Na karcie **Pakiety językowe** wybierz lub usuń zaznaczenie języków, które chcesz zainstalować lub odinstalować.</span><span class="sxs-lookup"><span data-stu-id="6ff70-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Karta Pakiety językowe programu Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="6ff70-183">Wybierz **pozycję Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="6ff70-183">Choose **Modify**.</span></span> <span data-ttu-id="6ff70-184">Rozpocznie się aktualizacja.</span><span class="sxs-lookup"><span data-stu-id="6ff70-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="6ff70-185">Modyfikowanie ustawień języka w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ff70-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="6ff70-186">Po zainstalowaniu żądanych pakietów językowych zmodyfikuj ustawienia programu Visual Studio, aby używać innego języka:</span><span class="sxs-lookup"><span data-stu-id="6ff70-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="6ff70-187">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ff70-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="6ff70-188">W oknie startowym wybierz pozycję **Kontynuuj bez kodu**.</span><span class="sxs-lookup"><span data-stu-id="6ff70-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="6ff70-189">Na pasku menu wybierz pozycję**Opcje** **narzędzi** > .</span><span class="sxs-lookup"><span data-stu-id="6ff70-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="6ff70-190">Zostanie otwarte okno dialogowe Opcje.</span><span class="sxs-lookup"><span data-stu-id="6ff70-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="6ff70-191">W obszarze **Węzeł Środowisko** wybierz pozycję **Ustawienia międzynarodowe**.</span><span class="sxs-lookup"><span data-stu-id="6ff70-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="6ff70-192">W **obszarze** rozwijanym Język wybierz żądany język.</span><span class="sxs-lookup"><span data-stu-id="6ff70-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="6ff70-193">Wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ff70-193">Choose **OK**.</span></span>

1. <span data-ttu-id="6ff70-194">Okno dialogowe informuje, że należy ponownie uruchomić program Visual Studio, aby zmiany zaczęły obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="6ff70-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="6ff70-195">Wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ff70-195">Choose **OK**.</span></span>

1. <span data-ttu-id="6ff70-196">Uruchom ponownie program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ff70-196">Restart Visual Studio.</span></span>

<span data-ttu-id="6ff70-197">Następnie intelliSense powinien działać zgodnie z oczekiwaniami po otwarciu projektu .NET Core, który jest przeznaczony dla wersji właśnie zainstalowanych plików IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="6ff70-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ff70-198">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ff70-198">See also</span></span>

- [<span data-ttu-id="6ff70-199">IntelliSense w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ff70-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
