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
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Porady: użycie wywołania platformy do odtwarzania pliku Wave (Przewodnik programowania w języku C#)
Poniższy przykład kodu C# ilustruje sposób użycia platformy wywołania usług do odtwarzania pliku wave dźwięku w systemie operacyjnym Windows.  
  
## <a name="example"></a>Przykład  
 Ten przykład kodu wykorzystuje `DllImport` do zaimportowania `winmm.dll`w `PlaySound` metody punktu wejścia jako `Form1 PlaySound()`. W przykładzie przedstawiono prosty formularza systemu Windows z przyciskiem. Kliknięcie przycisku otwiera standardowego systemu windows <xref:System.Windows.Forms.OpenFileDialog> okna dialogowego, dzięki czemu możesz otworzyć plik, aby odtworzyć. Po wybraniu pliku wave jest odtwarzany przy użyciu `PlaySound()` metody winmm. Metoda zestawu biblioteki DLL. Aby uzyskać więcej informacji o jego winmm.dll `PlaySound` metody, zobacz [przy użyciu funkcji PlaySound z plikami Audio fali](https://msdn.microsoft.com/library/aa910379.aspx). Przeglądaj i wybierz plik z rozszerzeniem wav, a następnie kliknij **Otwórz** do odtwarzania pliku wave przy użyciu platformy wywołania. Pole tekstowe zawiera pełną ścieżkę pliku, który został wybrany.  
  
 **Otwartych plików** okno dialogowe jest filtrowana w celu wyświetlania tylko pliki mające rozszerzenie wav za pomocą ustawień filtru:  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
### <a name="to-compile-the-code"></a>Aby skompilować kod  
  
1.  Utwórz nowy projekt aplikacji systemu Windows w języku C# w programie Visual Studio i nadaj mu nazwę **WinSound**.  
  
2.  Skopiuj powyższy kod i wklej go za pośrednictwem zawartość `Form1.cs` pliku.  
  
3.  Skopiuj poniższy kod i wklej go w `Form1.Designer.cs` pliku w `InitializeComponent()` metody po istniejący kod.  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  Kompilowanie i uruchamianie kodu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uzyskać więcej informacji, zobacz [zabezpieczenia programu .NET Framework](https://technet.microsoft.com/en-us/security/).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przegląd współdziałania](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [Bliższe spojrzenie na platformie wywołania](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
 [Marshaling danych w wywołaniu platformy](../../../framework/interop/marshaling-data-with-platform-invoke.md)
