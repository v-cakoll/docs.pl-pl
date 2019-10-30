---
title: 'Instrukcje: korzystanie z wywołania platformy do odtwarzania przewodnika po C# programowaniu plików Wave'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 6c2313f7b600bc1670c944f6a93868c1bc4c7c16
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039325"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Porady: użycie wywołania platformy do odtwarzania pliku Wave (Przewodnik programowania w języku C#)

Poniższy C# przykład kodu ilustruje sposób używania usług wywołania platformy do odtwarzania pliku dźwiękowego Wave w systemie operacyjnym Windows.

## <a name="example"></a>Przykład

Ten przykładowy kod używa <xref:System.Runtime.InteropServices.DllImportAttribute> do importowania `winmm.dll``PlaySound` punktu wejścia metody jako `Form1 PlaySound()`. Przykład ma prosty formularz systemu Windows z przyciskiem. Kliknięcie tego przycisku powoduje otwarcie standardowego okna dialogowego <xref:System.Windows.Forms.OpenFileDialog> systemu Windows, w którym można otworzyć plik do odtworzenia. Po wybraniu pliku Wave jest on odtwarzany przy użyciu metody `PlaySound()` biblioteki *winmm. dll* . Aby uzyskać więcej informacji na temat tej metody, zobacz [Używanie funkcji PlaySound z plikami Wave-audio](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). Przeglądaj i wybierz plik z rozszerzeniem WAV, a następnie kliknij przycisk **Otwórz** , aby odtworzyć plik Wave przy użyciu wywołania platformy. Pole tekstowe zawiera pełną ścieżkę wybranego pliku.

Okno dialogowe **otwieranie plików** jest filtrowane w celu wyświetlania tylko plików o rozszerzeniu WAV z wykorzystaniem ustawień filtru:

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

1. Utwórz nowy C# projekt aplikacji Windows Forms w programie Visual Studio i nadaj mu nazwę **WinSound**.

2. Skopiuj powyższy kod i wklej go do zawartości pliku *Form1.cs* .

3. Skopiuj poniższy kod i wklej go w pliku *Form1.Designer.cs* , w metodzie `InitializeComponent()` po jakimkolwiek istniejącym kodzie.

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. Kompiluj i uruchamiaj kod.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Przegląd współdziałania](interoperability-overview.md)
- [Bliższe spojrzenie na wywołanie platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Marshaling danych w wywołaniu platformy](../../../framework/interop/marshaling-data-with-platform-invoke.md)
