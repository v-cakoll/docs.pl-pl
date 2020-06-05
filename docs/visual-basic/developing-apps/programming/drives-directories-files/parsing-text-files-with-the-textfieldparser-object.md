---
title: Analizowanie plików tekstowych za pomocą obiektu TextFieldParser
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 7b2cb0dd39d14dd94db661cc9cbacf99edf0e778
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406680"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)

`TextFieldParser`Obiekt pozwala analizować i przetwarzać bardzo duży plik, który jest uporządkowany jako kolumny z rozdzielonymi szerokościami tekstu, takie jak pliki dziennika lub informacje o starszej bazie danych. Analizowanie pliku tekstowego za pomocą przypomina `TextFieldParser` iterację w pliku tekstowym, podczas gdy metoda Parse do wyodrębniania pól tekstu jest podobna do metod manipulowania ciągami używanymi do tokenize ciągów rozdzielanych.  
  
## <a name="parsing-different-types-of-text-files"></a>Analizowanie różnych typów plików tekstowych  

 Pliki tekstowe mogą mieć pola o różnej szerokości, rozdzielane znakami, takimi jak przecinki lub spacja tabulacji. Zdefiniuj `TextFieldType` i ogranicznik, jak w poniższym przykładzie, który używa `SetDelimiters` metody do definiowania pliku tekstowego rozdzielanego tabulatorami:  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 Inne pliki tekstowe mogą mieć stałe szerokości pól. W takich przypadkach należy zdefiniować `TextFieldType` jako `FixedWidth` i zdefiniować szerokości poszczególnych pól, jak w poniższym przykładzie. W tym przykładzie używamy `SetFieldWidths` metody do definiowania kolumn tekstu: pierwsza kolumna ma szerokość 5 znaków, a druga — 10, trzeci to 11, a czwarta jest szerokość zmiennej.  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 Po zdefiniowaniu formatu można wykonać pętlę przez plik, używając `ReadFields` metody, aby przetwarzać każdy wiersz z kolei.  
  
 Jeśli pole nie jest zgodne z określonym formatem, <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> zgłaszany jest wyjątek. Gdy takie wyjątki są zgłaszane, `ErrorLine` właściwości i `ErrorLineNumber` przechowują tekst powodujący wyjątek i numer wiersza tego tekstu.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analizowanie plików z wieloma formatami  

 `PeekChars`Metoda `TextFieldParser` obiektu może służyć do sprawdzenia każdego pola przed jego odczytaniem, co pozwala na zdefiniowanie wielu formatów dla pól i odpowiednie reagowanie. Aby uzyskać więcej informacji, zobacz [jak: odczyt z plików tekstowych w wielu formatach](how-to-read-from-text-files-with-multiple-formats.md).  
  
## <a name="see-also"></a>Zobacz też

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
