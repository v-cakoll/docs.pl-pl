---
title: 'Instrukcje: Odczyt z plików tekstowych w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: ad581d00a2499a94b9737ac69e724ea06a57ae59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582581"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Instrukcje: Odczyt z plików tekstowych w języku Visual Basic
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> Metody `My.Computer.FileSystem` obiektu umożliwia odczytywanie z pliku tekstowego. Kodowanie pliku może być określone, jeśli zawartość pliku używa kodowania, takiego jak ASCII lub UTF-8.  
  
 Podczas odczytu z pliku używającego znaków rozszerzonych, trzeba będzie określić kodowanie pliku.  
  
> [!NOTE]
>  Aby odczytać plik pojedynczy wiersz tekstu w czasie, należy użyć <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metody `My.Computer.FileSystem` obiektu. `OpenTextFileReader` Metoda zwraca <xref:System.IO.StreamReader> obiektu. Możesz użyć <xref:System.IO.StreamReader.ReadLine%2A> metody `StreamReader` obiektu do odczytania jeden wiersz pliku naraz. Możesz przetestować na końcu pliku, przy użyciu <xref:System.IO.StreamReader.EndOfStream%2A> metody `StreamReader` obiektu.  
  
### <a name="to-read-from-a-text-file"></a>Aby odczytać z pliku tekstowego  
  
-   Użyj `ReadAllText` metody `My.Computer.FileSystem` obiektu, aby odczytać zawartość pliku tekstowego na ciąg znaków, podając ścieżkę. Poniższy przykład odczytuje zawartość test.txt jako ciąg i wyświetla go w oknie komunikatu.  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a>Aby odczytać z pliku tekstowego, który jest kodowany  
  
-   Użyj `ReadAllText` metody `My.Computer.FileSystem` obiekt, aby odczytać zawartość pliku tekstowego na ciąg znaków, podając ścieżkę i typ kodowania pliku. Poniższy przykład odczytuje zawartość pliku z kodowaniem UTF32 test.txt jako ciąg i wyświetla go w oknie komunikatu.  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Plik nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Plik jest używany przez inny proces lub wystąpi błąd We/Wy (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
-   Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Nie ma wystarczającej ilości pamięci, aby zapisać ciąg do bufora (<xref:System.OutOfMemoryException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być plik źródłowy w języku Visual Basic.  
  
 Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Instrukcje: Odczyt z plików tekstowych rozdzielonych przecinkami](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Instrukcje: Odczyt z plików testowych o stałej szerokości](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Instrukcje: Odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Przewodnik: Manipulowanie plikami i katalogami w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Kodowanie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
