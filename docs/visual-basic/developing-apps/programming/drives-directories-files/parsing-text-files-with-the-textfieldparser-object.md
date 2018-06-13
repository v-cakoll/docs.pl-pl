---
title: Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 520121ba549532c5ce73810347025949eee5a077
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587309"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="7e95c-102">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e95c-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>
<span data-ttu-id="7e95c-103">`TextFieldParser` Obiektu umożliwia przeanalizować i przetworzyć pliku bardzo dużych mają strukturę jako rozdzielany szerokość kolumny tekstu, takich jak pliki dziennika lub starszej wersji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7e95c-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="7e95c-104">Podczas analizowania pliku tekstowego z `TextFieldParser` jest podobny do Iterowanie po pliku tekstowego, gdy metody parse do wyodrębniania pól tekstu jest podobny do metod manipulowania ciągami używany do tokenizacji ciągów rozdzielone.</span><span class="sxs-lookup"><span data-stu-id="7e95c-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="7e95c-105">Podczas analizowania różnych typów plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="7e95c-105">Parsing different types of text files</span></span>  
 <span data-ttu-id="7e95c-106">Pliki tekstowe mogą mieć pól szerokości różnych znakiem np. przecinek lub miejsce na karcie.</span><span class="sxs-lookup"><span data-stu-id="7e95c-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="7e95c-107">Zdefiniuj `TextFieldType` i znaku ogranicznika, jak w poniższym przykładzie, który używa `SetDelimiters` metodę, aby określić plik tekstowy tabulacji:</span><span class="sxs-lookup"><span data-stu-id="7e95c-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]  
  
 <span data-ttu-id="7e95c-108">Inne pliki tekst może mieć szerokości pól, które zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="7e95c-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="7e95c-109">W takich przypadkach należy zdefiniować `TextFieldType` jako `FixedWidth` i zdefiniuj szerokość każdego pola, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7e95c-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="7e95c-110">W tym przykładzie użyto `SetFieldWidths` metody do definiowania kolumn tekstu: pierwsza kolumna jest 5 znaków, drugą jest wartość 10, 11 jest trzeci i czwarty jest o zmiennej szerokości.</span><span class="sxs-lookup"><span data-stu-id="7e95c-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]  
  
 <span data-ttu-id="7e95c-111">Gdy ten format jest zdefiniowany, pętli za pomocą pliku, przy użyciu `ReadFields` metoda z kolei przetwarzania każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="7e95c-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="7e95c-112">Jeśli pole jest niezgodny z określonym formacie <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7e95c-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="7e95c-113">Gdy taki wyjątek `ErrorLine` i `ErrorLineNumber` właściwości przechowywania tekstu, powodując wyjątek i numer wiersza tekstu.</span><span class="sxs-lookup"><span data-stu-id="7e95c-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="7e95c-114">Analizowanie plików w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="7e95c-114">Parsing files with multiple formats</span></span>  
 <span data-ttu-id="7e95c-115">`PeekChars` Metody `TextFieldParser` obiekt może służyć do sprawdzania każdego pola przed odczytaniem, umożliwiając zdefiniowanie wielu formatów pól i odpowiednio reagują.</span><span class="sxs-lookup"><span data-stu-id="7e95c-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="7e95c-116">Aby uzyskać więcej informacji, zobacz [porady: Odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="7e95c-116">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e95c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e95c-117">See also</span></span>  
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
