---
title: "Odtwarzanie dźwięków (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8be5cec634482bf99ddff4ff6b6af8e897c4909e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="5170c-102">Odtwarzanie dźwięków (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5170c-102">Playing Sounds (Visual Basic)</span></span>
<span data-ttu-id="5170c-103">`My.Computer.Audio` Obiektu zapewnia metody odtwarzanie dźwięków.</span><span class="sxs-lookup"><span data-stu-id="5170c-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="5170c-104">Odtwarzanie dźwięków</span><span class="sxs-lookup"><span data-stu-id="5170c-104">Playing Sounds</span></span>  
 <span data-ttu-id="5170c-105">Odtwarzanie tła umożliwia aplikacji wykonanie innych kodu podczas odtwarzania dźwięku.</span><span class="sxs-lookup"><span data-stu-id="5170c-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="5170c-106">`My.Computer.Audio.Play` Metody umożliwia aplikacji Odtwórz tylko jedno tło dźwięk w czasie; gdy aplikacja odtwarza dźwięk nowe tło, zatrzymuje odtwarzanie dźwięku poprzedniej tła.</span><span class="sxs-lookup"><span data-stu-id="5170c-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="5170c-107">Można także odtwarzanie dźwięku i poczekaj na jej zakończenie.</span><span class="sxs-lookup"><span data-stu-id="5170c-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="5170c-108">W poniższym przykładzie `My.Computer.Audio.Play` metody odtwarza dźwięk.</span><span class="sxs-lookup"><span data-stu-id="5170c-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="5170c-109">Gdy `AudioPlayMode.WaitToComplete` jest określony, `My.Computer.Audio.Play` czeka, aż do zakończenia dźwięk, przed kontynuowaniem wywołanie kodu.</span><span class="sxs-lookup"><span data-stu-id="5170c-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="5170c-110">Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego .wav znajduje się na komputerze</span><span class="sxs-lookup"><span data-stu-id="5170c-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 <span data-ttu-id="5170c-111">W poniższym przykładzie `My.Computer.Audio.Play` metody odtwarza dźwięk.</span><span class="sxs-lookup"><span data-stu-id="5170c-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="5170c-112">Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy wav o nazwie wykresu kaskadowego.</span><span class="sxs-lookup"><span data-stu-id="5170c-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="5170c-113">Odtwarzanie dźwięków pętli</span><span class="sxs-lookup"><span data-stu-id="5170c-113">Playing Looping Sounds</span></span>  
 <span data-ttu-id="5170c-114">W poniższym przykładzie `My.Computer.Audio.Play` metody odtwarza dźwięk określony w tle podczas `PlayMode.BackgroundLoop` jest określona.</span><span class="sxs-lookup"><span data-stu-id="5170c-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="5170c-115">Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego .wav znajduje się na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5170c-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 <span data-ttu-id="5170c-116">W poniższym przykładzie `My.Computer.Audio.Play` metody odtwarza dźwięk określony w tle podczas `PlayMode.BackgroundLoop` jest określona.</span><span class="sxs-lookup"><span data-stu-id="5170c-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="5170c-117">Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy wav o nazwie wykresu kaskadowego.</span><span class="sxs-lookup"><span data-stu-id="5170c-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 <span data-ttu-id="5170c-118">W poprzednim przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5170c-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="5170c-119">Selektor wstawek kodu, znajduje się się w **aplikacjach formularzy systemu Windows > dźwięk**.</span><span class="sxs-lookup"><span data-stu-id="5170c-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="5170c-120">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="5170c-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="5170c-121">Ogólnie rzecz biorąc gdy aplikacja odtwarza zapętlony dźwięk, powinien po pewnym czasie zatrzymał dźwięku.</span><span class="sxs-lookup"><span data-stu-id="5170c-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="5170c-122">Zatrzymuje odtwarzanie dźwięków w tle</span><span class="sxs-lookup"><span data-stu-id="5170c-122">Stopping the Playing of Sounds in the Background</span></span>  
 <span data-ttu-id="5170c-123">Użyj `My.Computer.Audio.Stop` metodę, aby zatrzymać aplikacji aktualnie odtwarzanie tło lub odtwarzanie dźwięku w pętli.</span><span class="sxs-lookup"><span data-stu-id="5170c-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="5170c-124">Ogólnie rzecz biorąc gdy aplikacja odtwarza zapętlony dźwięk, należy zatrzymać dźwięk w pewnym momencie.</span><span class="sxs-lookup"><span data-stu-id="5170c-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="5170c-125">Poniższy przykład powoduje zatrzymanie dźwięk jest odtwarzany w tle.</span><span class="sxs-lookup"><span data-stu-id="5170c-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 <span data-ttu-id="5170c-126">W poprzednim przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5170c-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="5170c-127">Selektor wstawek kodu, znajduje się się w **aplikacjach formularzy systemu Windows > dźwięk**.</span><span class="sxs-lookup"><span data-stu-id="5170c-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="5170c-128">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="5170c-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="5170c-129">Odtwarzanie dźwięków systemu</span><span class="sxs-lookup"><span data-stu-id="5170c-129">Playing System Sounds</span></span>  
 <span data-ttu-id="5170c-130">Użyj `My.Computer.Audio.PlaySystemSound` metodę, aby odtwarzać dźwięk do określonego systemu.</span><span class="sxs-lookup"><span data-stu-id="5170c-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="5170c-131">`My.Computer.Audio.PlaySystemSound` Metoda przyjmuje jako parametr jedną udostępniane elementy członkowskie z <xref:System.Media.SystemSound> klasy.</span><span class="sxs-lookup"><span data-stu-id="5170c-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="5170c-132">Dźwięku systemowego <xref:System.Media.SystemSounds.Asterisk%2A> zazwyczaj oznacza błędy.</span><span class="sxs-lookup"><span data-stu-id="5170c-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="5170c-133">W poniższym przykładzie użyto `My.Computer.Audio.PlaySystemSound` metodę, aby odtwarzać dźwięk systemu.</span><span class="sxs-lookup"><span data-stu-id="5170c-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5170c-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5170c-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Audio>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>  
 <xref:Microsoft.VisualBasic.AudioPlayMode>
