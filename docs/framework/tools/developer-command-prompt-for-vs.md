---
title: wiersz polecenia dla deweloperów dla programu Visual Studio
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715831"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="a27c1-102">wiersz polecenia dla deweloperów dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a27c1-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="a27c1-103">Wiersz polecenia dla deweloperów dla programu Visual Studio umożliwia łatwiejsze korzystanie z narzędzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a27c1-103">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="a27c1-104">Jest to wiersz polecenia, który automatycznie ustawia określone zmienne środowiskowe.</span><span class="sxs-lookup"><span data-stu-id="a27c1-104">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="a27c1-105">Po otwarciu wiersz polecenia dla deweloperów można wprowadzić polecenia dla [.NET Framework narzędzi](index.md) , takich jak `ildasm` lub `clrver`.</span><span class="sxs-lookup"><span data-stu-id="a27c1-105">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a27c1-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a27c1-106">Prerequisites</span></span>

- [<span data-ttu-id="a27c1-107">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="a27c1-107">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="a27c1-108">Wyszukaj wiersz polecenia na komputerze</span><span class="sxs-lookup"><span data-stu-id="a27c1-108">Search for the command prompt on your machine</span></span>

<span data-ttu-id="a27c1-109">W zależności od wersji programu Visual Studio i wszelkich dodatkowych zestawów SDK i obciążeń, które zostały zainstalowane, może być wiele wierszy poleceń.</span><span class="sxs-lookup"><span data-stu-id="a27c1-109">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="a27c1-110">Jeśli poniższe kroki nie działają, możesz spróbować [ręcznie zlokalizować pliki na maszynie](#manually-locate-the-files-on-your-machine) lub [uruchomić wiersz polecenia z poziomu programu Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="a27c1-110">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="a27c1-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a27c1-111">Windows 10</span></span>

1. <span data-ttu-id="a27c1-112">Na klawiaturze wybierz pozycję **uruchom** ![klucz logo systemu Windows.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="a27c1-112">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="a27c1-113">i przewiń do litery **V**.</span><span class="sxs-lookup"><span data-stu-id="a27c1-113">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="a27c1-114">Rozwiń folder **programu Visual Studio 2019** .</span><span class="sxs-lookup"><span data-stu-id="a27c1-114">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="a27c1-115">Wybierz **wiersz polecenia dla deweloperów dla programu VS 2019** (lub wiersza polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="a27c1-115">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="a27c1-116">Alternatywnie można rozpocząć wpisywanie nazwy wiersza polecenia w polu wyszukiwania na pasku zadań, a następnie wybrać wynik, który zostanie wyświetlony na liście wyników wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="a27c1-116">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Animowany plik GIF pokazujący zachowanie wyszukiwania w systemie Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="a27c1-118">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a27c1-118">Windows 8.1</span></span>

1. <span data-ttu-id="a27c1-119">Przejdź do ekranu **startowego** , naciskając klawisz logo systemu Windows ![klawisz logo Windows na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="a27c1-119">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="a27c1-120">na przykład na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="a27c1-120">on your keyboard for example.</span></span>

1. <span data-ttu-id="a27c1-121">Na ekranie **startowym** naciśnij klawisze **Ctrl**+**Tab** , aby otworzyć listę **aplikacje** , a następnie naciśnij klawisz **V**. Spowoduje to wyświetlenie listy zawierającej wszystkie zainstalowane polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a27c1-121">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="a27c1-122">Wybierz **wiersz polecenia dla deweloperów dla programu VS 2019** (lub wiersza polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="a27c1-122">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="a27c1-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="a27c1-123">Windows 7</span></span>

1. <span data-ttu-id="a27c1-124">Wybierz przycisk **Start** , a następnie rozwiń pozycję **Wszystkie programy**.</span><span class="sxs-lookup"><span data-stu-id="a27c1-124">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="a27c1-125">Wybierz pozycję **Visual Studio 2019** > **Visual Studio Tools** > **wiersz polecenia dla deweloperów dla programu vs 2019**lub wiersz polecenia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="a27c1-125">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Menu Start systemu Windows 7 z wyróżnionym wierszem polecenia](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="a27c1-127">Jeśli zainstalowano inne zestawy SDK, takie jak [zestaw SDK systemu Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive), mogą pojawić się dodatkowe polecenia.</span><span class="sxs-lookup"><span data-stu-id="a27c1-127">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="a27c1-128">W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.</span><span class="sxs-lookup"><span data-stu-id="a27c1-128">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="a27c1-129">Ręczne Lokalizowanie plików na maszynie</span><span class="sxs-lookup"><span data-stu-id="a27c1-129">Manually locate the files on your machine</span></span>

<span data-ttu-id="a27c1-130">Zwykle skróty dla poleceń wyświetlanych przez użytkownika są umieszczane w folderze **menu Start** dla programu Visual Studio, na przykład w *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Tools*.</span><span class="sxs-lookup"><span data-stu-id="a27c1-130">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="a27c1-131">Ale jeśli z jakiegoś powodu, wyszukiwanie w wierszu polecenia nie daje oczekiwanych wyników, możesz spróbować ręcznie zlokalizować skrót na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a27c1-131">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="a27c1-132">Spróbuj wyszukać nazwę pliku wiersza polecenia, na przykład *VsDevCmd. bat*, lub przejdź do folderu Tools, takiego jak *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (zmiany ścieżki w zależności od wersji programu Visual Studio, wersji i lokalizacji instalacji).</span><span class="sxs-lookup"><span data-stu-id="a27c1-132">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="a27c1-133">Uruchom wiersz polecenia z wewnątrz programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a27c1-133">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="a27c1-134">Aby ułatwić dostęp, można dodać wiersz polecenia dla deweloperów lub dowolny inny wiersz polecenia do menu Narzędzia w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a27c1-134">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="a27c1-135">Aby udostępnić narzędzie, Dodaj je do listy narzędzi zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="a27c1-135">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="a27c1-136">Oto konkretne kroki:</span><span class="sxs-lookup"><span data-stu-id="a27c1-136">Here are the steps:</span></span>

1. <span data-ttu-id="a27c1-137">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a27c1-137">Open Visual Studio.</span></span>

1. <span data-ttu-id="a27c1-138">W oknie uruchamiania wybierz pozycję **Kontynuuj bez kodu**.</span><span class="sxs-lookup"><span data-stu-id="a27c1-138">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="a27c1-139">Na pasku menu wybierz kolejno opcje **narzędzia** > **narzędzia zewnętrzne**.</span><span class="sxs-lookup"><span data-stu-id="a27c1-139">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="a27c1-140">W oknie dialogowym **narzędzia zewnętrzne** wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="a27c1-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="a27c1-141">Zostanie wyświetlony nowy wpis.</span><span class="sxs-lookup"><span data-stu-id="a27c1-141">A new entry appears.</span></span>

1. <span data-ttu-id="a27c1-142">Wprowadź **tytuł** dla nowego elementu menu, takiego jak `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="a27c1-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="a27c1-143">W polu **polecenie** Określ plik, który chcesz uruchomić, taki jak `%comspec%` lub `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="a27c1-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="a27c1-144">W polu **argumenty** Określ, gdzie znaleźć konkretny wiersz polecenia, który ma być używany, taki jak `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span><span class="sxs-lookup"><span data-stu-id="a27c1-144">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="a27c1-145">To polecenie powoduje uruchomienie wiersz polecenia dla deweloperów zainstalowanego z programem Visual Studio 2019 Community.</span><span class="sxs-lookup"><span data-stu-id="a27c1-145">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="a27c1-146">Zmień tę wartość zgodnie z wersją programu Visual Studio, wydaniem i lokalizacją instalacji.</span><span class="sxs-lookup"><span data-stu-id="a27c1-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="a27c1-147">W polu **katalog początkowy** określ katalog, w którym zostanie uruchomiony wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="a27c1-147">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="a27c1-148">Wybierz wartość, na przykład **Katalog projektu** , wybierając strzałkę obok pola.</span><span class="sxs-lookup"><span data-stu-id="a27c1-148">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="a27c1-149">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a27c1-149">Choose the **OK** button.</span></span>

   ![Okno dialogowe zewnętrznych narzędzi z wartościami pól wypełnione.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="a27c1-151">Nowy element menu zostanie dodany i możesz uzyskać dostęp do wiersza polecenia z menu Narzędzia.</span><span class="sxs-lookup"><span data-stu-id="a27c1-151">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Element menu wiersza polecenia w programie Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="a27c1-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a27c1-153">See also</span></span>

- [<span data-ttu-id="a27c1-154">Narzędzia .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a27c1-154">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="a27c1-155">Zarządzanie narzędziami zewnętrznymi</span><span class="sxs-lookup"><span data-stu-id="a27c1-155">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="a27c1-156">Korzystanie z zestawu C++ narzędzi firmy Microsoft z poziomu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="a27c1-156">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
