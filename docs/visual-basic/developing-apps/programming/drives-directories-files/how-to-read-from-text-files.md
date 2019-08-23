---
title: 'Instrukcje: Odczyt z plików tekstowych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: f830a0794f67c0f8f7aca24a181e323317901923
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955958"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Instrukcje: Odczyt z plików tekstowych w Visual Basic
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> Metoda`My.Computer.FileSystem` obiektu umożliwia odczytywanie z pliku tekstowego. Kodowanie pliku może być określone, jeśli zawartość pliku używa kodowania, takiego jak ASCII lub UTF-8.  
  
 Podczas odczytu z pliku używającego znaków rozszerzonych, trzeba będzie określić kodowanie pliku.  
  
> [!NOTE]
> Aby odczytać plik pojedynczy wiersz tekstu, użyj <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metody `My.Computer.FileSystem` obiektu. `OpenTextFileReader` Metoda<xref:System.IO.StreamReader> zwraca obiekt. Można użyć <xref:System.IO.StreamReader.ReadLine%2A> metody `StreamReader` obiektu, aby odczytać plik jeden wiersz jednocześnie. Można testować pod kątem końca pliku przy użyciu <xref:System.IO.StreamReader.EndOfStream%2A> metody `StreamReader` obiektu.  
  
### <a name="to-read-from-a-text-file"></a>Aby odczytać z pliku tekstowego  
  
- `ReadAllText` Użyj metody `My.Computer.FileSystem` obiektu, aby odczytać zawartość pliku tekstowego w ciągu, dostarczając ścieżkę. Poniższy przykład odczytuje zawartość test.txt jako ciąg i wyświetla go w oknie komunikatu.  
  
     [!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a>Aby odczytać z pliku tekstowego, który jest kodowany  
  
- `ReadAllText` Użyj metody `My.Computer.FileSystem` obiektu, aby odczytać zawartość pliku tekstowego w ciągu, podając ścieżkę i typ kodowania pliku. Poniższy przykład odczytuje zawartość pliku z kodowaniem UTF32 test.txt jako ciąg i wyświetla go w oknie komunikatu.  
  
     [!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).  
  
- Plik nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
- Plik jest używany przez inny proces lub wystąpił błąd we/wy (<xref:System.IO.IOException>).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).  
  
- Za mało pamięci, aby zapisać ciąg do bufora (<xref:System.OutOfMemoryException>).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.  
  
 Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Instrukcje: Odczyt z rozdzielanych przecinkami plików tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Instrukcje: Odczyt z plików tekstowych o stałej szerokości](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Instrukcje: Odczyt z plików tekstowych z wieloma formatami](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Rozwiązywanie problemów: Odczytywanie z plików tekstowych i zapisywanie do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Przewodnik: Manipulowanie plikami i katalogami w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Kodowanie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
