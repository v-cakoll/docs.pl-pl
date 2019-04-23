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
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976784"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="43915-102">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43915-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>
<span data-ttu-id="43915-103">`TextFieldParser` Obiekt umożliwia analizowanie i procesu bardzo dużego pliku, który mają strukturę jako kolumn rozdzielana szerokości tekstu, takie jak pliki dziennika lub informacje o bazie danych w starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="43915-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="43915-104">Podczas analizowania pliku tekstowego z `TextFieldParser` przypomina Iterowanie pliku tekstowego, podczas gdy metody parse do wyodrębniania pól tekstu jest podobne do metod manipulowania ciąg do tokenizacji ciągów rozdzielanych.</span><span class="sxs-lookup"><span data-stu-id="43915-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="43915-105">Analizy różnych typów plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="43915-105">Parsing different types of text files</span></span>  
 <span data-ttu-id="43915-106">Pliki tekstowe mogą mieć pola różnych szerokości, takich jak przecinek lub miejsce na karcie rozdzielane.</span><span class="sxs-lookup"><span data-stu-id="43915-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="43915-107">Zdefiniuj `TextFieldType` i ogranicznik, jak w poniższym przykładzie, który używa `SetDelimiters` metodę, aby zdefiniować pliku tekstowego, rozdzielanego znakami tabulacji:</span><span class="sxs-lookup"><span data-stu-id="43915-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="43915-108">Inne pliki tekstowe mogą mieć szerokościami pól, które zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="43915-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="43915-109">W takich przypadkach należy zdefiniować `TextFieldType` jako `FixedWidth` i zdefiniuj szerokości każdego pola, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="43915-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="43915-110">W tym przykładzie użyto `SetFieldWidths` metody do definiowania kolumn tekstu: pierwsza kolumna jest 5 znaki dwubajtowe, drugi to 10, trzecia będzie 11 i czwarta to o zmiennej szerokości.</span><span class="sxs-lookup"><span data-stu-id="43915-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="43915-111">Po zdefiniowaniu format można pętli pliku przy użyciu `ReadFields` metodę, aby przetworzyć każdy wiersz z osobna.</span><span class="sxs-lookup"><span data-stu-id="43915-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="43915-112">Jeśli pole nie jest zgodny z określonym formacie <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="43915-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="43915-113">Jeśli takie wyjątki są zgłaszane, `ErrorLine` i `ErrorLineNumber` właściwości przechowywania tekstu, co powoduje wyjątek i numer wiersza tekstu.</span><span class="sxs-lookup"><span data-stu-id="43915-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="43915-114">Analizowanie plików w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="43915-114">Parsing files with multiple formats</span></span>  
 <span data-ttu-id="43915-115">`PeekChars` Metody `TextFieldParser` obiekt może służyć do sprawdzania poszczególnych pól przed odczytaniem, co pozwala na zdefiniowanie wielu formatach dla pól i odpowiednio reagować.</span><span class="sxs-lookup"><span data-stu-id="43915-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="43915-116">Aby uzyskać więcej informacji, zobacz [jak: Odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="43915-116">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43915-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43915-117">See also</span></span>

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
