---
title: Odtwarzanie dźwięków
ms.date: 07/20/2015
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
ms.openlocfilehash: 416fedd011ff35d2b32d1b64932e3908a73ed14e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345521"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="eeaa0-102">Odtwarzanie dźwięków (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eeaa0-102">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="eeaa0-103">Obiekt `My.Computer.Audio` zapewnia metody odtwarzania dźwięków.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="eeaa0-104">Odtwarzanie dźwięków</span><span class="sxs-lookup"><span data-stu-id="eeaa0-104">Playing Sounds</span></span>  

 <span data-ttu-id="eeaa0-105">Odtwarzanie w tle umożliwia aplikacji wykonywanie innych kodów podczas odtwarzania dźwięku.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="eeaa0-106">Metoda `My.Computer.Audio.Play` umożliwia aplikacji Jednoczesne odtwarzanie tylko jednego dźwięku w tle; gdy aplikacja odtwarza nowy dźwięk w tle, przestaje odtwarzać poprzedni dźwięk w tle.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="eeaa0-107">Możesz również odtworzyć dźwięk i poczekać na jego zakończenie.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="eeaa0-108">W poniższym przykładzie metoda `My.Computer.Audio.Play` odtwarza dźwięk.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="eeaa0-109">Gdy `AudioPlayMode.WaitToComplete` jest określony, `My.Computer.Audio.Play` czeka na zakończenie działania dźwięku przed kontynuowaniem kodu.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="eeaa0-110">W przypadku korzystania z tego przykładu należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego. wav, który znajduje się na komputerze.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="eeaa0-111">W poniższym przykładzie metoda `My.Computer.Audio.Play` odtwarza dźwięk.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="eeaa0-112">W przypadku korzystania z tego przykładu należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy WAV o nazwie wodospad.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="eeaa0-113">Odtwarzanie dźwięków pętli</span><span class="sxs-lookup"><span data-stu-id="eeaa0-113">Playing Looping Sounds</span></span>  

 <span data-ttu-id="eeaa0-114">W poniższym przykładzie metoda `My.Computer.Audio.Play` odtwarza określony dźwięk w tle, gdy `PlayMode.BackgroundLoop` jest określony.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="eeaa0-115">W przypadku korzystania z tego przykładu należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego. wav, który znajduje się na komputerze.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="eeaa0-116">W poniższym przykładzie metoda `My.Computer.Audio.Play` odtwarza określony dźwięk w tle, gdy `PlayMode.BackgroundLoop` jest określony.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="eeaa0-117">W przypadku korzystania z tego przykładu należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy WAV o nazwie wodospad.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="eeaa0-118">Poprzedni przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="eeaa0-119">W selektorze fragmentów kodu znajduje się w **Windows Forms aplikacje > dźwięk**.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="eeaa0-120">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="eeaa0-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="eeaa0-121">Ogólnie rzecz biorąc, gdy aplikacja odtwarza dźwięk pętli, powinien ostatecznie zatrzymać dźwięk.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="eeaa0-122">Zatrzymywanie odtwarzania dźwięków w tle</span><span class="sxs-lookup"><span data-stu-id="eeaa0-122">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="eeaa0-123">Użyj metody `My.Computer.Audio.Stop`, aby zatrzymać aktualnie odtwarzane tło lub podkład dźwiękowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="eeaa0-124">Ogólnie rzecz biorąc, gdy aplikacja odtwarza dźwięk pętli, powinien zatrzymać dźwięk w pewnym momencie.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="eeaa0-125">W poniższym przykładzie jest zatrzymywany dźwięk, który jest odtwarzany w tle.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="eeaa0-126">Poprzedni przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="eeaa0-127">W selektorze fragmentów kodu znajduje się w **Windows Forms aplikacje > dźwięk**.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="eeaa0-128">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="eeaa0-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="eeaa0-129">Odtwarzanie dźwięków systemowych</span><span class="sxs-lookup"><span data-stu-id="eeaa0-129">Playing System Sounds</span></span>  

 <span data-ttu-id="eeaa0-130">Użyj metody `My.Computer.Audio.PlaySystemSound`, aby odtworzyć określony dźwięk systemu.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="eeaa0-131">Metoda `My.Computer.Audio.PlaySystemSound` przyjmuje jako parametr jeden z udostępnionych elementów członkowskich z klasy <xref:System.Media.SystemSound>.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="eeaa0-132">Dźwięk systemowy <xref:System.Media.SystemSounds.Asterisk%2A> zwykle oznacza błędy.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="eeaa0-133">W poniższym przykładzie zastosowano metodę `My.Computer.Audio.PlaySystemSound`, aby odtworzyć dźwięk systemowy.</span><span class="sxs-lookup"><span data-stu-id="eeaa0-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="eeaa0-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eeaa0-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
