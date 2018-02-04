---
title: "Porady: użycie wywołania platformy do odtwarzania pliku Wave (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 10c2490255565de872396a0155bb588f9d696b24
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="48c21-102">Porady: użycie wywołania platformy do odtwarzania pliku Wave (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="48c21-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="48c21-103">Poniższy przykład kodu C# ilustruje sposób użycia platformy wywołania usług do odtwarzania pliku wave dźwięku w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="48c21-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48c21-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="48c21-104">Example</span></span>  
 <span data-ttu-id="48c21-105">Ten przykład kodu wykorzystuje `DllImport` do zaimportowania `winmm.dll`w `PlaySound` metody punktu wejścia jako `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="48c21-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="48c21-106">W przykładzie przedstawiono prosty formularza systemu Windows z przyciskiem.</span><span class="sxs-lookup"><span data-stu-id="48c21-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="48c21-107">Kliknięcie przycisku otwiera standardowego systemu windows <xref:System.Windows.Forms.OpenFileDialog> okna dialogowego, dzięki czemu możesz otworzyć plik, aby odtworzyć.</span><span class="sxs-lookup"><span data-stu-id="48c21-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="48c21-108">Po wybraniu pliku wave jest odtwarzany przy użyciu `PlaySound()` metody winmm. Metoda zestawu biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="48c21-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="48c21-109">Aby uzyskać więcej informacji o jego winmm.dll `PlaySound` metody, zobacz [przy użyciu funkcji PlaySound z plikami Audio fali](https://msdn.microsoft.com/library/aa910379.aspx).</span><span class="sxs-lookup"><span data-stu-id="48c21-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](https://msdn.microsoft.com/library/aa910379.aspx).</span></span> <span data-ttu-id="48c21-110">Przeglądaj i wybierz plik z rozszerzeniem wav, a następnie kliknij **Otwórz** do odtwarzania pliku wave przy użyciu platformy wywołania.</span><span class="sxs-lookup"><span data-stu-id="48c21-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="48c21-111">Pole tekstowe zawiera pełną ścieżkę pliku, który został wybrany.</span><span class="sxs-lookup"><span data-stu-id="48c21-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="48c21-112">**Otwartych plików** okno dialogowe jest filtrowana w celu wyświetlania tylko pliki mające rozszerzenie wav za pomocą ustawień filtru:</span><span class="sxs-lookup"><span data-stu-id="48c21-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="48c21-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="48c21-113">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="48c21-114">Aby skompilować kod</span><span class="sxs-lookup"><span data-stu-id="48c21-114">To compile the code</span></span>  
  
1.  <span data-ttu-id="48c21-115">Utwórz nowy projekt aplikacji systemu Windows w języku C# w programie Visual Studio i nadaj mu nazwę **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="48c21-115">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="48c21-116">Skopiuj powyższy kod i wklej go za pośrednictwem zawartość `Form1.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="48c21-116">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="48c21-117">Skopiuj poniższy kod i wklej go w `Form1.Designer.cs` pliku w `InitializeComponent()` metody po istniejący kod.</span><span class="sxs-lookup"><span data-stu-id="48c21-117">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  <span data-ttu-id="48c21-118">Kompilowanie i uruchamianie kodu.</span><span class="sxs-lookup"><span data-stu-id="48c21-118">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="48c21-119">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="48c21-119">.NET Framework Security</span></span>  
 <span data-ttu-id="48c21-120">Aby uzyskać więcej informacji, zobacz [zabezpieczenia programu .NET Framework](https://technet.microsoft.com/en-us/security/).</span><span class="sxs-lookup"><span data-stu-id="48c21-120">For more information, see [.NET Framework Security](https://technet.microsoft.com/en-us/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c21-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48c21-121">See Also</span></span>  
 [<span data-ttu-id="48c21-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="48c21-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="48c21-123">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="48c21-123">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [<span data-ttu-id="48c21-124">Bliższe spojrzenie na platformie wywołania</span><span class="sxs-lookup"><span data-stu-id="48c21-124">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
 [<span data-ttu-id="48c21-125">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="48c21-125">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
