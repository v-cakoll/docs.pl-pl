---
title: Jak używać wywołania platformy do odtwarzania pliku WAV - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 3ea90f0739ad45c31e4f25836c9de8e708dff2cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700825"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a><span data-ttu-id="8d22f-102">Jak używać wywołania platformy do odtwarzania pliku WAV (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="8d22f-102">How to use platform invoke to play a WAV file (C# Programming Guide)</span></span>

<span data-ttu-id="8d22f-103">Poniższy przykład kodu C# ilustruje sposób używania usług wywoływania platformy do odtwarzania pliku dźwiękowego WAV w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="8d22f-103">The following C# code example illustrates how to use platform invoke services to play a WAV sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="8d22f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d22f-104">Example</span></span>

<span data-ttu-id="8d22f-105">Ten przykładowy <xref:System.Runtime.InteropServices.DllImportAttribute> kod `winmm.dll`służy `PlaySound` do importowania 's punkt wejścia metody jako `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="8d22f-105">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="8d22f-106">Przykład ma prosty formularz systemu Windows z przyciskiem.</span><span class="sxs-lookup"><span data-stu-id="8d22f-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="8d22f-107">Kliknięcie przycisku powoduje otwarcie <xref:System.Windows.Forms.OpenFileDialog> standardowego okna dialogowego systemu Windows, dzięki czemu można otworzyć plik do odtworzenia.</span><span class="sxs-lookup"><span data-stu-id="8d22f-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="8d22f-108">Po wybraniu pliku grupy czynności jest odtwarzany przy użyciu `PlaySound()` metody biblioteki *winmm.dll.*</span><span class="sxs-lookup"><span data-stu-id="8d22f-108">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="8d22f-109">Aby uzyskać więcej informacji na temat tej metody, zobacz [Korzystanie z funkcji PlaySound z funkcjami Waveform-Audio .](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files)</span><span class="sxs-lookup"><span data-stu-id="8d22f-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="8d22f-110">Przejrzyj i wybierz plik z rozszerzeniem .wav, a następnie kliknij przycisk **Otwórz,** aby odtworzyć plik grupy czynności, używając wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="8d22f-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="8d22f-111">Pole tekstowe zawiera pełną ścieżkę zaznaczonego pliku.</span><span class="sxs-lookup"><span data-stu-id="8d22f-111">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="8d22f-112">Okno dialogowe **Otwieranie plików** jest filtrowane w celu wyświetlenia tylko plików z rozszerzeniem .wav za pomocą ustawień filtru:</span><span class="sxs-lookup"><span data-stu-id="8d22f-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="8d22f-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8d22f-113">Compiling the code</span></span>

1. <span data-ttu-id="8d22f-114">Utwórz nowy projekt aplikacji formularzy systemu Windows w programie Visual Studio i nawadom go o **nazwie WinSound**.</span><span class="sxs-lookup"><span data-stu-id="8d22f-114">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="8d22f-115">Skopiuj powyższy kod i wklej go nad zawartością *pliku Form1.cs.*</span><span class="sxs-lookup"><span data-stu-id="8d22f-115">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="8d22f-116">Skopiuj następujący kod i *Form1.Designer.cs* wklej go `InitializeComponent()` w pliku Form1.Designer.cs w metodzie po istniejącym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8d22f-116">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="8d22f-117">Skompiluj i uruchom kod.</span><span class="sxs-lookup"><span data-stu-id="8d22f-117">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d22f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d22f-118">See also</span></span>

- [<span data-ttu-id="8d22f-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="8d22f-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8d22f-120">Przegląd współdziałania</span><span class="sxs-lookup"><span data-stu-id="8d22f-120">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="8d22f-121">Bliższe spojrzenie na platformy Invoke</span><span class="sxs-lookup"><span data-stu-id="8d22f-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="8d22f-122">Organizowanie danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="8d22f-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
