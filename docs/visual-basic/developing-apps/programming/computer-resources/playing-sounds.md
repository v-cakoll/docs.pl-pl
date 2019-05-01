---
title: Odtwarzanie dźwięków (Visual Basic)
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
ms.openlocfilehash: ac890a4cc6024ae43af4146d1d8f43af70ae3ff0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803912"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="b39e1-102">Odtwarzanie dźwięków (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b39e1-102">Playing Sounds (Visual Basic)</span></span>
<span data-ttu-id="b39e1-103">`My.Computer.Audio` Obiekt zapewnia metody do odtwarzania dźwięku.</span><span class="sxs-lookup"><span data-stu-id="b39e1-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="b39e1-104">Odtwarzanie dźwięków</span><span class="sxs-lookup"><span data-stu-id="b39e1-104">Playing Sounds</span></span>  
 <span data-ttu-id="b39e1-105">Odtwarzanie tła umożliwia aplikacji wykonywanie innego kodu, podczas odtwarzania dźwięku.</span><span class="sxs-lookup"><span data-stu-id="b39e1-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="b39e1-106">`My.Computer.Audio.Play` Metody umożliwia aplikacji Odtwórz tylko jedno tło dźwięk w czasie; gdy aplikacja odtwarza dźwięk nowe tło, zatrzymuje odtwarzanie dźwięku poprzedniego tła.</span><span class="sxs-lookup"><span data-stu-id="b39e1-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="b39e1-107">Możesz odtwarzać dźwięk i poczekaj na jej zakończenie.</span><span class="sxs-lookup"><span data-stu-id="b39e1-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="b39e1-108">W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk.</span><span class="sxs-lookup"><span data-stu-id="b39e1-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="b39e1-109">Gdy `AudioPlayMode.WaitToComplete` jest określony, `My.Computer.Audio.Play` oczekuje na zakończenie przed kontynuowaniem wywoływanie kodu dźwięku.</span><span class="sxs-lookup"><span data-stu-id="b39e1-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="b39e1-110">Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego .wav, która znajduje się na komputerze</span><span class="sxs-lookup"><span data-stu-id="b39e1-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="b39e1-111">W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk.</span><span class="sxs-lookup"><span data-stu-id="b39e1-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="b39e1-112">Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy wav, o nazwie wykres kaskadowy.</span><span class="sxs-lookup"><span data-stu-id="b39e1-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="b39e1-113">Odtwarzanie dźwięków pętli</span><span class="sxs-lookup"><span data-stu-id="b39e1-113">Playing Looping Sounds</span></span>  
 <span data-ttu-id="b39e1-114">W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk określony w tle podczas `PlayMode.BackgroundLoop` jest określony.</span><span class="sxs-lookup"><span data-stu-id="b39e1-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="b39e1-115">Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego .wav, która znajduje się na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b39e1-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="b39e1-116">W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk określony w tle podczas `PlayMode.BackgroundLoop` jest określony.</span><span class="sxs-lookup"><span data-stu-id="b39e1-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="b39e1-117">Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy wav, o nazwie wykres kaskadowy.</span><span class="sxs-lookup"><span data-stu-id="b39e1-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="b39e1-118">W poprzednim przykładzie kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="b39e1-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="b39e1-119">W selektorze fragmentów kodu, znajduje się w **aplikacji z formularzem Windows > dźwięk**.</span><span class="sxs-lookup"><span data-stu-id="b39e1-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="b39e1-120">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="b39e1-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="b39e1-121">Ogólnie rzecz biorąc gdy aplikacja odtwarza zapętlony dźwięk, powinien po pewnym czasie zatrzymał dźwięku.</span><span class="sxs-lookup"><span data-stu-id="b39e1-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="b39e1-122">Zatrzymywanie odtwarzanie dźwięku w tle</span><span class="sxs-lookup"><span data-stu-id="b39e1-122">Stopping the Playing of Sounds in the Background</span></span>  
 <span data-ttu-id="b39e1-123">Użyj `My.Computer.Audio.Stop` metodę, aby zatrzymać aplikacji obecnie odtwarzanie w tle lub odtwarzanie dźwięku w pętli.</span><span class="sxs-lookup"><span data-stu-id="b39e1-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="b39e1-124">Ogólnie rzecz biorąc gdy aplikacja odtwarza zapętlony dźwięk, należy zatrzymać dźwięk w pewnym momencie.</span><span class="sxs-lookup"><span data-stu-id="b39e1-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="b39e1-125">Poniższy przykład powoduje zatrzymanie dźwięk jest odtwarzany w tle.</span><span class="sxs-lookup"><span data-stu-id="b39e1-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="b39e1-126">W poprzednim przykładzie kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="b39e1-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="b39e1-127">W selektorze fragmentów kodu, znajduje się w **aplikacji z formularzem Windows > dźwięk**.</span><span class="sxs-lookup"><span data-stu-id="b39e1-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="b39e1-128">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="b39e1-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="b39e1-129">Odtwarzanie dźwięków systemu</span><span class="sxs-lookup"><span data-stu-id="b39e1-129">Playing System Sounds</span></span>  
 <span data-ttu-id="b39e1-130">Użyj `My.Computer.Audio.PlaySystemSound` metodę, aby odtworzyć dźwięk określonego systemu.</span><span class="sxs-lookup"><span data-stu-id="b39e1-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="b39e1-131">`My.Computer.Audio.PlaySystemSound` Metoda przyjmuje jako parametr, jedną z udostępnionych elementów członkowskich z <xref:System.Media.SystemSound> klasy.</span><span class="sxs-lookup"><span data-stu-id="b39e1-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="b39e1-132">Dźwięku systemowego <xref:System.Media.SystemSounds.Asterisk%2A> zwykle wskazuje błędy.</span><span class="sxs-lookup"><span data-stu-id="b39e1-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="b39e1-133">W poniższym przykładzie użyto `My.Computer.Audio.PlaySystemSound` metodę, aby odtworzyć dźwięk systemu.</span><span class="sxs-lookup"><span data-stu-id="b39e1-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="b39e1-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b39e1-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
