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
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a>Jak używać wywołania platformy do odtwarzania pliku WAV (Przewodnik programowania C#)

Poniższy przykład kodu C# ilustruje sposób używania usług wywoływania platformy do odtwarzania pliku dźwiękowego WAV w systemie operacyjnym Windows.

## <a name="example"></a>Przykład

Ten przykładowy <xref:System.Runtime.InteropServices.DllImportAttribute> kod `winmm.dll`służy `PlaySound` do importowania 's punkt wejścia metody jako `Form1 PlaySound()`. Przykład ma prosty formularz systemu Windows z przyciskiem. Kliknięcie przycisku powoduje otwarcie <xref:System.Windows.Forms.OpenFileDialog> standardowego okna dialogowego systemu Windows, dzięki czemu można otworzyć plik do odtworzenia. Po wybraniu pliku grupy czynności jest odtwarzany przy użyciu `PlaySound()` metody biblioteki *winmm.dll.* Aby uzyskać więcej informacji na temat tej metody, zobacz [Korzystanie z funkcji PlaySound z funkcjami Waveform-Audio .](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files) Przejrzyj i wybierz plik z rozszerzeniem .wav, a następnie kliknij przycisk **Otwórz,** aby odtworzyć plik grupy czynności, używając wywołania platformy. Pole tekstowe zawiera pełną ścieżkę zaznaczonego pliku.

Okno dialogowe **Otwieranie plików** jest filtrowane w celu wyświetlenia tylko plików z rozszerzeniem .wav za pomocą ustawień filtru:

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

1. Utwórz nowy projekt aplikacji formularzy systemu Windows w programie Visual Studio i nawadom go o **nazwie WinSound**.

2. Skopiuj powyższy kod i wklej go nad zawartością *pliku Form1.cs.*

3. Skopiuj następujący kod i *Form1.Designer.cs* wklej go `InitializeComponent()` w pliku Form1.Designer.cs w metodzie po istniejącym kodzie.

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. Skompiluj i uruchom kod.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Przegląd współdziałania](interoperability-overview.md)
- [Bliższe spojrzenie na platformy Invoke](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Organizowanie danych w wywołaniu platformy](../../../framework/interop/marshaling-data-with-platform-invoke.md)
