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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345521"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="c427a-102">Odtwarzanie dźwięków (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c427a-102">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="c427a-103">Obiekt `My.Computer.Audio` udostępnia metody odtwarzania dźwięków.</span><span class="sxs-lookup"><span data-stu-id="c427a-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="c427a-104">Odtwarzanie dźwięków</span><span class="sxs-lookup"><span data-stu-id="c427a-104">Playing Sounds</span></span>  

 <span data-ttu-id="c427a-105">Odtwarzanie w tle umożliwia aplikacji wykonywanie innego kodu podczas odtwarzania dźwięku.</span><span class="sxs-lookup"><span data-stu-id="c427a-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="c427a-106">Metoda `My.Computer.Audio.Play` pozwala aplikacji odtwarzać tylko jeden dźwięk tła naraz; gdy aplikacja odtwarza nowy dźwięk tła, przestaje odtwarzać poprzedni dźwięk tła.</span><span class="sxs-lookup"><span data-stu-id="c427a-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="c427a-107">Możesz również odtworzyć dźwięk i poczekać na jego zakończenie.</span><span class="sxs-lookup"><span data-stu-id="c427a-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="c427a-108">W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk.</span><span class="sxs-lookup"><span data-stu-id="c427a-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="c427a-109">Po `AudioPlayMode.WaitToComplete` określeniu, czeka, `My.Computer.Audio.Play` aż dźwięk zostanie ukończony przed wywołaniem kodu będzie kontynuowany.</span><span class="sxs-lookup"><span data-stu-id="c427a-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="c427a-110">Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odnosi się do pliku dźwiękowego .wav znajdującego się na komputerze</span><span class="sxs-lookup"><span data-stu-id="c427a-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="c427a-111">W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk.</span><span class="sxs-lookup"><span data-stu-id="c427a-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="c427a-112">Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji zawierają plik dźwiękowy .wav o nazwie Waterfall.</span><span class="sxs-lookup"><span data-stu-id="c427a-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="c427a-113">Odtwarzanie zapętlania dźwięków</span><span class="sxs-lookup"><span data-stu-id="c427a-113">Playing Looping Sounds</span></span>  

 <span data-ttu-id="c427a-114">W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza określony dźwięk `PlayMode.BackgroundLoop` w tle, gdy jest określony.</span><span class="sxs-lookup"><span data-stu-id="c427a-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="c427a-115">Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odnosi się do pliku dźwiękowego .wav, który znajduje się na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c427a-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="c427a-116">W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza określony dźwięk `PlayMode.BackgroundLoop` w tle, gdy jest określony.</span><span class="sxs-lookup"><span data-stu-id="c427a-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="c427a-117">Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji zawierają plik dźwiękowy .wav o nazwie Waterfall.</span><span class="sxs-lookup"><span data-stu-id="c427a-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="c427a-118">W poprzednim przykładzie kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c427a-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c427a-119">W selektorze fragmentów kodu znajduje się w **aplikacji windows formularzy > dźwięku**.</span><span class="sxs-lookup"><span data-stu-id="c427a-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="c427a-120">Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c427a-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="c427a-121">Ogólnie rzecz biorąc, gdy aplikacja odtwarza dźwięk pętli, należy ostatecznie zatrzymać dźwięk.</span><span class="sxs-lookup"><span data-stu-id="c427a-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="c427a-122">Zatrzymywanie odtwarzania dźwięków w tle</span><span class="sxs-lookup"><span data-stu-id="c427a-122">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="c427a-123">Użyj `My.Computer.Audio.Stop` tej metody, aby zatrzymać aktualnie odtwarzany dźwięk tła lub pętli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c427a-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="c427a-124">Ogólnie rzecz biorąc, gdy aplikacja odtwarza dźwięk pętli, należy zatrzymać dźwięk w pewnym momencie.</span><span class="sxs-lookup"><span data-stu-id="c427a-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="c427a-125">Poniższy przykład zatrzymuje dźwięk odtwarzany w tle.</span><span class="sxs-lookup"><span data-stu-id="c427a-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="c427a-126">W poprzednim przykładzie kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c427a-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c427a-127">W selektorze fragmentów kodu znajduje się w **aplikacji windows formularzy > dźwięku**.</span><span class="sxs-lookup"><span data-stu-id="c427a-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="c427a-128">Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c427a-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="c427a-129">Odtwarzanie dźwięków systemowych</span><span class="sxs-lookup"><span data-stu-id="c427a-129">Playing System Sounds</span></span>  

 <span data-ttu-id="c427a-130">Użyj `My.Computer.Audio.PlaySystemSound` tej metody, aby odtworzyć określony dźwięk systemu.</span><span class="sxs-lookup"><span data-stu-id="c427a-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="c427a-131">Metoda `My.Computer.Audio.PlaySystemSound` przyjmuje jako parametr jeden z elementów członkowskich udostępnionych <xref:System.Media.SystemSound> z klasy.</span><span class="sxs-lookup"><span data-stu-id="c427a-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="c427a-132">Dźwięk <xref:System.Media.SystemSounds.Asterisk%2A> systemu zazwyczaj oznacza błędy.</span><span class="sxs-lookup"><span data-stu-id="c427a-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="c427a-133">W poniższym przykładzie `My.Computer.Audio.PlaySystemSound` użyto tej metody odtwarzania dźwięku systemowego.</span><span class="sxs-lookup"><span data-stu-id="c427a-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="c427a-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c427a-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
