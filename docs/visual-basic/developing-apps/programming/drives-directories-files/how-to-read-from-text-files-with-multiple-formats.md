---
title: 'Jak: Odczyt z plików tekstowych w wielu formatach'
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
ms.openlocfilehash: b36c781d5f8333749d346bb8f19540f0d1bd1692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334574"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a>Jak: Odczyt z plików fext z wieloma formatami w języku Visual Basic

Obiekt <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> umożliwia łatwą i wydajną analizowanie plików tekstowych strukturalnych, takich jak dzienniki. Plik z wieloma formatami można przetworzyć przy użyciu `PeekChars` metody określania formatu każdego wiersza podczas analizowania pliku.
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Aby przeanalizować plik tekstowy z wieloma formatami

1. Dodaj plik tekstowy o nazwie *testfile.txt* do projektu. Dodaj do pliku tekstowego następującą zawartość:

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. Zdefiniuj oczekiwany format i format używany podczas zgłaszania błędu. Ostatni wpis w każdej tablicy jest -1, dlatego przyjmuje się, że ostatnie pole ma zmienną szerokość. Dzieje się tak, gdy ostatni wpis w tablicy jest mniejsza lub równa 0.

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. Utwórz <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> nowy obiekt, definiując szerokość i format.

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. Pętla przez wiersze, testowanie formatu przed odczytem.

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. Zapis błędów na konsoli.

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a>Przykład

Poniżej znajduje się pełny przykład, `testfile.txt`który odczytuje z pliku:

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a>Solidne programowanie

Następujące warunki mogą spowodować wyjątek:  
  
- Nie można przeanalizować wiersza przy<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>użyciu określonego formatu ( ). Komunikat o wyjątku określa wiersz powodujący <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> wyjątek, podczas gdy właściwość jest przypisana do tekstu zawartego w wierszu.
- Określony plik nie istnieje<xref:System.IO.FileNotFoundException>( ).
- Sytuacja częściowego zaufania, w której użytkownik nie ma wystarczających uprawnień dostępu do pliku. (<xref:System.Security.SecurityException>).
- Ścieżka jest za<xref:System.IO.PathTooLongException>długa ( ).
- Użytkownik nie ma wystarczających uprawnień dostępu<xref:System.UnauthorizedAccessException>do pliku ( ).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [Porady: odczyt z rozdzielonych przecinkami plików testowych](how-to-read-from-comma-delimited-text-files.md)
- [Porady: odczyt z plików testowych o stałej szerokości](how-to-read-from-fixed-width-text-files.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](parsing-text-files-with-the-textfieldparser-object.md)
