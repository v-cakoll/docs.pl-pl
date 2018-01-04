---
title: "Wiersz polecenia dla programu Visual Studio deweloperów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8bd7baec77e6e776f93a2a13156d66c1199f918
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="76bf4-102">Wiersz polecenia dla programu Visual Studio deweloperów</span><span class="sxs-lookup"><span data-stu-id="76bf4-102">Developer Command Prompt for Visual Studio</span></span>
<span data-ttu-id="76bf4-103">Wiersz polecenia dla programu Visual Studio deweloperów automatycznie ustawia zmienne środowiskowe, które pozwalają łatwo za pomocą narzędzia .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76bf4-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="76bf4-104">Wiersz polecenia dewelopera jest instalowany z full lub społeczności wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76bf4-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="76bf4-105">Nie jest instalowany z wersji Express programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76bf4-105">It is not installed with the Express versions of Visual Studio.</span></span>  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="76bf4-106">Wyszukiwanie w wierszu polecenia na komputerze</span><span class="sxs-lookup"><span data-stu-id="76bf4-106">Searching for the Command Prompt on your machine</span></span>  
 <span data-ttu-id="76bf4-107">Może pojawić się wiele wierszy polecenia, w zależności od wersji programu Visual Studio i wszelkie dodatkowe zestawy SDK został zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="76bf4-107">You may see multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="76bf4-108">Na przykład 64-bitowe wersje programu Visual Studio oferują 32-bitowy i 64-bitowy wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="76bf4-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="76bf4-109">(32-bitowe i 64-bitowe wersje większości narzędzi są identyczne, ale niektóre narzędzia wprowadzają zmiany specyficzne dla środowisk 32-bitowych i 64-bitowych). Jeśli Poniższa procedura nie działa, możesz spróbować [ręcznie lokalizowanie plików na tym komputerze](#alternative) lub [polecenia monitu w programie Visual Studio](#visualstudio).</span><span class="sxs-lookup"><span data-stu-id="76bf4-109">(The 32-bit and 64-bit versions of most tools are identical; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the steps below don't work, you can try [Manually locating the files on your machine](#alternative) or [Running command prompt from inside Visual Studio](#visualstudio).</span></span>  
  
 <span data-ttu-id="76bf4-110">**W systemie Windows 10**</span><span class="sxs-lookup"><span data-stu-id="76bf4-110">**In Windows 10**</span></span>  
  
1.  <span data-ttu-id="76bf4-111">Otwórz **Start** menu, naciskając klawisz z logo systemu Windows ![logo systemu Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.</span><span class="sxs-lookup"><span data-stu-id="76bf4-111">Open the **Start** menu, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="76bf4-112">Na **Start** menu, wprowadź `dev`.</span><span class="sxs-lookup"><span data-stu-id="76bf4-112">On the **Start** menu, enter `dev`.</span></span> <span data-ttu-id="76bf4-113">Zostanie wyświetlone listę zainstalowanych aplikacji, spełniających kryteria wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="76bf4-113">This will bring a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="76bf4-114">Jeśli szukasz innego wiersza polecenia, spróbuj wprowadzić inny wyszukiwany termin, takich jak `prompt`.</span><span class="sxs-lookup"><span data-stu-id="76bf4-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>  
  
3.  <span data-ttu-id="76bf4-115">Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="76bf4-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="76bf4-116">**W Windows 8.1**</span><span class="sxs-lookup"><span data-stu-id="76bf4-116">**In Windows 8.1**</span></span>  
  
1.  <span data-ttu-id="76bf4-117">Przejdź do **Start** ekran, naciskając klawisz z logo systemu Windows ![logo systemu Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.</span><span class="sxs-lookup"><span data-stu-id="76bf4-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="76bf4-118">Na **Start** ekranu, naciśnij klawisz `CTRL + TAB` otworzyć **aplikacje** listy, a następnie wprowadź `V`.</span><span class="sxs-lookup"><span data-stu-id="76bf4-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="76bf4-119">Zostanie wyświetlone na liście zawierającej wszystkie zainstalowane wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76bf4-119">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
3.  <span data-ttu-id="76bf4-120">Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="76bf4-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="76bf4-121">**W systemie Windows 8**</span><span class="sxs-lookup"><span data-stu-id="76bf4-121">**In Windows 8**</span></span>  
  
1.  <span data-ttu-id="76bf4-122">Przejdź do **Start** ekran, naciskając klawisz z logo systemu Windows ![logo systemu Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.</span><span class="sxs-lookup"><span data-stu-id="76bf4-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="76bf4-123">Na **Start** ekranu, naciśnij klawisz z logo systemu Windows ![logo systemu Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="76bf4-123">On the **Start** screen, press the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>  
  
3.  <span data-ttu-id="76bf4-124">Wybierz **wyświetlić aplikacje** ikony w dolnej części ekranu, a następnie wprowadź `V`.</span><span class="sxs-lookup"><span data-stu-id="76bf4-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="76bf4-125">Zostanie wyświetlone na liście zawierającej wszystkie zainstalowane wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76bf4-125">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
4.  <span data-ttu-id="76bf4-126">Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).</span><span class="sxs-lookup"><span data-stu-id="76bf4-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="76bf4-127">**W systemie Windows 7**</span><span class="sxs-lookup"><span data-stu-id="76bf4-127">**In Windows 7**</span></span>  
  
1.  <span data-ttu-id="76bf4-128">Wybierz **Start**, rozwiń węzeł **wszystkie programy**, a następnie rozwiń węzeł **programu Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="76bf4-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="76bf4-129">W zależności od wersji programu Visual Studio został zainstalowany, należy wybrać **programu Visual Studio Tools**, **wiersz polecenia programu Visual Studio**, lub w wierszu polecenia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="76bf4-129">Depending on the version of Visual Studio you have installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>  
  
 <span data-ttu-id="76bf4-130">Jeśli masz [zestaw Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) lub [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) zainstalowany, może zostać wyświetlony dodatkowe polecenie monituje o ARM, x 86 lub x64 architektury.</span><span class="sxs-lookup"><span data-stu-id="76bf4-130">If you have the [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) or [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="76bf4-131">W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.</span><span class="sxs-lookup"><span data-stu-id="76bf4-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="76bf4-132">Ręcznie lokalizowanie plików na tym komputerze</span><span class="sxs-lookup"><span data-stu-id="76bf4-132">Manually locating the files on your machine</span></span>  
  <span data-ttu-id="76bf4-133">Zwykle, skróty klawiaturowe polecenie monituje o zainstalowaniu zostaną umieszczone w **Start Menu** folderu dla programu Visual Studio, taki jak C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Narzędzia.</span><span class="sxs-lookup"><span data-stu-id="76bf4-133">Usually, the shortcuts for the command prompts you have installed will be placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools.</span></span>    <span data-ttu-id="76bf4-134">Jednak jeśli zaistnieje, wyszukiwanie w wierszu polecenia nie oczekiwanych rezultatów, możesz spróbować ręcznie zlokalizować skrót na komputerze, aby można było go używać.</span><span class="sxs-lookup"><span data-stu-id="76bf4-134">But if for some reason, searching for the command prompt doesn't yield the expected results, you can try to manually locate the shortcut on your machine in order to use it.</span></span>   <span data-ttu-id="76bf4-135">Spróbuj wyszukiwania dla nazwy pliku wiersza polecenia, takich jak VsDevCmd.bat lub przejdź do folderu narzędzi, takich jak C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\Tools (ścieżka zmieni się zgodnie z lokalizacją wersji i instalacji programu Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="76bf4-135">Try searching for the name of the command prompt file such as VsDevCmd.bat or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools (path will change according to your Visual Studio version and installation location).</span></span>  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="76bf4-136">Uruchomienie polecenia monitu w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76bf4-136">Running command prompt from inside Visual Studio</span></span>  
 <span data-ttu-id="76bf4-137">W celu ułatwienia dostępu można dodać wiersz polecenia dewelopera programu Visual Studio lub innych poleceń do menu Narzędzia w programie Visual Studio przez dodanie go do listy narzędzi zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="76bf4-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="76bf4-138">Jest to, jak można wykonać który:</span><span class="sxs-lookup"><span data-stu-id="76bf4-138">This is how you can accomplish that:</span></span>  
  
1.  <span data-ttu-id="76bf4-139">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76bf4-139">Open Visual Studio.</span></span>  
  
2.  <span data-ttu-id="76bf4-140">Wybierz **narzędzia** menu i wybierz polecenie **zewnętrznych narzędzi...** .</span><span class="sxs-lookup"><span data-stu-id="76bf4-140">Select the **Tools** menu and choose **External Tools...**.</span></span>  
  
3.  <span data-ttu-id="76bf4-141">Na **zewnętrznych narzędzi** oknie dialogowym wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="76bf4-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="76bf4-142">Pojawi się nowy wpis</span><span class="sxs-lookup"><span data-stu-id="76bf4-142">A new entry appears</span></span>  
  
4.  <span data-ttu-id="76bf4-143">Wprowadź **tytuł** dla nowego elementu menu, takich jak `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="76bf4-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>  
  
5.  <span data-ttu-id="76bf4-144">W **polecenia** Określ plik, który chcesz uruchomić, takich jak `%comspec%` lub `C:\Windows\System32\cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="76bf4-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe` .</span></span>  
  
6.  <span data-ttu-id="76bf4-145">W **argumenty** Określ, gdzie można znaleźć określonego wiersza polecenia, którego chcesz użyć, takich jak `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (spowoduje to uruchomienie zainstalowany z wiersza polecenia dewelopera [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="76bf4-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (this will launch the Developer Command Prompt installed with [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span></span> <span data-ttu-id="76bf4-146">Ta wartość musi zostać zmienione w zależności od lokalizacji wersji i instalacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76bf4-146">This value needs to be changed according to your Visual Studio version and installation location.</span></span>  
  
7.  <span data-ttu-id="76bf4-147">Wybierz wartość dla **katalog początkowy** pola, takie jak **katalogu projektu** .</span><span class="sxs-lookup"><span data-stu-id="76bf4-147">Choose a value for the **Initial directory** field such as **Project Directory** .</span></span>  
  
8.  <span data-ttu-id="76bf4-148">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="76bf4-148">Choose the **OK** button.</span></span>  
  
 <span data-ttu-id="76bf4-149">Po wykonaniu tej zostanie dodany nowy element menu i może uzyskać dostępu do wiersza polecenia z **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="76bf4-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76bf4-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76bf4-150">See Also</span></span>  
 [<span data-ttu-id="76bf4-151">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="76bf4-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="76bf4-152">Zarządzanie narzędziami zewnętrznymi</span><span class="sxs-lookup"><span data-stu-id="76bf4-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
