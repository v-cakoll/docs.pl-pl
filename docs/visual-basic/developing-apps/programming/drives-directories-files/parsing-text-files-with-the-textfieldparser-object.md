---
title: Analizowanie plików tekstowych za pomocą obiektu TextFieldParser
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: f3239184beb58312a8e3598545fc37423ff85287
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333845"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)

Obiekt `TextFieldParser` umożliwia analizowanie i przetwarzanie bardzo dużych plików, które są skonstruowane jako kolumny o rozdzielanej szerokości tekstu, takie jak pliki dziennika lub informacje o starszej bazie danych. Analizowanie pliku tekstowego `TextFieldParser` z jest podobny do iteracji nad plikiem tekstowym, podczas gdy metoda analizy wyodrębnić pola tekstu jest podobna do metod manipulowania ciągami używanych do tokenizacji ciągów rozdzielanych.  
  
## <a name="parsing-different-types-of-text-files"></a>Analizowanie różnych typów plików tekstowych  

 Pliki tekstowe mogą mieć pola o różnej szerokości, rozdzielone znakiem, takim jak przecinek lub miejsce na tabulatorze. Zdefiniuj `TextFieldType` i ogranicznik, jak w `SetDelimiters` poniższym przykładzie, który używa metody do definiowania pliku tekstowego rozdzielanego tabulatora:  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 Inne pliki tekstowe mogą mieć szerokości pól, które są stałe. W takich przypadkach należy `TextFieldType` zdefiniować `FixedWidth` as i zdefiniować szerokości każdego pola, jak w poniższym przykładzie. W tym przykładzie użyto `SetFieldWidths` metody do definiowania kolumn tekstu: pierwsza kolumna ma szerokość 5 znaków, druga to 10, trzecia 11, a czwarta ma zmienną szerokość.  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 Po zdefiniowaniu formatu można zapętlać `ReadFields` plik, używając metody przetwarzania każdego wiersza po kolei.  
  
 Jeśli pole nie jest zgodne z <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> określonym formatem, zgłaszany jest wyjątek. Gdy takie wyjątki są `ErrorLine` `ErrorLineNumber` zgłaszane, i właściwości przechowywania tekstu powodując wyjątek i numer wiersza tego tekstu.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analizowanie plików w wielu formatach  

 Metoda `PeekChars` `TextFieldParser` obiektu może służyć do sprawdzania każdego pola przed jego odczytem, co pozwala na zdefiniowanie wielu formatów pól i odpowiednie reagowanie. Aby uzyskać więcej informacji, zobacz [Jak: Odczyt z plików tekstowych z wieloma formatami](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
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
