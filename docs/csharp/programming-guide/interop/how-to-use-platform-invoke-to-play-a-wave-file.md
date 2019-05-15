---
title: 'Instrukcje: Użycie wywołania platformy do odtwarzania pliku Wave - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 2d7f50952a485c09e74462f3ad731d710b8f9198
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584262"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="d9345-102">Instrukcje: Użycie wywołania platformy do odtwarzania pliku Wave (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="d9345-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="d9345-103">Poniższy przykład kodu C# ilustruje sposób użycia platform wywołania usług do odtwarzania pliku wave dźwięku w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="d9345-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9345-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9345-104">Example</span></span>  
 <span data-ttu-id="d9345-105">Ten przykładowy kod używa `DllImport` do zaimportowania `winmm.dll`firmy `PlaySound` metody punktu wejścia jako `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="d9345-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="d9345-106">W przykładzie przedstawiono prosty formularz Windows za pomocą przycisku.</span><span class="sxs-lookup"><span data-stu-id="d9345-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="d9345-107">Kliknięcie przycisku otwiera standardowy system windows <xref:System.Windows.Forms.OpenFileDialog> okno dialogowe, tak aby mogli otworzyć plik, aby odtworzyć.</span><span class="sxs-lookup"><span data-stu-id="d9345-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="d9345-108">Po wybraniu pliku wave jest odtwarzany za pomocą `PlaySound()` metody `winmm.dll` biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d9345-108">When a wave file is selected, it is played by using the `PlaySound()` method of the `winmm.dll` library.</span></span> <span data-ttu-id="d9345-109">Aby uzyskać więcej informacji na temat tej metody, zobacz [przy użyciu funkcji PlaySound pliki Audio fali](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="d9345-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="d9345-110">Przeglądaj i wybierz plik, który ma rozszerzenie wav, a następnie kliknij **Otwórz** do odtwarzania pliku wave przy użyciu platformy wywołania.</span><span class="sxs-lookup"><span data-stu-id="d9345-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="d9345-111">Pole tekstowe pokazuje pełną ścieżkę pliku, który został wybrany.</span><span class="sxs-lookup"><span data-stu-id="d9345-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="d9345-112">**Otwartych plików** okno dialogowe jest filtrowana w celu wyświetlenia tylko pliki mające rozszerzenie wav przy zastosowaniu ustawień filtru:</span><span class="sxs-lookup"><span data-stu-id="d9345-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]  
  
 [!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d9345-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d9345-113">Compiling the Code</span></span>  
  
1. <span data-ttu-id="d9345-114">Utwórz nowy projekt aplikacji Windows w języku C# w programie Visual Studio i nadaj mu nazwę **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="d9345-114">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2. <span data-ttu-id="d9345-115">Skopiuj kod powyżej i Wklej zawartość `Form1.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="d9345-115">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3. <span data-ttu-id="d9345-116">Skopiuj poniższy kod, a następnie wklej je `Form1.Designer.cs` pliku w `InitializeComponent()` metody, istniejący kod.</span><span class="sxs-lookup"><span data-stu-id="d9345-116">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]  
  
4. <span data-ttu-id="d9345-117">Skompiluj i uruchom kod.</span><span class="sxs-lookup"><span data-stu-id="d9345-117">Compile and run the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9345-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9345-118">See also</span></span>

- [<span data-ttu-id="d9345-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d9345-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d9345-120">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="d9345-120">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)
- [<span data-ttu-id="d9345-121">Im bliżej wywołania platformy</span><span class="sxs-lookup"><span data-stu-id="d9345-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="d9345-122">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="d9345-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
