---
title: "Porady: odczyt z plików testowych w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f75d89fb4ab10a8c116d4a0ab79c17ceb3efd0ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Porady: odczyt z plików testowych w Visual Basic
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> Metody `My.Computer.FileSystem` obiektu służy do odczytu z pliku tekstowego. Kodowanie pliku może być określone, jeśli zawartość pliku używa kodowania, takiego jak ASCII lub UTF-8.  
  
 Podczas odczytu z pliku używającego znaków rozszerzonych, trzeba będzie określić kodowanie pliku.  
  
> [!NOTE]
>  Aby odczytać plik pojedynczy wiersz tekstu w czasie, należy użyć <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metody `My.Computer.FileSystem` obiektu. `OpenTextFileReader` Metoda zwraca <xref:System.IO.StreamReader> obiektu. Można użyć <xref:System.IO.StreamReader.ReadLine%2A> metody `StreamReader` obiektu do odczytania jeden wiersz pliku naraz. Możesz przetestować końca pliku przy użyciu <xref:System.IO.StreamReader.EndOfStream%2A> metody `StreamReader` obiektu.  
  
### <a name="to-read-from-a-text-file"></a>Aby odczytać z pliku tekstowego  
  
-   Użyj `ReadAllText` metody `My.Computer.FileSystem` obiektu można odczytać zawartości pliku tekstowego na ciąg, podając ścieżkę. Poniższy przykład odczytuje zawartość test.txt jako ciąg i wyświetla go w oknie komunikatu.  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a>Aby odczytać z pliku tekstowego, który jest kodowany  
  
-   Użyj `ReadAllText` metody `My.Computer.FileSystem` obiekt, aby przeczytać jego zawartość pliku tekstowego na ciąg, podając ścieżkę i typ kodowania pliku. Poniższy przykład odczytuje zawartość pliku z kodowaniem UTF32 test.txt jako ciąg i wyświetla go w oknie komunikatu.  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Plik nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Plik jest używany przez inny proces lub błąd We/Wy (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Nie ma wystarczającej ilości pamięci do zapisania ciągu do buforu (<xref:System.OutOfMemoryException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pliku źródłowego.  
  
 Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>  
 [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Porady: Odczyt z plików tekstowych rozdzielanych przecinkami](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Porady: Odczyt z plików testowych o stałej szerokości](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [Porady: Odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [Wskazówki: Manipulowanie plikami i katalogami w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [Kodowanie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
