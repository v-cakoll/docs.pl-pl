---
title: 'Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows'
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
ms.openlocfilehash: 3b9eb6f902d0d2193f0099f8e868e4ead347ce26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913413"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows
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
  
- Zastąp nazwę pliku `"c:\Windows\Media\chimes.wav"` z prawidłową nazwą pliku.  
  
- (C#) Odwołanie do <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Operacje na plikach powinna zostać ujęta w odpowiednie bloki obsługi wyjątków strukturalnych.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa ścieżki jest nieprawidłowo sformułowany. Na przykład zawiera niedozwolone znaki lub jest tylko spacją (<xref:System.ArgumentException> klasy).  
  
- Ścieżka jest tylko do odczytu (<xref:System.IO.IOException> klasy).  
  
- Nazwa ścieżki jest `null` (<xref:System.ArgumentNullException> klasy).  
  
- Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException> klasy).  
  
- Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException> klasy).  
  
- Ścieżka jest tylko dwukropek, ":" (<xref:System.NotSupportedException> klasy).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik `Form1.vb` może nie być plikiem źródłowym programu Visual Basic. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Media.SoundPlayer>
- [Instrukcje: Ładowanie dźwięku asynchronicznie w formularzu Windows](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
