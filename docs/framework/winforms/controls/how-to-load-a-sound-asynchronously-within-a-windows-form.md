---
title: 'Porady: ładowanie dźwięku asynchronicznie w formularzu systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ea84f03088deb7225e90150d9d298f1b64030cc6
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="523f6-102">Porady: ładowanie dźwięku asynchronicznie w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="523f6-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="523f6-103">Poniższy przykład kodu asynchronicznie ładuje dźwięk z adresu URL i jest odtwarzany na nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="523f6-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="523f6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="523f6-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="523f6-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="523f6-105">Compiling the Code</span></span>  
 <span data-ttu-id="523f6-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="523f6-106">This example requires:</span></span>  
  
-   <span data-ttu-id="523f6-107">Odwołania do zestawów systemu i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="523f6-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="523f6-108">Aby zastąpić nazwę pliku `"http://www.tailspintoys.com/sounds/stop.wav"` z prawidłową nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="523f6-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="523f6-109">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="523f6-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="523f6-110">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="523f6-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="523f6-111">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="523f6-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="523f6-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="523f6-112">Robust Programming</span></span>  
 <span data-ttu-id="523f6-113">Operacje na plikach, powinna zostać ujęta w odpowiednie bloki obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="523f6-113">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="523f6-114">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="523f6-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="523f6-115">Nazwa ścieżki jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="523f6-115">The path name is malformed.</span></span> <span data-ttu-id="523f6-116">Na przykład zawiera znaki, które są nieprawidłowe lub jest tylko znak odstępu (<xref:System.ArgumentException> klasy).</span><span class="sxs-lookup"><span data-stu-id="523f6-116">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="523f6-117">Ścieżka jest tylko do odczytu (<xref:System.IO.IOException> klasy).</span><span class="sxs-lookup"><span data-stu-id="523f6-117">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="523f6-118">Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException> klasy).</span><span class="sxs-lookup"><span data-stu-id="523f6-118">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="523f6-119">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException> klasy).</span><span class="sxs-lookup"><span data-stu-id="523f6-119">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="523f6-120">Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException> klasy).</span><span class="sxs-lookup"><span data-stu-id="523f6-120">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="523f6-121">Ścieżka jest tylko dwukropka ":" (<xref:System.NotSupportedException> klasy).</span><span class="sxs-lookup"><span data-stu-id="523f6-121">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="523f6-122">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="523f6-122">.NET Framework Security</span></span>  
 <span data-ttu-id="523f6-123">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="523f6-123">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="523f6-124">Na przykład plik `Form1.vb` nie może być plik źródłowy języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="523f6-124">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="523f6-125">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="523f6-125">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523f6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="523f6-126">See Also</span></span>  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <xref:System.Media.SoundPlayer.LoadCompleted>  
 <xref:System.Media.SoundPlayer.Play%2A>  
 [<span data-ttu-id="523f6-127">Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="523f6-127">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
