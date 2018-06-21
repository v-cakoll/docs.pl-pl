---
title: Wiersz polecenia dla programu Visual Studio deweloperów
ms.date: 06/18/2018
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
ms.openlocfilehash: 7e91822f172de8700b04847541c4b80010a22b53
ms.sourcegitcommit: 3d42e1d73e21c35c540dd4adbea23efcbe1b8b0a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270490"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="d2bcf-102">Wiersz polecenia dla programu Visual Studio deweloperów</span><span class="sxs-lookup"><span data-stu-id="d2bcf-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="d2bcf-103">Wiersz polecenia dla programu Visual Studio deweloperów automatycznie ustawia zmienne środowiskowe, które pozwalają łatwo za pomocą narzędzia .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="d2bcf-104">Wiersz polecenia dewelopera jest instalowany z full lub społeczności wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="d2bcf-105">Nie jest on instalowany w wersjach Express programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-105">It isn't installed with the Express versions of Visual Studio.</span></span>

> [!div class="button"]
[<span data-ttu-id="d2bcf-106">Pobierz program Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d2bcf-106">Download Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="d2bcf-107">Wyszukiwanie w wierszu polecenia na komputerze</span><span class="sxs-lookup"><span data-stu-id="d2bcf-107">Searching for the Command Prompt on your machine</span></span>

<span data-ttu-id="d2bcf-108">Może pojawić się wiele wierszy polecenia, w zależności od wersji programu Visual Studio i wszelkie dodatkowe zestawy SDK został zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-108">You may see many command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="d2bcf-109">Na przykład 64-bitowe wersje programu Visual Studio oferują 32-bitowy i 64-bitowy wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-109">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="d2bcf-110">(Wersje 32-bitowe i 64-bitowe Większość narzędzi są takie same; jednak kilka narzędzi zmiany określonego środowiska 32-bitowe i 64-bitowe). Jeśli nie działają następujące kroki, możesz spróbować [ręcznie lokalizowanie plików na tym komputerze](#manually-locating-the-files-on-your-machine) lub [polecenia monitu w programie Visual Studio](#running-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="d2bcf-110">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locating the files on your machine](#manually-locating-the-files-on-your-machine) or [Running command prompt from inside Visual Studio](#running-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="d2bcf-111">W systemie Windows 10</span><span class="sxs-lookup"><span data-stu-id="d2bcf-111">In Windows 10</span></span>

1. <span data-ttu-id="d2bcf-112">W polu wyszukiwania na pasku zadań, rozpocznij wpisywanie nazwy narzędzia, takie jak `dev` lub `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-112">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="d2bcf-113">Dzięki temu udostępniają listę zainstalowanych aplikacji, spełniających kryteria wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-113">This brings a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="d2bcf-114">Jeśli szukasz innego wiersza polecenia, spróbuj wprowadzić inny wyszukiwany termin, takich jak `prompt`.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="d2bcf-115">Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="d2bcf-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="d2bcf-116">W Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d2bcf-116">In Windows 8.1</span></span>

1. <span data-ttu-id="d2bcf-117">Przejdź do **Start** ekran, naciskając klawisz z logo systemu Windows ![logo systemu Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="d2bcf-118">Na **Start** ekranu, naciśnij klawisz `CTRL + TAB` otworzyć **aplikacje** listy, a następnie wprowadź `V`.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="d2bcf-119">Wybranie tej opcji powoduje listy, która zawiera wszystkie zainstalowane wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-119">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="d2bcf-120">Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="d2bcf-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="d2bcf-121">W systemie Windows 8</span><span class="sxs-lookup"><span data-stu-id="d2bcf-121">In Windows 8</span></span>

1. <span data-ttu-id="d2bcf-122">Przejdź do **Start** ekran, naciskając klawisz z logo systemu Windows ![logo systemu Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="d2bcf-123">Na **Start** ekranu, naciśnij klawisz z logo systemu Windows ![logo systemu Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-123">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="d2bcf-124">Wybierz **wyświetlić aplikacje** ikony w dolnej części ekranu, a następnie wprowadź `V`.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="d2bcf-125">Wybranie tej opcji powoduje listy, która zawiera wszystkie zainstalowane wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-125">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="d2bcf-126">Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="d2bcf-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="d2bcf-127">W systemie Windows 7</span><span class="sxs-lookup"><span data-stu-id="d2bcf-127">In Windows 7</span></span>

1. <span data-ttu-id="d2bcf-128">Wybierz **Start**, rozwiń węzeł **wszystkie programy**, a następnie rozwiń węzeł **programu Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="d2bcf-129">W zależności od wersji programu Visual Studio po zainstalowaniu, wybierz **programu Visual Studio Tools**, **wiersz polecenia programu Visual Studio**, lub w wierszu polecenia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-129">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="d2bcf-130">Jeśli masz inne zainstalowano zestaw SDK usługi takie jak [zestawu Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive) zainstalowany, może zostać wyświetlony dodatkowe polecenie monituje o ARM, x 86 lub x64 architektury.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-130">If you have other SDKs installed such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="d2bcf-131">W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="d2bcf-132">Ręcznie lokalizowanie plików na tym komputerze</span><span class="sxs-lookup"><span data-stu-id="d2bcf-132">Manually locating the files on your machine</span></span>

<span data-ttu-id="d2bcf-133">Zwykle, skróty klawiaturowe polecenie monituje o zainstalowaniu są umieszczane na **Start Menu** folderu dla programu Visual Studio, taki jak C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual w Studio Tools.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-133">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="d2bcf-134">Ale jeśli z jakiegoś powodu wyszukiwanie w wierszu polecenia nie zachowa oczekiwanych rezultatów, możesz spróbować ręcznie zlokalizować skrót na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-134">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="d2bcf-135">Spróbuj wyszukiwania dla nazwy pliku wiersza polecenia, takich jak *VsDevCmd.bat*, lub przejdź do folderu narzędzi takich jak C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (ścieżka zmian zgodnie z Visual Studio wersji, wersji i instalacji lokalizacji).</span><span class="sxs-lookup"><span data-stu-id="d2bcf-135">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="d2bcf-136">Uruchomienie polecenia monitu w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d2bcf-136">Running command prompt from inside Visual Studio</span></span>

<span data-ttu-id="d2bcf-137">W celu ułatwienia dostępu można dodać wiersz polecenia dewelopera programu Visual Studio lub innych poleceń do menu Narzędzia w programie Visual Studio przez dodanie go do listy narzędzi zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="d2bcf-138">Jest to, jak można wykonać który:</span><span class="sxs-lookup"><span data-stu-id="d2bcf-138">This is how you can accomplish that:</span></span>

1. <span data-ttu-id="d2bcf-139">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-139">Open Visual Studio.</span></span>

2. <span data-ttu-id="d2bcf-140">Wybierz **narzędzia** menu i wybierz polecenie **zewnętrznych narzędzi**.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-140">Select the **Tools** menu and choose **External Tools**.</span></span>

3. <span data-ttu-id="d2bcf-141">Na **zewnętrznych narzędzi** oknie dialogowym wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="d2bcf-142">Zostanie wyświetlony nowy wpis.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-142">A new entry appears.</span></span>

4. <span data-ttu-id="d2bcf-143">Wprowadź **tytuł** dla nowego elementu menu, takich jak `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="d2bcf-144">W **polecenia** Określ plik, który chcesz uruchomić, takich jak `%comspec%` lub `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="d2bcf-145">W **argumenty** Określ, gdzie można znaleźć określonego wiersza polecenia, którego chcesz użyć, takich jak `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (to polecenie uruchamia Developer wierszu polecenia, który jest instalowany z programu Visual Studio Enterprise 2017).</span><span class="sxs-lookup"><span data-stu-id="d2bcf-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="d2bcf-146">Zmień tę wartość w zależności od lokalizacji wersji, wersji i instalacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="d2bcf-147">Wybierz wartość dla **katalog początkowy** pola, takie jak **katalogu projektu**.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-147">Choose a value for the **Initial directory** field such as **Project Directory**.</span></span>

8. <span data-ttu-id="d2bcf-148">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-148">Choose the **OK** button.</span></span>

<span data-ttu-id="d2bcf-149">Po wykonaniu tej zostanie dodany nowy element menu i może uzyskać dostępu do wiersza polecenia z **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="d2bcf-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2bcf-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2bcf-150">See also</span></span>

 [<span data-ttu-id="d2bcf-151">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="d2bcf-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="d2bcf-152">Zarządzanie narzędziami zewnętrznymi</span><span class="sxs-lookup"><span data-stu-id="d2bcf-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)  
