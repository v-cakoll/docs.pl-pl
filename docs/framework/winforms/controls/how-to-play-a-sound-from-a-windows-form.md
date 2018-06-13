---
title: 'Porady: odtwarzanie dźwięku za pomocą formularza systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
ms.openlocfilehash: 853d0f78b4f6dba2dc84109270f79f4b010c27b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533523"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>Porady: odtwarzanie dźwięku za pomocą formularza systemu Windows
W tym przykładzie odtwarza dźwięk w danej ścieżce w czasie wykonywania.  
  
## <a name="example"></a>Przykład  
  
```vb  
Sub PlaySimpleSound()  
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")  
End Sub  
```  
  
```csharp  
private void playSimpleSound()  
{  
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");  
    simpleSound.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Aby zastąpić nazwę pliku `"c:\Windows\Media\chimes.wav"` z prawidłową nazwą pliku.  
  
-   (C#) Odwołanie do <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Operacje na plikach, powinna zostać ujęta w ramach obsługi bloków odpowiednich wyjątków strukturalnych.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa ścieżki jest nieprawidłowo sformułowany. Na przykład zawiera niedozwolone znaki lub jest tylko znak odstępu (<xref:System.ArgumentException> klasy).  
  
-   Ścieżka jest tylko do odczytu (<xref:System.IO.IOException> klasy).  
  
-   Nazwa ścieżki jest `null` (<xref:System.ArgumentNullException> klasy).  
  
-   Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException> klasy).  
  
-   Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException> klasy).  
  
-   Ścieżka jest tylko dwukropka ":" (<xref:System.NotSupportedException> klasy).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik `Form1.vb` nie może być plik źródłowy języka Visual Basic. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Media.SoundPlayer>  
 [Instrukcje: ładowanie dźwięku asynchronicznie w formularzu systemu Windows](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)  
 
