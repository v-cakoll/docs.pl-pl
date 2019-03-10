---
title: 'Instrukcje: Ładowanie dźwięku asynchronicznie w formularzu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 8240e26ea0133aa091354d29f52d0692499d7765
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718301"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="a24a3-102">Instrukcje: Ładowanie dźwięku asynchronicznie w formularzu Windows</span><span class="sxs-lookup"><span data-stu-id="a24a3-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="a24a3-103">Poniższy przykład kodu asynchronicznego ładuje dźwięku z adresu URL i jest odtwarzany w nowym wątku.</span><span class="sxs-lookup"><span data-stu-id="a24a3-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a24a3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a24a3-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a24a3-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a24a3-105">Compiling the Code</span></span>  
 <span data-ttu-id="a24a3-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a24a3-106">This example requires:</span></span>  
  
-   <span data-ttu-id="a24a3-107">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="a24a3-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="a24a3-108">Zastąp nazwę pliku `"http://www.tailspintoys.com/sounds/stop.wav"` z prawidłową nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="a24a3-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="a24a3-109">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a24a3-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a24a3-110">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="a24a3-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a24a3-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a24a3-111">Robust Programming</span></span>  
 <span data-ttu-id="a24a3-112">Operacje na plikach powinna zostać ujęta w odpowiednie bloki obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="a24a3-112">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="a24a3-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a24a3-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a24a3-114">Nazwa ścieżki jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="a24a3-114">The path name is malformed.</span></span> <span data-ttu-id="a24a3-115">Na przykład zawiera znaki, które są nieprawidłowe lub jest tylko spacją (<xref:System.ArgumentException> klasy).</span><span class="sxs-lookup"><span data-stu-id="a24a3-115">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="a24a3-116">Ścieżka jest tylko do odczytu (<xref:System.IO.IOException> klasy).</span><span class="sxs-lookup"><span data-stu-id="a24a3-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="a24a3-117">Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException> klasy).</span><span class="sxs-lookup"><span data-stu-id="a24a3-117">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="a24a3-118">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException> klasy).</span><span class="sxs-lookup"><span data-stu-id="a24a3-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="a24a3-119">Ścieżka nie jest prawidłowa (<xref:System.IO.DirectoryNotFoundException> klasy).</span><span class="sxs-lookup"><span data-stu-id="a24a3-119">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="a24a3-120">Ścieżka jest tylko dwukropek ":" (<xref:System.NotSupportedException> klasy).</span><span class="sxs-lookup"><span data-stu-id="a24a3-120">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a24a3-121">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a24a3-121">.NET Framework Security</span></span>  
 <span data-ttu-id="a24a3-122">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="a24a3-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="a24a3-123">Na przykład plik `Form1.vb` może nie być plikiem źródłowym programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a24a3-123">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="a24a3-124">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a24a3-124">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24a3-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a24a3-125">See also</span></span>
- <xref:System.Media.SoundPlayer.LoadAsync%2A>
- <xref:System.Media.SoundPlayer.LoadCompleted>
- <xref:System.Media.SoundPlayer.Play%2A>
- [<span data-ttu-id="a24a3-126">Instrukcje: Odtwarzanie dźwięku za pomocą formularza Windows</span><span class="sxs-lookup"><span data-stu-id="a24a3-126">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
