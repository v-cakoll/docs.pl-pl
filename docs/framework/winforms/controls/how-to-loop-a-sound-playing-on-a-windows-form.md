---
title: 'Porady: odtwarzanie dźwięku w pętli w formularzu systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: 67e1f8abe6872358a29ab8f6734b58c1c1bc809c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533760"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="08063-102">Porady: odtwarzanie dźwięku w pętli w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="08063-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="08063-103">Poniższy przykład kodu odtwarza dźwięk wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="08063-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="08063-104">Gdy kod w `stopPlayingButton_Click` uruchamia program obsługi zdarzeń, wszystkie obecnie odtwarzanie zatrzymuje dźwięku.</span><span class="sxs-lookup"><span data-stu-id="08063-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="08063-105">Jeśli żaden dźwięk jest odtwarzany, nic się nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="08063-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08063-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="08063-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="08063-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="08063-107">Compiling the Code</span></span>  
 <span data-ttu-id="08063-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="08063-108">This example requires:</span></span>  
  
-   <span data-ttu-id="08063-109">Odwołania do zestawów systemu i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="08063-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="08063-110">Aby zastąpić nazwę pliku `"c:\Windows\Media\chimes.wav"` z prawidłową nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="08063-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="08063-111">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="08063-111">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="08063-112">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="08063-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="08063-113">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="08063-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="08063-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="08063-114">Robust Programming</span></span>  
 <span data-ttu-id="08063-115">Operacje na plikach, powinna zostać ujęta w odpowiednie bloki obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="08063-115">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="08063-116">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="08063-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="08063-117">Nazwa ścieżki jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="08063-117">The path name is malformed.</span></span> <span data-ttu-id="08063-118">Na przykład zawiera znaki, które nie są prawidłowe, lub jest tylko znak odstępu (<xref:System.ArgumentException> klasy).</span><span class="sxs-lookup"><span data-stu-id="08063-118">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="08063-119">Ścieżka jest tylko do odczytu (<xref:System.IO.IOException> klasy).</span><span class="sxs-lookup"><span data-stu-id="08063-119">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="08063-120">Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException> klasy).</span><span class="sxs-lookup"><span data-stu-id="08063-120">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="08063-121">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException> klasy).</span><span class="sxs-lookup"><span data-stu-id="08063-121">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="08063-122">Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException> klasy).</span><span class="sxs-lookup"><span data-stu-id="08063-122">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="08063-123">Ścieżka jest tylko dwukropka ":" (<xref:System.NotSupportedException> klasy).</span><span class="sxs-lookup"><span data-stu-id="08063-123">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="08063-124">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="08063-124">.NET Framework Security</span></span>  
 <span data-ttu-id="08063-125">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="08063-125">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="08063-126">Na przykład plik Form1.vb nie może być plik źródłowy języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="08063-126">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="08063-127">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08063-127">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08063-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08063-128">See Also</span></span>  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [<span data-ttu-id="08063-129">Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="08063-129">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="08063-130">SoundPlayer, klasa — omówienie</span><span class="sxs-lookup"><span data-stu-id="08063-130">SoundPlayer Class Overview</span></span>](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
