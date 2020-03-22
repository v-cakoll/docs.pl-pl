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
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="f2155-102">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2155-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>

<span data-ttu-id="f2155-103">Obiekt `TextFieldParser` umożliwia analizowanie i przetwarzanie bardzo dużych plików, które są skonstruowane jako kolumny o rozdzielanej szerokości tekstu, takie jak pliki dziennika lub informacje o starszej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="f2155-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="f2155-104">Analizowanie pliku tekstowego `TextFieldParser` z jest podobny do iteracji nad plikiem tekstowym, podczas gdy metoda analizy wyodrębnić pola tekstu jest podobna do metod manipulowania ciągami używanych do tokenizacji ciągów rozdzielanych.</span><span class="sxs-lookup"><span data-stu-id="f2155-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="f2155-105">Analizowanie różnych typów plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="f2155-105">Parsing different types of text files</span></span>  

 <span data-ttu-id="f2155-106">Pliki tekstowe mogą mieć pola o różnej szerokości, rozdzielone znakiem, takim jak przecinek lub miejsce na tabulatorze.</span><span class="sxs-lookup"><span data-stu-id="f2155-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="f2155-107">Zdefiniuj `TextFieldType` i ogranicznik, jak w `SetDelimiters` poniższym przykładzie, który używa metody do definiowania pliku tekstowego rozdzielanego tabulatora:</span><span class="sxs-lookup"><span data-stu-id="f2155-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="f2155-108">Inne pliki tekstowe mogą mieć szerokości pól, które są stałe.</span><span class="sxs-lookup"><span data-stu-id="f2155-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="f2155-109">W takich przypadkach należy `TextFieldType` zdefiniować `FixedWidth` as i zdefiniować szerokości każdego pola, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f2155-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="f2155-110">W tym przykładzie użyto `SetFieldWidths` metody do definiowania kolumn tekstu: pierwsza kolumna ma szerokość 5 znaków, druga to 10, trzecia 11, a czwarta ma zmienną szerokość.</span><span class="sxs-lookup"><span data-stu-id="f2155-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="f2155-111">Po zdefiniowaniu formatu można zapętlać `ReadFields` plik, używając metody przetwarzania każdego wiersza po kolei.</span><span class="sxs-lookup"><span data-stu-id="f2155-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="f2155-112">Jeśli pole nie jest zgodne z <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> określonym formatem, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f2155-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="f2155-113">Gdy takie wyjątki są `ErrorLine` `ErrorLineNumber` zgłaszane, i właściwości przechowywania tekstu powodując wyjątek i numer wiersza tego tekstu.</span><span class="sxs-lookup"><span data-stu-id="f2155-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="f2155-114">Analizowanie plików w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="f2155-114">Parsing files with multiple formats</span></span>  

 <span data-ttu-id="f2155-115">Metoda `PeekChars` `TextFieldParser` obiektu może służyć do sprawdzania każdego pola przed jego odczytem, co pozwala na zdefiniowanie wielu formatów pól i odpowiednie reagowanie.</span><span class="sxs-lookup"><span data-stu-id="f2155-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="f2155-116">Aby uzyskać więcej informacji, zobacz [Jak: Odczyt z plików tekstowych z wieloma formatami](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="f2155-116">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2155-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2155-117">See also</span></span>

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
