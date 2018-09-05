---
title: 'Porady: ładowanie dźwięku asynchronicznie w formularzu systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 2de2be478e81183201cc85e1a6dfd6f1a1833af6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538613"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="41dff-102">Porady: ładowanie dźwięku asynchronicznie w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="41dff-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="41dff-103">Poniższy przykład kodu asynchronicznego ładuje dźwięku z adresu URL i jest odtwarzany w nowym wątku.</span><span class="sxs-lookup"><span data-stu-id="41dff-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41dff-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="41dff-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41dff-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="41dff-105">Compiling the Code</span></span>  
 <span data-ttu-id="41dff-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="41dff-106">This example requires:</span></span>  
  
-   <span data-ttu-id="41dff-107">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="41dff-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="41dff-108">Zastąp nazwę pliku `"http://www.tailspintoys.com/sounds/stop.wav"` z prawidłową nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="41dff-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="41dff-109">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="41dff-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="41dff-110">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="41dff-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="41dff-111">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="41dff-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="41dff-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="41dff-112">Robust Programming</span></span>  
 <span data-ttu-id="41dff-113">Operacje na plikach powinna zostać ujęta w odpowiednie bloki obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="41dff-113">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="41dff-114">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="41dff-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="41dff-115">Nazwa ścieżki jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="41dff-115">The path name is malformed.</span></span> <span data-ttu-id="41dff-116">Na przykład zawiera znaki, które są nieprawidłowe lub jest tylko spacją (<xref:System.ArgumentException> klasy).</span><span class="sxs-lookup"><span data-stu-id="41dff-116">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="41dff-117">Ścieżka jest tylko do odczytu (<xref:System.IO.IOException> klasy).</span><span class="sxs-lookup"><span data-stu-id="41dff-117">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="41dff-118">Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException> klasy).</span><span class="sxs-lookup"><span data-stu-id="41dff-118">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="41dff-119">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException> klasy).</span><span class="sxs-lookup"><span data-stu-id="41dff-119">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="41dff-120">Ścieżka nie jest prawidłowa (<xref:System.IO.DirectoryNotFoundException> klasy).</span><span class="sxs-lookup"><span data-stu-id="41dff-120">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="41dff-121">Ścieżka jest tylko dwukropek ":" (<xref:System.NotSupportedException> klasy).</span><span class="sxs-lookup"><span data-stu-id="41dff-121">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="41dff-122">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="41dff-122">.NET Framework Security</span></span>  
 <span data-ttu-id="41dff-123">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="41dff-123">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="41dff-124">Na przykład plik `Form1.vb` może nie być plikiem źródłowym programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="41dff-124">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="41dff-125">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41dff-125">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41dff-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41dff-126">See Also</span></span>  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <xref:System.Media.SoundPlayer.LoadCompleted>  
 <xref:System.Media.SoundPlayer.Play%2A>  
 [<span data-ttu-id="41dff-127">Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="41dff-127">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
