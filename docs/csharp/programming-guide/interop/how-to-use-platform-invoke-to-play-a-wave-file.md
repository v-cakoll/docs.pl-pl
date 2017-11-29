---
title: "Porady: użycie wywołania platformy do odtwarzania pliku Wave (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d037e17ef48ebfdd5cfd860efbacf195e7b6a76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Porady: użycie wywołania platformy do odtwarzania pliku Wave (Przewodnik programowania w języku C#)
Poniższy przykład kodu C# ilustruje sposób użycia platformy wywołania usług do odtwarzania pliku wave dźwięku w systemie operacyjnym Windows.  
  
## <a name="example"></a>Przykład  
 Ten przykład kodu wykorzystuje `DllImport` do zaimportowania `winmm.dll`w `PlaySound` metody punktu wejścia jako `Form1 PlaySound()`. W przykładzie przedstawiono prosty formularza systemu Windows z przyciskiem. Kliknięcie przycisku otwiera standardowego systemu windows <xref:System.Windows.Forms.OpenFileDialog> okna dialogowego, dzięki czemu możesz otworzyć plik, aby odtworzyć. Po wybraniu pliku wave jest odtwarzany przy użyciu `PlaySound()` metody winmm. Metoda zestawu biblioteki DLL. Aby uzyskać więcej informacji o jego winmm.dll `PlaySound` metody, zobacz [przy użyciu funkcji PlaySound z plikami Audio fali](http://go.microsoft.com/fwlink/?LinkId=148553). Przeglądaj i wybierz plik z rozszerzeniem wav, a następnie kliknij **Otwórz** do odtwarzania pliku wave przy użyciu platformy wywołania. Pole tekstowe zawiera pełną ścieżkę pliku, który został wybrany.  
  
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
 Aby uzyskać więcej informacji, zobacz [zabezpieczenia programu .NET Framework](http://go.microsoft.com/fwlink/?LinkId=37122).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przegląd współdziałania](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [Przegląd współdziałania](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [Bliższe spojrzenie na platformie wywołania](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [Marshaling danych w wywołaniu platformy](../../../framework/interop/marshaling-data-with-platform-invoke.md)
