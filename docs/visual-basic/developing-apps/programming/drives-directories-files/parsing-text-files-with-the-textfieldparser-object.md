---
title: Analizowanie plików tekstowych za pomocą obiektu TextFieldParser
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: f3239184beb58312a8e3598545fc37423ff85287
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333845"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)

Obiekt `TextFieldParser` pozwala analizować i przetwarzać bardzo duży plik, który jest uporządkowany jako kolumny z rozdzielonymi szerokościami tekstu, takie jak pliki dziennika lub informacje o starszej bazie danych. Analizowanie pliku tekstowego za pomocą `TextFieldParser` jest podobne do iterowania w pliku tekstowym, podczas gdy metoda Parse do wyodrębniania pól tekstowych jest podobna do metod manipulowania ciągami służącymi do tokenize ciągów znaków.  
  
## <a name="parsing-different-types-of-text-files"></a>Analizowanie różnych typów plików tekstowych  

 Pliki tekstowe mogą mieć pola o różnej szerokości, rozdzielane znakami, takimi jak przecinki lub spacja tabulacji. Zdefiniuj `TextFieldType` i ogranicznik, jak w poniższym przykładzie, który używa metody `SetDelimiters` do definiowania pliku tekstowego rozdzielanego tabulatorami:  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 Inne pliki tekstowe mogą mieć stałe szerokości pól. W takich przypadkach należy zdefiniować `TextFieldType` jako `FixedWidth` i zdefiniować szerokości poszczególnych pól, jak w poniższym przykładzie. W poniższym przykładzie zastosowano metodę `SetFieldWidths`, aby zdefiniować kolumny tekstu: pierwsza kolumna ma szerokość 5 znaków, a druga — 10, trzeci to 11, a czwarta jest szerokość zmiennej.  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 Po zdefiniowaniu formatu można wykonać pętlę w pliku przy użyciu metody `ReadFields`, aby przetwarzać każdy wiersz z kolei.  
  
 Jeśli pole nie jest zgodne z określonym formatem, zostanie zgłoszony wyjątek <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>. Gdy takie wyjątki są zgłaszane, właściwości `ErrorLine` i `ErrorLineNumber` przechowują tekst powodujący wyjątek i numer wiersza tego tekstu.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analizowanie plików z wieloma formatami  

 Metoda `PeekChars` obiektu `TextFieldParser` może być użyta do sprawdzenia każdego pola przed jego odczytaniem, co pozwala na zdefiniowanie wielu formatów dla pól i odpowiednie reagowanie. Aby uzyskać więcej informacji, zobacz [jak: odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>
