---
title: Wiersz polecenia programisty dla programu Visual Studio
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
ms.openlocfilehash: 4c95074190419dd3e984c7659ede917b83b97f08
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524719"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="427d0-102">Wiersz polecenia programisty dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="427d0-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="427d0-103">Wiersz polecenia dla deweloperów programu Visual Studio automatycznie ustawia zmienne środowiskowe, które pozwalają na łatwe używanie narzędzi programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="427d0-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span>

> [!div class="button"]
[<span data-ttu-id="427d0-104">Pobierz program Visual Studio</span><span class="sxs-lookup"><span data-stu-id="427d0-104">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="427d0-105">Wyszukiwanie w wierszu polecenia na komputerze</span><span class="sxs-lookup"><span data-stu-id="427d0-105">Searching for the command prompt on your machine</span></span>

<span data-ttu-id="427d0-106">Może mieć kilka wierszy polecenia, w zależności od wersji programu Visual Studio oraz wszelkie dodatkowe zainstalowanych zestawów SDK.</span><span class="sxs-lookup"><span data-stu-id="427d0-106">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="427d0-107">Na przykład 64-bitowe wersje programu Visual Studio oferują 32-bitowy i 64-bitowy wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="427d0-107">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="427d0-108">(32-bitowych i 64-bitowe wersje większości narzędzi są takie same; jednak niektóre narzędzia wprowadzają zmiany specyficzne dla środowisk 32-bitowych i 64-bitowych). Jeśli poniższe kroki nie zadziałają, spróbuj [ręcznie lokalizowania plików na maszynie](#manually-locating-the-files-on-your-machine) lub [uruchamiając wiersz polecenia z poziomu programu Visual Studio](#running-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="427d0-108">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locating the files on your machine](#manually-locating-the-files-on-your-machine) or [Running the command prompt from inside Visual Studio](#running-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="427d0-109">W systemie Windows 10</span><span class="sxs-lookup"><span data-stu-id="427d0-109">In Windows 10</span></span>

1. <span data-ttu-id="427d0-110">W polu wyszukiwania na pasku zadań, należy uruchomić, wpisując nazwę narzędzia, takie jak `dev` lub `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="427d0-110">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="427d0-111">Wyświetlenie listy zainstalowanych aplikacji spełniających kryteria wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="427d0-111">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="427d0-112">Jeśli potrzebujesz innego wiersza polecenia, spróbuj wprowadzić różne wyszukiwany termin takich jak `prompt`.</span><span class="sxs-lookup"><span data-stu-id="427d0-112">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="427d0-113">Wybierz **wiersz polecenia dla deweloperów** (lub wiersza polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="427d0-113">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="427d0-114">W Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="427d0-114">In Windows 8.1</span></span>

1. <span data-ttu-id="427d0-115">Przejdź do **Start** ekran przez naciśnięcie klawiszy logo Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.</span><span class="sxs-lookup"><span data-stu-id="427d0-115">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="427d0-116">Na **Start** ekranu, naciśnij klawisz `CTRL + TAB` otworzyć **aplikacje** listy, a następnie wprowadź `V`.</span><span class="sxs-lookup"><span data-stu-id="427d0-116">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="427d0-117">Wybranie tej opcji powoduje listy, która zawiera wszystkie zainstalowane wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="427d0-117">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="427d0-118">Wybierz **wiersz polecenia dla deweloperów** (lub wiersza polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="427d0-118">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="427d0-119">W systemie Windows 8</span><span class="sxs-lookup"><span data-stu-id="427d0-119">In Windows 8</span></span>

1. <span data-ttu-id="427d0-120">Przejdź do **Start** ekran przez naciśnięcie klawiszy logo Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.</span><span class="sxs-lookup"><span data-stu-id="427d0-120">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="427d0-121">Na **Start** ekranu, naciśnij klawisze logo Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="427d0-121">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="427d0-122">Wybierz **wyświetlić aplikacje** ikony w dolnej części ekranu, a następnie wprowadź `V`.</span><span class="sxs-lookup"><span data-stu-id="427d0-122">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="427d0-123">Wybranie tej opcji powoduje listy, która zawiera wszystkie zainstalowane wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="427d0-123">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="427d0-124">Wybierz **wiersz polecenia dla deweloperów** (lub wiersza polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="427d0-124">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="427d0-125">W Windows 7</span><span class="sxs-lookup"><span data-stu-id="427d0-125">In Windows 7</span></span>

1. <span data-ttu-id="427d0-126">Wybierz **Start**, rozwiń węzeł **wszystkie programy**, a następnie rozwiń węzeł **programu Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="427d0-126">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="427d0-127">W zależności od wersji programu Visual Studio po zainstalowaniu wybierz **Visual Studio Tools**, **Visual Studio Command Prompt**, lub z wiersza polecenia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="427d0-127">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="427d0-128">W przypadku innych zestawów SDK zainstalowany, takich jak [zestawu Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive), może zostać wyświetlony dodatkowe wiersze polecenia dla ARM, x 86 lub x64 architektury.</span><span class="sxs-lookup"><span data-stu-id="427d0-128">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="427d0-129">W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.</span><span class="sxs-lookup"><span data-stu-id="427d0-129">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="427d0-130">Ręcznie lokalizowania plików na komputerze</span><span class="sxs-lookup"><span data-stu-id="427d0-130">Manually locate the files on your machine</span></span>

<span data-ttu-id="427d0-131">Zwykle, skróty klawiaturowe wiersz polecenia, zainstalowane są umieszczane na **Start Menu** folderu dla programu Visual Studio, takich jak narzędzia Studio 2017\Visual C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="427d0-131">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="427d0-132">Ale jeśli z jakiegoś powodu, wyszukiwanie w wierszu polecenia nie zachowa oczekiwanych rezultatów, możesz spróbować ręcznie zlokalizować skrót na swojej maszynie.</span><span class="sxs-lookup"><span data-stu-id="427d0-132">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="427d0-133">Spróbuj wyszukać nazwę pliku polecenia, takie jak *VsDevCmd.bat*, lub przejdź do folderu Tools, np. C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (ścieżka zmiany na podstawie wizualizacji Studio wersji i edycji oraz z instalacji lokalizacji).</span><span class="sxs-lookup"><span data-stu-id="427d0-133">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="427d0-134">Uruchom polecenie prompt z poziomu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="427d0-134">Run command prompt from inside Visual Studio</span></span>

<span data-ttu-id="427d0-135">W celu ułatwienia dostępu, można dodać wiersz polecenia dla deweloperów Visual Studio lub inne polecenia do **narzędzia** menu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="427d0-135">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="427d0-136">Aby udostępnić narzędzia, należy go dodać do listy zewnętrznych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="427d0-136">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="427d0-137">Poniżej przedstawiono kroki:</span><span class="sxs-lookup"><span data-stu-id="427d0-137">Here are the steps:</span></span>

1. <span data-ttu-id="427d0-138">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="427d0-138">Open Visual Studio.</span></span>

2. <span data-ttu-id="427d0-139">Wybierz **narzędzia** menu, a następnie wybierz **zewnętrznych narzędzi**.</span><span class="sxs-lookup"><span data-stu-id="427d0-139">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="427d0-140">Na **zewnętrznych narzędzi** okna dialogowego wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="427d0-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="427d0-141">Pojawi się nowy wpis.</span><span class="sxs-lookup"><span data-stu-id="427d0-141">A new entry appears.</span></span>

4. <span data-ttu-id="427d0-142">Wprowadź **tytuł** dla nowego elementu menu, takich jak `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="427d0-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="427d0-143">W **polecenia** Określ plik, który chcesz uruchomić, takich jak `%comspec%` lub `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="427d0-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="427d0-144">W **argumenty** pola, określ, gdzie można znaleźć określonego wiersza polecenia, którego chcesz użyć, takie jak `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (to polecenie uruchamia wiersz polecenia dla deweloperów jest instalowany z programem Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="427d0-144">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="427d0-145">Zmień tę wartość, zgodnie z lokalizacją wersji i edycji oraz z instalacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="427d0-145">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="427d0-146">Wybierz wartość dla **Czątkowy katalog** pola, takie jak **katalogu projektu**.</span><span class="sxs-lookup"><span data-stu-id="427d0-146">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="427d0-147">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="427d0-147">Choose the **OK** button.</span></span>

   <span data-ttu-id="427d0-148">Zostanie dodany nowy element menu, a są dostępne z wiersza polecenia z **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="427d0-148">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="427d0-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="427d0-149">See also</span></span>

- [<span data-ttu-id="427d0-150">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="427d0-150">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="427d0-151">Zarządzanie narzędziami zewnętrznymi</span><span class="sxs-lookup"><span data-stu-id="427d0-151">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
