---
title: 'Instrukcje: Odczyt z plików tekstowych w wielu formatach w Visual Basic'
ms.date: 07/20/2015
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
ms.openlocfilehash: 9fa484f0a74d900bd6f0365f2ce71fd32e1422db
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623183"
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a>Instrukcje: Odczyt z plików tekstowych w wielu formatach w Visual Basic
<xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Obiekt umożliwia łatwe oraz efektywne analizowanie strukturyzowanych plików tekstowych, takie jak dzienniki. Pozwala na przetwarzanie plików w wielu formatach za pomocą `PeekChars` metodę, aby określić format każdego wiersza, ponieważ przeanalizować za pomocą pliku.  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Można przeanalizować pliku tekstowego w wielu formatach  
  
1. Dodaj plik tekstowy o nazwie testfile.txt do projektu. Dodaj następującą zawartość do pliku tekstowego.  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2. Zdefiniuj oczekiwanego formatu i format używany przy zwróci błąd. Ostatni wpis w każdej macierzy -1, w związku z tym ostatnim polu zakłada się, że o zmiennej szerokości. Dzieje się tak, gdy ostatni wpis w tablicy jest mniejsza lub równa 0.  
  
     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]  
  
3. Utwórz nową <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> obiekt, definiujący szerokości i format.  
  
     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]  
  
4. W pętli poprzez wierszy, testowanie pod kątem formatu przed przeczytaniem.  
  
     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]  
  
5. Błędy zapisu do konsoli.  
  
     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]  
  
## <a name="example"></a>Przykład  
 Oto kompletny przykład, która odczytuje z pliku `testfile.txt`.  
  
 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nie można przeanalizować wiersz w określonym formacie (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Komunikat o wyjątku Określa wiersz, powoduje wyjątek, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> właściwość jest przypisany do tekstu w wierszu.  
  
- Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
- Sytuacja częściowego zaufania, użytkownik nie ma wystarczających uprawnień dostępu do tego pliku. (<xref:System.Security.SecurityException>).  
  
- Ścieżka jest zbyt długa (<xref:System.IO.PathTooLongException>).  
  
- Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [Instrukcje: Odczyt z plików tekstowych rozdzielonych przecinkami](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Instrukcje: Odczyt z plików testowych o stałej szerokości](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
