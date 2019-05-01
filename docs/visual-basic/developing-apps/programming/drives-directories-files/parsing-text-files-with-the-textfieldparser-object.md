---
title: Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 70848e2d53ec4bdb031f73286f2c5be9a7e19387
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014105"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)
`TextFieldParser` Obiekt umożliwia analizowanie i procesu bardzo dużego pliku, który mają strukturę jako kolumn rozdzielana szerokości tekstu, takie jak pliki dziennika lub informacje o bazie danych w starszej wersji. Podczas analizowania pliku tekstowego z `TextFieldParser` przypomina Iterowanie pliku tekstowego, podczas gdy metody parse do wyodrębniania pól tekstu jest podobne do metod manipulowania ciąg do tokenizacji ciągów rozdzielanych.  
  
## <a name="parsing-different-types-of-text-files"></a>Analizy różnych typów plików tekstowych  
 Pliki tekstowe mogą mieć pola różnych szerokości, takich jak przecinek lub miejsce na karcie rozdzielane. Zdefiniuj `TextFieldType` i ogranicznik, jak w poniższym przykładzie, który używa `SetDelimiters` metodę, aby zdefiniować pliku tekstowego, rozdzielanego znakami tabulacji:  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 Inne pliki tekstowe mogą mieć szerokościami pól, które zostały usunięte. W takich przypadkach należy zdefiniować `TextFieldType` jako `FixedWidth` i zdefiniuj szerokości każdego pola, jak w poniższym przykładzie. W tym przykładzie użyto `SetFieldWidths` metody do definiowania kolumn tekstu: pierwsza kolumna jest 5 znaki dwubajtowe, drugi to 10, trzecia będzie 11 i czwarta to o zmiennej szerokości.  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 Po zdefiniowaniu format można pętli pliku przy użyciu `ReadFields` metodę, aby przetworzyć każdy wiersz z osobna.  
  
 Jeśli pole nie jest zgodny z określonym formacie <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> wyjątku. Jeśli takie wyjątki są zgłaszane, `ErrorLine` i `ErrorLineNumber` właściwości przechowywania tekstu, co powoduje wyjątek i numer wiersza tekstu.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analizowanie plików w wielu formatach  
 `PeekChars` Metody `TextFieldParser` obiekt może służyć do sprawdzania poszczególnych pól przed odczytaniem, co pozwala na zdefiniowanie wielu formatach dla pól i odpowiednio reagować. Aby uzyskać więcej informacji, zobacz [jak: Odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
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
