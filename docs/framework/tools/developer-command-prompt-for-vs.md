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
ms.openlocfilehash: 20dc7caa9e4c3e023bf2848b1dd8c63a9b94a01b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696758"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="71424-102">Wiersz polecenia programisty dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71424-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="71424-103">Wiersz polecenia dla deweloperów programu Visual Studio pozwala łatwiej używać narzędzi programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71424-103">The Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="71424-104">Jest automatycznie ustawia zmienne środowiskowe określonego wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="71424-104">It is a command prompt that automatically sets specific environment variables.</span></span>

> [!div class="button"]
[<span data-ttu-id="71424-105">Pobierz program Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71424-105">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="71424-106">Wyszukaj wiersz polecenia na komputerze</span><span class="sxs-lookup"><span data-stu-id="71424-106">Search for the command prompt on your machine</span></span>

<span data-ttu-id="71424-107">Może mieć kilka wierszy polecenia, w zależności od wersji programu Visual Studio oraz wszelkie dodatkowe zainstalowanych zestawów SDK.</span><span class="sxs-lookup"><span data-stu-id="71424-107">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="71424-108">Na przykład 64-bitowe wersje programu Visual Studio oferują 32-bitowy i 64-bitowy wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="71424-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="71424-109">(32-bitowych i 64-bitowe wersje większości narzędzi są takie same; jednak niektóre narzędzia wprowadzają zmiany specyficzne dla środowisk 32-bitowych i 64-bitowych). Jeśli poniższe kroki nie zadziałają, spróbuj [ręcznie zlokalizować plikami na komputerze](#manually-locate-the-files-on-your-machine) lub [Uruchom wiersz polecenia z poziomu programu Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="71424-109">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [Run the command prompt from inside Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="71424-110">W systemie Windows 10</span><span class="sxs-lookup"><span data-stu-id="71424-110">In Windows 10</span></span>

1. <span data-ttu-id="71424-111">W polu wyszukiwania na pasku zadań, należy uruchomić, wpisując nazwę narzędzia, takie jak `dev` lub `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="71424-111">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="71424-112">Wyświetlenie listy zainstalowanych aplikacji spełniających kryteria wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="71424-112">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="71424-113">Jeśli potrzebujesz innego wiersza polecenia, spróbuj wprowadzić różne wyszukiwany termin takich jak `prompt`.</span><span class="sxs-lookup"><span data-stu-id="71424-113">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="71424-114">Wybierz **wiersz polecenia dla deweloperów** (lub wiersza polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="71424-114">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="71424-115">W Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="71424-115">In Windows 8.1</span></span>

1. <span data-ttu-id="71424-116">Przejdź do **Start** ekran przez naciśnięcie klawiszy logo Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.</span><span class="sxs-lookup"><span data-stu-id="71424-116">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="71424-117">Na **Start** ekranu, naciśnij klawisz **Ctrl**+**kartę** otworzyć **aplikacje** listy, a następnie wprowadź `V`.</span><span class="sxs-lookup"><span data-stu-id="71424-117">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then enter `V`.</span></span> <span data-ttu-id="71424-118">Wybranie tej opcji powoduje listy, która zawiera wszystkie zainstalowane wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71424-118">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="71424-119">Wybierz **wiersz polecenia dla deweloperów** (lub wiersza polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="71424-119">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="71424-120">W systemie Windows 8</span><span class="sxs-lookup"><span data-stu-id="71424-120">In Windows 8</span></span>

1. <span data-ttu-id="71424-121">Przejdź do **Start** ekran przez naciśnięcie klawiszy logo Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.</span><span class="sxs-lookup"><span data-stu-id="71424-121">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="71424-122">Na **Start** ekranu, naciśnij klawisze logo Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="71424-122">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="71424-123">Wybierz **wyświetlić aplikacje** ikony w dolnej części ekranu, a następnie wprowadź `V`.</span><span class="sxs-lookup"><span data-stu-id="71424-123">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="71424-124">Wybranie tej opcji powoduje listy, która zawiera wszystkie zainstalowane wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71424-124">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="71424-125">Wybierz **wiersz polecenia dla deweloperów** (lub wiersza polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="71424-125">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="71424-126">W Windows 7</span><span class="sxs-lookup"><span data-stu-id="71424-126">In Windows 7</span></span>

1. <span data-ttu-id="71424-127">Wybierz **Start**, rozwiń węzeł **wszystkie programy**, a następnie rozwiń węzeł **programu Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="71424-127">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="71424-128">W zależności od wersji programu Visual Studio po zainstalowaniu wybierz **Visual Studio Tools**, **Visual Studio Command Prompt**, lub z wiersza polecenia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="71424-128">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="71424-129">W przypadku innych zestawów SDK zainstalowany, takich jak [zestawu Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive), może zostać wyświetlony dodatkowe wiersze polecenia dla ARM, x 86 lub x64 architektury.</span><span class="sxs-lookup"><span data-stu-id="71424-129">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="71424-130">W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.</span><span class="sxs-lookup"><span data-stu-id="71424-130">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="71424-131">Ręcznie lokalizowania plików na komputerze</span><span class="sxs-lookup"><span data-stu-id="71424-131">Manually locate the files on your machine</span></span>

<span data-ttu-id="71424-132">Zwykle, skróty klawiaturowe wiersz polecenia, zainstalowane są umieszczane na **Start Menu** folderu dla programu Visual Studio, takich jak narzędzia Studio 2017\Visual C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71424-132">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="71424-133">Ale jeśli z jakiegoś powodu, wyszukiwanie w wierszu polecenia nie zachowa oczekiwanych rezultatów, możesz spróbować ręcznie zlokalizować skrót na swojej maszynie.</span><span class="sxs-lookup"><span data-stu-id="71424-133">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="71424-134">Spróbuj wyszukać nazwę pliku polecenia, takie jak *VsDevCmd.bat*, lub przejdź do folderu Tools, np. C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (ścieżka zmiany na podstawie wizualizacji Studio wersji i edycji oraz z instalacji lokalizacji).</span><span class="sxs-lookup"><span data-stu-id="71424-134">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="71424-135">Uruchom wiersz polecenia z poziomu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71424-135">Run the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="71424-136">W celu ułatwienia dostępu, można dodać wiersz polecenia dla deweloperów Visual Studio lub inne polecenia do **narzędzia** menu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71424-136">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="71424-137">Aby udostępnić narzędzia, należy go dodać do listy zewnętrznych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="71424-137">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="71424-138">Poniżej przedstawiono kroki:</span><span class="sxs-lookup"><span data-stu-id="71424-138">Here are the steps:</span></span>

1. <span data-ttu-id="71424-139">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71424-139">Open Visual Studio.</span></span>

2. <span data-ttu-id="71424-140">Wybierz **narzędzia** menu, a następnie wybierz **zewnętrznych narzędzi**.</span><span class="sxs-lookup"><span data-stu-id="71424-140">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="71424-141">Na **zewnętrznych narzędzi** okna dialogowego wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="71424-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="71424-142">Pojawi się nowy wpis.</span><span class="sxs-lookup"><span data-stu-id="71424-142">A new entry appears.</span></span>

4. <span data-ttu-id="71424-143">Wprowadź **tytuł** dla nowego elementu menu, takich jak `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="71424-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="71424-144">W **polecenia** Określ plik, który chcesz uruchomić, takich jak `%comspec%` lub `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="71424-144">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="71424-145">W **argumenty** pola, określ, gdzie można znaleźć określonego wiersza polecenia, którego chcesz użyć, takie jak `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (to polecenie uruchamia wiersz polecenia dla deweloperów jest instalowany z programem Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="71424-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="71424-146">Zmień tę wartość, zgodnie z lokalizacją wersji i edycji oraz z instalacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71424-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="71424-147">Wybierz wartość dla **Czątkowy katalog** pola, takie jak **katalogu projektu**.</span><span class="sxs-lookup"><span data-stu-id="71424-147">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="71424-148">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="71424-148">Choose the **OK** button.</span></span>

   <span data-ttu-id="71424-149">Zostanie dodany nowy element menu, a są dostępne z wiersza polecenia z **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="71424-149">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

   ![Wiersz polecenia z menu w programie Visual Studio](media/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="71424-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71424-151">See also</span></span>

- [<span data-ttu-id="71424-152">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="71424-152">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="71424-153">Zarządzanie narzędziami zewnętrznymi</span><span class="sxs-lookup"><span data-stu-id="71424-153">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
