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
ms.openlocfilehash: 101cd6fa044e181cf6f993fbea642c9dffe04008
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236859"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="d8ca1-102">Instrukcje: Użycie wywołania platformy do odtwarzania pliku Wave (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="d8ca1-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="d8ca1-103">Poniższy przykład kodu C# ilustruje sposób użycia platform wywołania usług do odtwarzania pliku wave dźwięku w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8ca1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8ca1-104">Example</span></span>  
 <span data-ttu-id="d8ca1-105">Ten przykładowy kod używa `DllImport` do zaimportowania `winmm.dll`firmy `PlaySound` metody punktu wejścia jako `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="d8ca1-106">W przykładzie przedstawiono prosty formularz Windows za pomocą przycisku.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="d8ca1-107">Kliknięcie przycisku otwiera standardowy system windows <xref:System.Windows.Forms.OpenFileDialog> okno dialogowe, tak aby mogli otworzyć plik, aby odtworzyć.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="d8ca1-108">Po wybraniu pliku wave jest odtwarzany za pomocą `PlaySound()` metody `winmm.dll` biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-108">When a wave file is selected, it is played by using the `PlaySound()` method of the `winmm.dll` library.</span></span> <span data-ttu-id="d8ca1-109">Aby uzyskać więcej informacji na temat tej metody, zobacz [przy użyciu funkcji PlaySound pliki Audio fali](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="d8ca1-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="d8ca1-110">Przeglądaj i wybierz plik, który ma rozszerzenie wav, a następnie kliknij **Otwórz** do odtwarzania pliku wave przy użyciu platformy wywołania.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="d8ca1-111">Pole tekstowe pokazuje pełną ścieżkę pliku, który został wybrany.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="d8ca1-112">**Otwartych plików** okno dialogowe jest filtrowana w celu wyświetlenia tylko pliki mające rozszerzenie wav przy zastosowaniu ustawień filtru:</span><span class="sxs-lookup"><span data-stu-id="d8ca1-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d8ca1-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d8ca1-113">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="d8ca1-114">Aby skompilować kod</span><span class="sxs-lookup"><span data-stu-id="d8ca1-114">To compile the code</span></span>  
  
1.  <span data-ttu-id="d8ca1-115">Utwórz nowy projekt aplikacji Windows w języku C# w programie Visual Studio i nadaj mu nazwę **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-115">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="d8ca1-116">Skopiuj kod powyżej i Wklej zawartość `Form1.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-116">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="d8ca1-117">Skopiuj poniższy kod, a następnie wklej je `Form1.Designer.cs` pliku w `InitializeComponent()` metody, istniejący kod.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-117">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  <span data-ttu-id="d8ca1-118">Skompiluj i uruchom kod.</span><span class="sxs-lookup"><span data-stu-id="d8ca1-118">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d8ca1-119">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8ca1-119">.NET Framework Security</span></span>  
 <span data-ttu-id="d8ca1-120">Aby uzyskać więcej informacji, zobacz [zabezpieczeń na platformie .NET](../../../standard/security/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8ca1-120">For more information, see [Security in .NET](../../../standard/security/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ca1-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8ca1-121">See Also</span></span>

- [<span data-ttu-id="d8ca1-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d8ca1-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d8ca1-123">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="d8ca1-123">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
- [<span data-ttu-id="d8ca1-124">Im bliżej wywołania platformy</span><span class="sxs-lookup"><span data-stu-id="d8ca1-124">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
- [<span data-ttu-id="d8ca1-125">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="d8ca1-125">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
