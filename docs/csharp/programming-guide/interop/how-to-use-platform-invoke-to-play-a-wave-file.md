---
title: 'Instrukcje: Użyj wywołania platformy, aby odtworzyć Przewodnik C# programowania plików Wave'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: cf8415b2d501ae2394fa76170eb232da33c3e308
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589100"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="ae17d-102">Instrukcje: Użyj wywołania platformy do odtwarzania pliku Wave (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="ae17d-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="ae17d-103">Poniższy C# przykład kodu ilustruje sposób używania usług wywołania platformy do odtwarzania pliku dźwiękowego Wave w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="ae17d-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae17d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae17d-104">Example</span></span>  
 <span data-ttu-id="ae17d-105">Ten przykładowy kod używa `DllImport` do `PlaySound` importowania `winmm.dll`punktu wejścia metody jako `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="ae17d-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="ae17d-106">Przykład ma prosty formularz systemu Windows z przyciskiem.</span><span class="sxs-lookup"><span data-stu-id="ae17d-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="ae17d-107">Kliknięcie tego przycisku powoduje otwarcie standardowego okna <xref:System.Windows.Forms.OpenFileDialog> dialogowego systemu Windows, w którym można otworzyć plik do odtworzenia.</span><span class="sxs-lookup"><span data-stu-id="ae17d-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="ae17d-108">Po wybraniu pliku Wave jest on odtwarzany przy użyciu `PlaySound()` metody `winmm.dll` biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ae17d-108">When a wave file is selected, it is played by using the `PlaySound()` method of the `winmm.dll` library.</span></span> <span data-ttu-id="ae17d-109">Aby uzyskać więcej informacji na temat tej metody, zobacz [Używanie funkcji PlaySound z plikami Wave-audio](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="ae17d-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="ae17d-110">Przeglądaj i wybierz plik z rozszerzeniem WAV, a następnie kliknij przycisk **Otwórz** , aby odtworzyć plik Wave przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="ae17d-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="ae17d-111">Pole tekstowe zawiera pełną ścieżkę wybranego pliku.</span><span class="sxs-lookup"><span data-stu-id="ae17d-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="ae17d-112">Okno dialogowe **otwieranie plików** jest filtrowane w celu wyświetlania tylko plików o rozszerzeniu WAV z wykorzystaniem ustawień filtru:</span><span class="sxs-lookup"><span data-stu-id="ae17d-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]  
  
 [!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae17d-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ae17d-113">Compiling the Code</span></span>  
  
1. <span data-ttu-id="ae17d-114">Utwórz nowy C# projekt aplikacji systemu Windows w programie Visual Studio i nadaj mu nazwę **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="ae17d-114">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2. <span data-ttu-id="ae17d-115">Skopiuj powyższy kod i wklej go na zawartość `Form1.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="ae17d-115">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3. <span data-ttu-id="ae17d-116">Skopiuj poniższy kod i wklej go w `Form1.Designer.cs` pliku, `InitializeComponent()` w metodzie po dowolnym istniejącym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ae17d-116">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]  
  
4. <span data-ttu-id="ae17d-117">Kompiluj i uruchamiaj kod.</span><span class="sxs-lookup"><span data-stu-id="ae17d-117">Compile and run the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae17d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae17d-118">See also</span></span>

- [<span data-ttu-id="ae17d-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ae17d-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ae17d-120">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="ae17d-120">Interoperability Overview</span></span>](./interoperability-overview.md)
- [<span data-ttu-id="ae17d-121">Bliższe spojrzenie na wywołanie platformy</span><span class="sxs-lookup"><span data-stu-id="ae17d-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="ae17d-122">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="ae17d-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
