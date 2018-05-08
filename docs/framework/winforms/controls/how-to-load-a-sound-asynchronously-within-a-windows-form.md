---
title: 'Porady: ładowanie dźwięku asynchronicznie w formularzu systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 9ebede03a3a9d2cc6db1cda2537bcaf30afcb2d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a>Porady: ładowanie dźwięku asynchronicznie w formularzu systemu Windows
Poniższy przykład kodu asynchronicznie ładuje dźwięk z adresu URL i jest odtwarzany na nowego wątku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu i System.Windows.Forms.  
  
-   Aby zastąpić nazwę pliku `"http://www.tailspintoys.com/sounds/stop.wav"` z prawidłową nazwą pliku.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Operacje na plikach, powinna zostać ujęta w odpowiednie bloki obsługi wyjątków.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa ścieżki jest nieprawidłowo sformułowany. Na przykład zawiera znaki, które są nieprawidłowe lub jest tylko znak odstępu (<xref:System.ArgumentException> klasy).  
  
-   Ścieżka jest tylko do odczytu (<xref:System.IO.IOException> klasy).  
  
-   Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException> klasy).  
  
-   Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException> klasy).  
  
-   Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException> klasy).  
  
-   Ścieżka jest tylko dwukropka ":" (<xref:System.NotSupportedException> klasy).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik `Form1.vb` nie może być plik źródłowy języka Visual Basic. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <xref:System.Media.SoundPlayer.LoadCompleted>  
 <xref:System.Media.SoundPlayer.Play%2A>  
 [Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
