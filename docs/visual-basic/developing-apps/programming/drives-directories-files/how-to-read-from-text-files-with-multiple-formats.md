---
title: "Porady: odczyt z plików tekstowych w wielu formatach w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 12362f932561bf16412e5beb364f785778c58814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a>Porady: odczyt z plików tekstowych w wielu formatach w Visual Basic
<xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Obiektu pozwala łatwo i efektywnie przeanalizować strukturyzowanych plików tekstowych, takich jak dzienniki. Plik o wiele formatów można przetwarzać przy użyciu `PeekChars` metodę, aby określić format każdego wiersza, jak przeanalizować za pośrednictwem pliku.  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Można przeanalizować pliku tekstowego w wielu formatach  
  
1.  Dodaj plik tekstowy o nazwie plik_testowy.txt do projektu. Dodaj następującą zawartość do pliku tekstowego.  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  Zdefiniuj oczekiwanego formatu i format używany podczas jest zgłaszany błąd. Ostatni wpis w każdej macierzy wynosi -1, w związku z tym ostatnim polu zakłada się, że o zmiennej szerokości. Dzieje się tak, gdy ostatni wpis w tablicy jest mniejsza lub równa 0.  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  Utwórz nową <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> obiekt definiujący szerokości i format.  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  Pętli wiersze testowania dla formatu przed czytaniem.  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  Błędy zapisu do konsoli.  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełny przykład, służącą do odczytywania z pliku `testfile.txt`.  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nie można analizować wiersza w określonym formacie (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Komunikat o wyjątku Określa wiersz przyczyną tego wyjątku, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> właściwości jest przypisany do zawartych w wierszu tekstu.  
  
-   Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Sytuacja częściowego zaufania, użytkownik nie ma wystarczających uprawnień dostępu do tego pliku. (<xref:System.Security.SecurityException>).  
  
-   Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do dostępu do pliku (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>  
 [Porady: Odczyt z plików tekstowych rozdzielanych przecinkami](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Porady: Odczyt z plików testowych o stałej szerokości](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
