---
title: wiersz polecenia dla deweloperów dla programu Visual Studio
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59af252967a18eca858035fb0a3465d909734ddf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044726"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="cd3ba-102">wiersz polecenia dla deweloperów dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cd3ba-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="cd3ba-103">Wiersz polecenia dla deweloperów dla programu Visual Studio umożliwia łatwiejsze korzystanie z narzędzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-103">The Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="cd3ba-104">Jest to wiersz polecenia, który automatycznie ustawia określone zmienne środowiskowe.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-104">It is a command prompt that automatically sets specific environment variables.</span></span>

> [!div class="button"]
> [<span data-ttu-id="cd3ba-105">Pobierz program Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cd3ba-105">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="cd3ba-106">Wyszukaj wiersz polecenia na komputerze</span><span class="sxs-lookup"><span data-stu-id="cd3ba-106">Search for the command prompt on your machine</span></span>

<span data-ttu-id="cd3ba-107">W zależności od używanej wersji programu Visual Studio i dowolnych dodatkowych zestawów SDK można wyświetlać wiele wierszy poleceń.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-107">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="cd3ba-108">Na przykład 64-bitowe wersje programu Visual Studio oferują 32-bitowy i 64-bitowy wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="cd3ba-109">(32-bitowe i 64-bitowe wersje większości narzędzi są takie same, ale kilka narzędzi wprowadza zmiany specyficzne dla środowisk 32-bit i 64-bitowym). Jeśli poniższe kroki nie działają, możesz spróbować [ręcznie zlokalizować pliki na maszynie](#manually-locate-the-files-on-your-machine) lub [uruchomić wiersz polecenia z wewnątrz programu Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="cd3ba-109">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [Run the command prompt from inside Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="cd3ba-110">W systemie Windows 10</span><span class="sxs-lookup"><span data-stu-id="cd3ba-110">In Windows 10</span></span>

1. <span data-ttu-id="cd3ba-111">W polu wyszukiwania na pasku zadań Zacznij wpisywać nazwę narzędzia, `dev` na przykład lub. `developer command prompt`</span><span class="sxs-lookup"><span data-stu-id="cd3ba-111">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="cd3ba-112">Spowoduje to wyświetlenie listy zainstalowanych aplikacji, które pasują do Twojego wzorca wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-112">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="cd3ba-113">Jeśli szukasz innego wiersza polecenia, spróbuj wprowadzić inny termin wyszukiwania, taki jak `prompt`.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-113">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="cd3ba-114">Wybierz **wiersz polecenia dla deweloperów dla programu Visual Studio** (lub wiersz polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="cd3ba-114">Choose the **Developer Command Prompt for Visual Studio** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="cd3ba-115">W Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="cd3ba-115">In Windows 8.1</span></span>

1. <span data-ttu-id="cd3ba-116">Przejdź do ekranu **startowego** , naciskając klawisz logo systemu Windows ![na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="cd3ba-116">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="cd3ba-117">na przykład na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-117">on your keyboard for example.</span></span>

2. <span data-ttu-id="cd3ba-118">Na ekranie **startowym** naciśnij klawisz **Ctrl**+ **, aby otworzyć** listę **aplikacje** , a następnie wprowadź `V`.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-118">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then enter `V`.</span></span> <span data-ttu-id="cd3ba-119">Spowoduje to wyświetlenie listy zawierającej wszystkie zainstalowane polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-119">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="cd3ba-120">Wybierz **wiersz polecenia dla deweloperów** (lub wiersz polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="cd3ba-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="cd3ba-121">W systemie Windows 8</span><span class="sxs-lookup"><span data-stu-id="cd3ba-121">In Windows 8</span></span>

1. <span data-ttu-id="cd3ba-122">Przejdź do ekranu **startowego** , naciskając klawisz logo systemu Windows ![na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="cd3ba-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="cd3ba-123">na przykład na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-123">on your keyboard for example.</span></span>

2. <span data-ttu-id="cd3ba-124">Na ekranie **startowym** naciśnij klawisz ![logo systemu Windows na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="cd3ba-124">On the **Start** screen, press the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="cd3ba-125">`+ Z`.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-125">`+ Z`.</span></span>

3. <span data-ttu-id="cd3ba-126">Wybierz ikonę **widok aplikacje** u dołu ekranu, a następnie wprowadź `V`.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-126">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="cd3ba-127">Spowoduje to wyświetlenie listy zawierającej wszystkie zainstalowane polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-127">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="cd3ba-128">Wybierz **wiersz polecenia dla deweloperów** (lub wiersz polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="cd3ba-128">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="cd3ba-129">W systemie Windows 7</span><span class="sxs-lookup"><span data-stu-id="cd3ba-129">In Windows 7</span></span>

1. <span data-ttu-id="cd3ba-130">Wybierz **Start**, rozwiń **Wszystkie programy**, a następnie rozwiń **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-130">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="cd3ba-131">W zależności od zainstalowanej wersji programu Visual Studio wybierz **Visual Studio Tools**, **wiersz polecenia programu Visual Studio**lub wiersz polecenia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-131">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="cd3ba-132">Jeśli zainstalowano inne zestawy SDK, takie jak [zestaw SDK systemu Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive), mogą pojawić się dodatkowe wiersze poleceń dla architektury ARM, x86 i x64.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-132">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="cd3ba-133">W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-133">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="cd3ba-134">Ręczne Lokalizowanie plików na maszynie</span><span class="sxs-lookup"><span data-stu-id="cd3ba-134">Manually locate the files on your machine</span></span>

<span data-ttu-id="cd3ba-135">Zwykle skróty dla poleceń z zainstalowanymi monitami są umieszczane w folderze **menu Start** dla programu Visual Studio, na przykład w programie C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017 \ Visual Studio Tools.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-135">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="cd3ba-136">Ale jeśli z jakiegoś powodu, wyszukiwanie w wierszu polecenia nie powoduje przeprowadzenia oczekiwanych wyników, możesz spróbować ręcznie zlokalizować skrót na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-136">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="cd3ba-137">Spróbuj wyszukać nazwę pliku wiersza polecenia, na przykład *VsDevCmd. bat*, lub przejdź do folderu Tools, takiego jak C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (zmiany ścieżki zgodnie z wersją programu Visual Studio, wersja i lokalizacja instalacji).</span><span class="sxs-lookup"><span data-stu-id="cd3ba-137">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="cd3ba-138">Uruchom wiersz polecenia z wewnątrz programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cd3ba-138">Run the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="cd3ba-139">Aby ułatwić dostęp, można dodać program Visual Studio wiersz polecenia dla deweloperów lub dowolny inny wiersz polecenia do menu **Narzędzia** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-139">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="cd3ba-140">Aby udostępnić narzędzie, Dodaj je do listy narzędzi zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-140">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="cd3ba-141">Oto konkretne kroki:</span><span class="sxs-lookup"><span data-stu-id="cd3ba-141">Here are the steps:</span></span>

1. <span data-ttu-id="cd3ba-142">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-142">Open Visual Studio.</span></span>

2. <span data-ttu-id="cd3ba-143">Wybierz menu **Narzędzia** , a następnie wybierz polecenie **narzędzia zewnętrzne**.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-143">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="cd3ba-144">W oknie dialogowym **narzędzia zewnętrzne** wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="cd3ba-144">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="cd3ba-145">Zostanie wyświetlony nowy wpis.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-145">A new entry appears.</span></span>

4. <span data-ttu-id="cd3ba-146">Wprowadź **tytuł** dla nowego elementu menu, na przykład `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-146">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="cd3ba-147">W polu **polecenie** Określ plik, który chcesz uruchomić, `%comspec%` na przykład lub. `C:\Windows\System32\cmd.exe`</span><span class="sxs-lookup"><span data-stu-id="cd3ba-147">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="cd3ba-148">W polu **argumenty** Określ lokalizację, w której ma znajdować się konkretny wiersz polecenia, który ma być `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` używany na przykład (to polecenie powoduje uruchomienie wiersz polecenia dla deweloperów zainstalowanego z programem Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="cd3ba-148">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="cd3ba-149">Zmień tę wartość zgodnie z wersją programu Visual Studio, wydaniem i lokalizacją instalacji.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-149">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="cd3ba-150">Wybierz wartość pola **katalog początkowy** , na przykład **Katalog projektu**.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-150">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="cd3ba-151">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="cd3ba-151">Choose the **OK** button.</span></span>

   <span data-ttu-id="cd3ba-152">Nowy element menu zostanie dodany i możesz uzyskać dostęp do wiersza polecenia z menu **Narzędzia** .</span><span class="sxs-lookup"><span data-stu-id="cd3ba-152">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

   ![Element menu wiersza polecenia w programie Visual Studio](./media/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="cd3ba-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd3ba-154">See also</span></span>

- [<span data-ttu-id="cd3ba-155">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="cd3ba-155">Tools</span></span>](index.md)
- [<span data-ttu-id="cd3ba-156">Zarządzanie narzędziami zewnętrznymi</span><span class="sxs-lookup"><span data-stu-id="cd3ba-156">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
