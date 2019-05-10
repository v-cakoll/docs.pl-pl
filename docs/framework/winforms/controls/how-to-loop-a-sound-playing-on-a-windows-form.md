---
title: 'Instrukcje: odtwarzanie zapętlonego dźwięku w formularzu systemu Windows'
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
ms.openlocfilehash: bc3cf7775f68237f8b3393f867b81fcf020e52fa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649291"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="deb47-102">Instrukcje: odtwarzanie zapętlonego dźwięku w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="deb47-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="deb47-103">Poniższy przykład kodu odtwarza dźwięk wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="deb47-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="deb47-104">Gdy kod w `stopPlayingButton_Click` programu obsługi zdarzeń uruchamia wszystkie obecnie odtwarzanie zatrzymuje dźwięku.</span><span class="sxs-lookup"><span data-stu-id="deb47-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="deb47-105">Jeśli żaden dźwięk jest odtwarzany, nic się nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="deb47-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="deb47-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="deb47-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="deb47-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="deb47-107">Compiling the Code</span></span>  
 <span data-ttu-id="deb47-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="deb47-108">This example requires:</span></span>  
  
- <span data-ttu-id="deb47-109">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="deb47-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="deb47-110">Zastąp nazwę pliku `"c:\Windows\Media\chimes.wav"` z prawidłową nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="deb47-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="deb47-111">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="deb47-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="deb47-112">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="deb47-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="deb47-113">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="deb47-113">Robust Programming</span></span>  
 <span data-ttu-id="deb47-114">Operacje na plikach powinna zostać ujęta w odpowiednie bloki obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="deb47-114">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="deb47-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="deb47-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="deb47-116">Nazwa ścieżki jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="deb47-116">The path name is malformed.</span></span> <span data-ttu-id="deb47-117">Na przykład zawiera znaki, które nie są prawidłowe, lub jest tylko spacją (<xref:System.ArgumentException> klasy).</span><span class="sxs-lookup"><span data-stu-id="deb47-117">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
- <span data-ttu-id="deb47-118">Ścieżka jest tylko do odczytu (<xref:System.IO.IOException> klasy).</span><span class="sxs-lookup"><span data-stu-id="deb47-118">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="deb47-119">Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException> klasy).</span><span class="sxs-lookup"><span data-stu-id="deb47-119">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="deb47-120">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException> klasy).</span><span class="sxs-lookup"><span data-stu-id="deb47-120">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="deb47-121">Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException> klasy).</span><span class="sxs-lookup"><span data-stu-id="deb47-121">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
- <span data-ttu-id="deb47-122">Ścieżka jest tylko dwukropek ":" (<xref:System.NotSupportedException> klasy).</span><span class="sxs-lookup"><span data-stu-id="deb47-122">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="deb47-123">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="deb47-123">.NET Framework Security</span></span>  
 <span data-ttu-id="deb47-124">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="deb47-124">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="deb47-125">Na przykład plik Form1.vb może nie być plik źródłowy w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="deb47-125">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="deb47-126">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="deb47-126">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb47-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="deb47-127">See also</span></span>

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [<span data-ttu-id="deb47-128">Instrukcje: Odtwarzanie dźwięku za pomocą formularza Windows</span><span class="sxs-lookup"><span data-stu-id="deb47-128">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="deb47-129">SoundPlayer, klasa — omówienie</span><span class="sxs-lookup"><span data-stu-id="deb47-129">SoundPlayer Class Overview</span></span>](soundplayer-class-overview.md)
