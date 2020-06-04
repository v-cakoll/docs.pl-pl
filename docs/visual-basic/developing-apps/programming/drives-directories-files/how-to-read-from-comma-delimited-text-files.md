---
title: 'Instrukcje: odczyt z rozdzielonych przecinkami plików tekstowych'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: ba62a0226a1a83326cbc7ab393d135763a7c7cb2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411645"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="a70f9-102">Instrukcje: odczyt z rozdzielonych przecinkami plików tekstowych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a70f9-102">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="a70f9-103">`TextFieldParser`Obiekt umożliwia łatwe i wydajne analizowanie strukturalnych plików tekstowych, takich jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="a70f9-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="a70f9-104">`TextFieldType`Właściwość określa, czy jest to plik rozdzielany, czy jeden z polami o stałej szerokości tekstu.</span><span class="sxs-lookup"><span data-stu-id="a70f9-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="a70f9-105">Aby przeanalizować plik tekstowy rozdzielany przecinkami</span><span class="sxs-lookup"><span data-stu-id="a70f9-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="a70f9-106">Utwórz nowy element `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="a70f9-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="a70f9-107">Poniższy kod tworzy `TextFieldParser` nazwę `MyReader` i otwiera plik `test.txt` .</span><span class="sxs-lookup"><span data-stu-id="a70f9-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="a70f9-108">Zdefiniuj `TextField` Typ i ogranicznik.</span><span class="sxs-lookup"><span data-stu-id="a70f9-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="a70f9-109">Poniższy kod definiuje `TextFieldType` Właściwość jako `Delimited` i ogranicznik jako ",".</span><span class="sxs-lookup"><span data-stu-id="a70f9-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="a70f9-110">Przepętlenie przez pola w pliku.</span><span class="sxs-lookup"><span data-stu-id="a70f9-110">Loop through the fields in the file.</span></span> <span data-ttu-id="a70f9-111">Jeśli wszystkie wiersze są uszkodzone, zgłoś błąd i Kontynuuj analizowanie.</span><span class="sxs-lookup"><span data-stu-id="a70f9-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="a70f9-112">Poniższy kod pętle za pomocą pliku, wyświetlając każde pole z kolei i zgłasza wszystkie pola, które są sformatowane nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="a70f9-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="a70f9-113">Zamknij `While` bloki i i `Using` `End While` `End Using` .</span><span class="sxs-lookup"><span data-stu-id="a70f9-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="a70f9-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="a70f9-114">Example</span></span>  

 <span data-ttu-id="a70f9-115">Ten przykład odczytuje z pliku `test.txt` .</span><span class="sxs-lookup"><span data-stu-id="a70f9-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a70f9-116">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a70f9-116">Robust programming</span></span>  

 <span data-ttu-id="a70f9-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a70f9-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a70f9-118">Nie można przeanalizować wiersza przy użyciu określonego formatu ( <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> ).</span><span class="sxs-lookup"><span data-stu-id="a70f9-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="a70f9-119">Komunikat o wyjątku określa wiersz powodujący wyjątek, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> Właściwość jest przypisana do tekstu zawartego w wierszu.</span><span class="sxs-lookup"><span data-stu-id="a70f9-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="a70f9-120">Określony plik nie istnieje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="a70f9-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="a70f9-121">Sytuacja częściowej relacji zaufania, w której użytkownik nie ma wystarczających uprawnień dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="a70f9-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="a70f9-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a70f9-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="a70f9-123">Ścieżka jest za długa ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="a70f9-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="a70f9-124">Użytkownik nie ma wystarczających uprawnień dostępu do pliku ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="a70f9-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a70f9-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a70f9-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="a70f9-126">Instrukcje: Odczyt z plików testowych o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="a70f9-126">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="a70f9-127">Instrukcje: Odczyt z plików tekstowych w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="a70f9-127">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="a70f9-128">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="a70f9-128">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="a70f9-129">Wskazówki: manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a70f9-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="a70f9-130">Rozwiązywanie problemów: Odczytywanie z plików tekstowych oraz zapisywanie w nich</span><span class="sxs-lookup"><span data-stu-id="a70f9-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
