---
title: 'Instrukcje: Odtwarzanie w formularzu Windows dźwięku w pętli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: 238d269f9c3d3b2612eab70341200221c5b43d3a
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260923"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a>Instrukcje: Odtwarzanie w formularzu Windows dźwięku w pętli
Poniższy przykład kodu odtwarza dźwięk wielokrotnie. Gdy kod w `stopPlayingButton_Click` programu obsługi zdarzeń uruchamia wszystkie obecnie odtwarzanie zatrzymuje dźwięku. Jeśli żaden dźwięk jest odtwarzany, nic się nie dzieje.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.  
  
-   Zastąp nazwę pliku `"c:\Windows\Media\chimes.wav"` z prawidłową nazwą pliku.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Operacje na plikach powinna zostać ujęta w odpowiednie bloki obsługi wyjątków.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa ścieżki jest nieprawidłowo sformułowany. Na przykład zawiera znaki, które nie są prawidłowe, lub jest tylko spacją (<xref:System.ArgumentException> klasy).  
  
-   Ścieżka jest tylko do odczytu (<xref:System.IO.IOException> klasy).  
  
-   Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException> klasy).  
  
-   Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException> klasy).  
  
-   Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException> klasy).  
  
-   Ścieżka jest tylko dwukropek ":" (<xref:System.NotSupportedException> klasy).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być plik źródłowy w języku Visual Basic. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [Instrukcje: Odtwarzanie dźwięku za pomocą formularza Windows](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
- [SoundPlayer, klasa — omówienie](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
