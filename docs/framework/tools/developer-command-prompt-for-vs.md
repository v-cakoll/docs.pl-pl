---
title: wiersz polecenia dla deweloperów dla programu Visual Studio
description: Dowiedz się, jak korzystać z wiersz polecenia dla deweloperów dla programu Visual Studio, co ułatwia korzystanie z narzędzi platformy .NET. Automatycznie ustawia określone zmienne środowiskowe.
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
ms.openlocfilehash: 92416820f47cb778dfcc916b8626df4aa328814c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167180"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="f72b8-104">wiersz polecenia dla deweloperów dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f72b8-104">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="f72b8-105">Wiersz polecenia dla deweloperów dla programu Visual Studio umożliwia łatwiejsze korzystanie z narzędzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f72b8-105">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="f72b8-106">Jest to wiersz polecenia, który automatycznie ustawia określone zmienne środowiskowe.</span><span class="sxs-lookup"><span data-stu-id="f72b8-106">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="f72b8-107">Po otwarciu wiersz polecenia dla deweloperów można wprowadzić polecenia dla [.NET Framework narzędzi](index.md) , takich jak `ildasm` lub `clrver` .</span><span class="sxs-lookup"><span data-stu-id="f72b8-107">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f72b8-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f72b8-108">Prerequisites</span></span>

- [<span data-ttu-id="f72b8-109">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="f72b8-109">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="f72b8-110">Wyszukaj wiersz polecenia na komputerze</span><span class="sxs-lookup"><span data-stu-id="f72b8-110">Search for the command prompt on your machine</span></span>

<span data-ttu-id="f72b8-111">W zależności od wersji programu Visual Studio i wszelkich dodatkowych zestawów SDK i obciążeń, które zostały zainstalowane, może być wiele wierszy poleceń.</span><span class="sxs-lookup"><span data-stu-id="f72b8-111">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="f72b8-112">Jeśli poniższe kroki nie działają, możesz spróbować [ręcznie zlokalizować pliki na maszynie](#manually-locate-the-files-on-your-machine) lub [uruchomić wiersz polecenia z poziomu programu Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f72b8-112">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="f72b8-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="f72b8-113">Windows 10</span></span>

1. <span data-ttu-id="f72b8-114">Wybierz pozycję **Uruchom** ![ klucz logo systemu Windows na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="f72b8-114">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="f72b8-115">i przewiń do litery **V**.</span><span class="sxs-lookup"><span data-stu-id="f72b8-115">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="f72b8-116">Rozwiń folder **programu Visual Studio 2019** .</span><span class="sxs-lookup"><span data-stu-id="f72b8-116">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="f72b8-117">Wybierz **wiersz polecenia dla deweloperów dla programu VS 2019** (lub wiersza polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="f72b8-117">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="f72b8-118">Alternatywnie można rozpocząć wpisywanie nazwy wiersza polecenia w polu wyszukiwania na pasku zadań, a następnie wybrać wynik, który zostanie wyświetlony na liście wyników wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="f72b8-118">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Animowany plik GIF pokazujący zachowanie wyszukiwania w systemie Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="f72b8-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="f72b8-120">Windows 8.1</span></span>

1. <span data-ttu-id="f72b8-121">Przejdź do ekranu **startowego** , naciskając klawisz logo systemu Windows ![ na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="f72b8-121">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="f72b8-122">na przykład na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="f72b8-122">on your keyboard for example.</span></span>

1. <span data-ttu-id="f72b8-123">Na ekranie **startowym** naciśnij klawisz **Ctrl**, + **Tab** aby otworzyć listę **aplikacje** , a następnie naciśnij klawisz **V**. Spowoduje to wyświetlenie listy zawierającej wszystkie zainstalowane polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f72b8-123">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="f72b8-124">Wybierz **wiersz polecenia dla deweloperów dla programu VS 2019** (lub wiersza polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="f72b8-124">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="f72b8-125">Windows 7</span><span class="sxs-lookup"><span data-stu-id="f72b8-125">Windows 7</span></span>

1. <span data-ttu-id="f72b8-126">Wybierz przycisk **Start** , a następnie rozwiń pozycję **Wszystkie programy**.</span><span class="sxs-lookup"><span data-stu-id="f72b8-126">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="f72b8-127">Wybierz pozycję **Visual Studio 2019**  >  **Visual Studio Tools**  >  **wiersz polecenia dla deweloperów dla programu vs 2019**lub wiersz polecenia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="f72b8-127">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Menu Start systemu Windows 7 z wyróżnionym wierszem polecenia](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="f72b8-129">Jeśli zainstalowano inne zestawy SDK, takie jak [zestaw SDK systemu Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive), mogą pojawić się dodatkowe polecenia.</span><span class="sxs-lookup"><span data-stu-id="f72b8-129">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="f72b8-130">W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.</span><span class="sxs-lookup"><span data-stu-id="f72b8-130">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="f72b8-131">Ręczne Lokalizowanie plików na maszynie</span><span class="sxs-lookup"><span data-stu-id="f72b8-131">Manually locate the files on your machine</span></span>

<span data-ttu-id="f72b8-132">Zwykle skróty dla poleceń wyświetlanych przez użytkownika są umieszczane w folderze **menu Start** dla programu Visual Studio, na przykład w *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Tools*.</span><span class="sxs-lookup"><span data-stu-id="f72b8-132">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="f72b8-133">Ale jeśli z jakiegoś powodu, wyszukiwanie w wierszu polecenia nie daje oczekiwanych wyników, możesz spróbować ręcznie zlokalizować skrót na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f72b8-133">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="f72b8-134">Spróbuj wyszukać nazwę pliku wiersza polecenia, na przykład *VsDevCmd.bat*, lub przejdź do folderu Tools, takiego jak *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (zmiany ścieżki według wersji programu Visual Studio, wersji i lokalizacji instalacji).</span><span class="sxs-lookup"><span data-stu-id="f72b8-134">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="f72b8-135">Uruchom wiersz polecenia z wewnątrz programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f72b8-135">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="f72b8-136">Aby ułatwić dostęp, można dodać wiersz polecenia dla deweloperów lub dowolny inny wiersz polecenia do menu Narzędzia w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f72b8-136">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="f72b8-137">Aby udostępnić narzędzie, Dodaj je do listy narzędzi zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="f72b8-137">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="f72b8-138">Oto odpowiednie kroki:</span><span class="sxs-lookup"><span data-stu-id="f72b8-138">Here are the steps:</span></span>

1. <span data-ttu-id="f72b8-139">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f72b8-139">Open Visual Studio.</span></span>

1. <span data-ttu-id="f72b8-140">W oknie uruchamiania wybierz pozycję **Kontynuuj bez kodu**.</span><span class="sxs-lookup"><span data-stu-id="f72b8-140">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="f72b8-141">Na pasku menu wybierz kolejno opcje **Narzędzia**  >  **zewnętrzne narzędzia**.</span><span class="sxs-lookup"><span data-stu-id="f72b8-141">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="f72b8-142">W oknie dialogowym **narzędzia zewnętrzne** wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="f72b8-142">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="f72b8-143">Zostanie wyświetlony nowy wpis.</span><span class="sxs-lookup"><span data-stu-id="f72b8-143">A new entry appears.</span></span>

1. <span data-ttu-id="f72b8-144">Wprowadź **tytuł** dla nowego elementu menu, na przykład `Command Prompt` .</span><span class="sxs-lookup"><span data-stu-id="f72b8-144">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="f72b8-145">W polu **polecenie** Określ plik, który chcesz uruchomić, na przykład `%comspec%` lub `C:\Windows\System32\cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="f72b8-145">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="f72b8-146">W polu **argumenty** określ miejsce znalezienia konkretnego wiersza polecenia, którego chcesz użyć, na przykład `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"` .</span><span class="sxs-lookup"><span data-stu-id="f72b8-146">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="f72b8-147">To polecenie powoduje uruchomienie wiersz polecenia dla deweloperów zainstalowanego z programem Visual Studio 2019 Community.</span><span class="sxs-lookup"><span data-stu-id="f72b8-147">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="f72b8-148">Zmień tę wartość zgodnie z wersją programu Visual Studio, wydaniem i lokalizacją instalacji.</span><span class="sxs-lookup"><span data-stu-id="f72b8-148">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="f72b8-149">W polu **katalog początkowy** określ katalog, w którym zostanie uruchomiony wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="f72b8-149">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="f72b8-150">Wybierz wartość, na przykład **Katalog projektu** , wybierając strzałkę obok pola.</span><span class="sxs-lookup"><span data-stu-id="f72b8-150">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="f72b8-151">Wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="f72b8-151">Choose the **OK** button.</span></span>

   ![Okno dialogowe zewnętrznych narzędzi z wartościami pól wypełnione.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="f72b8-153">Nowy element menu zostanie dodany i możesz uzyskać dostęp do wiersza polecenia z menu Narzędzia.</span><span class="sxs-lookup"><span data-stu-id="f72b8-153">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Element menu wiersza polecenia w programie Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="f72b8-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f72b8-155">See also</span></span>

- [<span data-ttu-id="f72b8-156">Narzędzia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f72b8-156">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="f72b8-157">Zarządzanie narzędziami zewnętrznymi</span><span class="sxs-lookup"><span data-stu-id="f72b8-157">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="f72b8-158">Używanie zestawu narzędzi platformy Microsoft C++ w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="f72b8-158">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
