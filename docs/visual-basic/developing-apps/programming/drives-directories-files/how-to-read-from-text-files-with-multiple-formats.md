---
title: 'Instrukcje: odczyt z plików tekstowych z wieloma formatami'
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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334574"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a>Instrukcje: odczyt z plików fext z wieloma formatami w Visual Basic

Obiekt <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> umożliwia łatwe i wydajne analizowanie strukturalnych plików tekstowych, takich jak dzienniki. Można przetworzyć plik z wieloma formatami przy użyciu metody `PeekChars`, aby określić format każdego wiersza podczas analizowania pliku.
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Aby przeanalizować plik tekstowy z wieloma formatami

1. Dodaj plik tekstowy o nazwie *TestFile. txt* do projektu. Dodaj następującą zawartość do pliku tekstowego:

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. Zdefiniuj oczekiwany format i format używany, gdy zostanie zgłoszony błąd. Ostatni wpis w każdej tablicy to-1, w związku z czym przyjmuje się, że ostatnie pole ma szerokość zmiennej. Dzieje się tak, gdy ostatni wpis w tablicy jest mniejszy lub równy 0.

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. Utwórz nowy obiekt <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>, definiując szerokość i format.

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. Przechodzenie między wierszami, testowanie formatu przed odczytem.

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. Zapisuj błędy w konsoli.

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a>Przykład

Oto kompletny przykład, który odczytuje z pliku `testfile.txt`:

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą spowodować wyjątek:  
  
- Nie można przeanalizować wiersza przy użyciu określonego formatu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Komunikat o wyjątku określa wiersz powodujący wyjątek, podczas gdy właściwość <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> jest przypisana do tekstu zawartego w wierszu.
- Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).
- Sytuacja częściowej relacji zaufania, w której użytkownik nie ma wystarczających uprawnień dostępu do pliku. (<xref:System.Security.SecurityException>).
- Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).
- Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [Instrukcje: odczyt z rozdzielonych przecinkami plików testowych](how-to-read-from-comma-delimited-text-files.md)
- [Instrukcje: odczyt z plików testowych o stałej szerokości](how-to-read-from-fixed-width-text-files.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](parsing-text-files-with-the-textfieldparser-object.md)
