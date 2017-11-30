---
title: "Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 544b65a5197f6a1b68a54f12dbdc0c591bc512e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)
`TextFieldParser` Obiektu umożliwia przeanalizować i przetworzyć pliku bardzo dużych mają strukturę jako rozdzielany szerokość kolumny tekstu, takich jak pliki dziennika lub starszej wersji bazy danych. Podczas analizowania pliku tekstowego z `TextFieldParser` jest podobny do Iterowanie po pliku tekstowego, gdy metody parse do wyodrębniania pól tekstu jest podobny do metod manipulowania ciągami używany do tokenizacji ciągów rozdzielone.  
  
## <a name="parsing-different-types-of-text-files"></a>Podczas analizowania różnych typów plików tekstowych  
 Pliki tekstowe mogą mieć pól szerokości różnych znakiem np. przecinek lub miejsce na karcie. Zdefiniuj `TextFieldType` i znaku ogranicznika, jak w poniższym przykładzie, który używa `SetDelimiters` metodę, aby określić plik tekstowy tabulacji:  
  
 [!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]  
  
 Inne pliki tekst może mieć szerokości pól, które zostały usunięte. W takich przypadkach należy zdefiniować `TextFieldType` jako `FixedWidth` i zdefiniuj szerokość każdego pola, jak w poniższym przykładzie. W tym przykładzie użyto `SetFieldWidths` metody do definiowania kolumn tekstu: pierwsza kolumna jest 5 znaków, drugą jest wartość 10, 11 jest trzeci i czwarty jest o zmiennej szerokości.  
  
 [!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]  
  
 Gdy ten format jest zdefiniowany, pętli za pomocą pliku, przy użyciu `ReadFields` metoda z kolei przetwarzania każdego wiersza.  
  
 Jeśli pole jest niezgodny z określonym formacie <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> wyjątku. Gdy taki wyjątek `ErrorLine` i `ErrorLineNumber` właściwości przechowywania tekstu, powodując wyjątek i numer wiersza tekstu.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analizowanie plików w wielu formatach  
 `PeekChars` Metody `TextFieldParser` obiekt może służyć do sprawdzania każdego pola przed odczytaniem, umożliwiając zdefiniowanie wielu formatów pól i odpowiednio reagują. Aby uzyskać więcej informacji, zobacz [porady: Odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>
