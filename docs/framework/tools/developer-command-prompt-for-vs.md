---
title: Wiersz polecenia dewelopera dla programu Visual Studio
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715831"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="93d67-102">Wiersz polecenia dewelopera dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="93d67-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="93d67-103">Wiersz polecenia dewelopera dla programu Visual Studio umożliwia łatwiejsze korzystanie z narzędzi programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93d67-103">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="93d67-104">Jest to wiersz polecenia, który automatycznie ustawia określone zmienne środowiskowe.</span><span class="sxs-lookup"><span data-stu-id="93d67-104">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="93d67-105">Po otwarciu wiersza polecenia dewelopera można wprowadzić polecenia `ildasm` dla `clrver`narzędzi [programu .NET Framework,](index.md) takich jak lub .</span><span class="sxs-lookup"><span data-stu-id="93d67-105">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="93d67-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="93d67-106">Prerequisites</span></span>

- [<span data-ttu-id="93d67-107">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="93d67-107">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="93d67-108">Wyszukiwanie wiersza polecenia na komputerze</span><span class="sxs-lookup"><span data-stu-id="93d67-108">Search for the command prompt on your machine</span></span>

<span data-ttu-id="93d67-109">Może być wiele wierszy polecenia, w zależności od wersji programu Visual Studio i wszelkie dodatkowe zestawy SDK i obciążeń, które zostały zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="93d67-109">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="93d67-110">Jeśli poniższe kroki nie działają, możesz spróbować [ręcznie zlokalizować pliki na komputerze](#manually-locate-the-files-on-your-machine) lub uruchomić wiersz polecenia z programu Visual [Studio](#start-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="93d67-110">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="93d67-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="93d67-111">Windows 10</span></span>

1. <span data-ttu-id="93d67-112">Wybierz **pozycję Uruchom** ![klawisz logo systemu Windows na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="93d67-112">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="93d67-113">i przewiń do litery **V**.</span><span class="sxs-lookup"><span data-stu-id="93d67-113">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="93d67-114">Rozwiń folder **programu Visual Studio 2019.**</span><span class="sxs-lookup"><span data-stu-id="93d67-114">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="93d67-115">Wybierz **pozycję Developer Command Prompt for VS 2019** (lub wiersz polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="93d67-115">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="93d67-116">Alternatywnie można rozpocząć wpisywanie nazwy wiersza polecenia w polu wyszukiwania na pasku zadań i wybrać wynik, który ma być wyświetlany, gdy lista wyników zacznie wyświetlać dopasowania wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="93d67-116">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Animowany gif pokazujący zachowanie wyszukiwania w systemie Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="93d67-118">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="93d67-118">Windows 8.1</span></span>

1. <span data-ttu-id="93d67-119">Przejdź do ekranu **startowego,** naciskając ![klawisz logo Windows na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="93d67-119">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="93d67-120">na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="93d67-120">on your keyboard for example.</span></span>

1. <span data-ttu-id="93d67-121">Na ekranie **startowym** naciśnij klawisz **Ctrl**+**Tab,** aby otworzyć listę **Aplikacje,** a następnie naciśnij klawisz **V**. Spowoduje to wyświetlenie listy zawierającej wszystkie zainstalowane wiersze poleceń programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93d67-121">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="93d67-122">Wybierz **pozycję Developer Command Prompt for VS 2019** (lub wiersz polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="93d67-122">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="93d67-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="93d67-123">Windows 7</span></span>

1. <span data-ttu-id="93d67-124">Wybierz **pozycję Start,** a następnie rozwiń pozycję **Wszystkie programy**.</span><span class="sxs-lookup"><span data-stu-id="93d67-124">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="93d67-125">Wybierz polecenie **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**lub wiersz polecenia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="93d67-125">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Menu Start systemu Windows 7 z wyróżnionym wierszem polecenia](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="93d67-127">Jeśli masz zainstalowane inne pakiety SDK, takie jak [windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje,](https://developer.microsoft.com/windows/downloads/sdk-archive)mogą zostać wyświetlona dodatkowe monity o polecenia.</span><span class="sxs-lookup"><span data-stu-id="93d67-127">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="93d67-128">W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.</span><span class="sxs-lookup"><span data-stu-id="93d67-128">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="93d67-129">Ręczne lokalizowanie plików na komputerze</span><span class="sxs-lookup"><span data-stu-id="93d67-129">Manually locate the files on your machine</span></span>

<span data-ttu-id="93d67-130">Zazwyczaj skróty zainstalowanych wierszy polecenia są umieszczane w folderze **Menu Start** programu Visual Studio, na przykład w *programie "ProgramData%\Microsoft\Windows\Menu Start\Programy\Visual Studio 2019\Visual Studio Tools*.</span><span class="sxs-lookup"><span data-stu-id="93d67-130">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="93d67-131">Jeśli jednak z jakiegoś powodu wyszukiwanie wiersza polecenia nie daje oczekiwanych rezultatów, możesz spróbować ręcznie zlokalizować skrót na komputerze.</span><span class="sxs-lookup"><span data-stu-id="93d67-131">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="93d67-132">Spróbuj wyszukać nazwę pliku wiersza polecenia, takiego jak *VsDevCmd.bat,* lub przejdź do folderu Narzędzia, takiego jak *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (ścieżka zmienia się zgodnie z wersją programu Visual Studio, wersją i lokalizacją instalacji).</span><span class="sxs-lookup"><span data-stu-id="93d67-132">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="93d67-133">Uruchamianie wiersza polecenia od wewnątrz programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="93d67-133">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="93d67-134">Aby uzyskać łatwiejszy dostęp, można dodać wiersz polecenia dewelopera lub dowolny inny wiersz polecenia do menu Narzędzia w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93d67-134">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="93d67-135">Aby udostępnić narzędzie, dodaj je do listy narzędzi zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="93d67-135">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="93d67-136">Oto konkretne kroki:</span><span class="sxs-lookup"><span data-stu-id="93d67-136">Here are the steps:</span></span>

1. <span data-ttu-id="93d67-137">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93d67-137">Open Visual Studio.</span></span>

1. <span data-ttu-id="93d67-138">W oknie startowym wybierz pozycję **Kontynuuj bez kodu**.</span><span class="sxs-lookup"><span data-stu-id="93d67-138">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="93d67-139">Na pasku menu wybierz pozycję Narzędzia**zewnętrzne** **Narzędzia** > .</span><span class="sxs-lookup"><span data-stu-id="93d67-139">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="93d67-140">W oknie dialogowym **Narzędzia zewnętrzne** wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="93d67-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="93d67-141">Pojawi się nowy wpis.</span><span class="sxs-lookup"><span data-stu-id="93d67-141">A new entry appears.</span></span>

1. <span data-ttu-id="93d67-142">Wprowadź **tytuł** dla nowego elementu `Command Prompt`menu, takiego jak .</span><span class="sxs-lookup"><span data-stu-id="93d67-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="93d67-143">W polu **Polecenie** określ plik, który chcesz `%comspec%` `C:\Windows\System32\cmd.exe`uruchomić, na przykład lub .</span><span class="sxs-lookup"><span data-stu-id="93d67-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="93d67-144">W polu **Argumenty** określ, gdzie ma być używany określony `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`wiersz polecenia, którego chcesz użyć, na przykład .</span><span class="sxs-lookup"><span data-stu-id="93d67-144">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="93d67-145">To polecenie uruchamia wiersz polecenia dewelopera, który jest zainstalowany w środowisku społeczności programu Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="93d67-145">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="93d67-146">Zmień tę wartość zgodnie z wersją programu Visual Studio, wersją i lokalizacją instalacji.</span><span class="sxs-lookup"><span data-stu-id="93d67-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="93d67-147">W polu **Katalog początkowy** określ katalog, w którym zostanie uruchomiony wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="93d67-147">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="93d67-148">Wybierz wartość, taką jak **Katalog projektów,** zaznaczając strzałkę obok pola.</span><span class="sxs-lookup"><span data-stu-id="93d67-148">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="93d67-149">Wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="93d67-149">Choose the **OK** button.</span></span>

   ![Okno dialogowe Narzędzia zewnętrzne z wypełnionymi wartościami pól.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="93d67-151">Nowy element menu zostanie dodany i można uzyskać dostęp do wiersza polecenia z menu Narzędzia.</span><span class="sxs-lookup"><span data-stu-id="93d67-151">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Pozycja menu wiersza polecenia w programie Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="93d67-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93d67-153">See also</span></span>

- [<span data-ttu-id="93d67-154">Narzędzia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="93d67-154">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="93d67-155">Zarządzanie narzędziami zewnętrznymi</span><span class="sxs-lookup"><span data-stu-id="93d67-155">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="93d67-156">Używanie zestawu narzędzi Microsoft C++ z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="93d67-156">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
