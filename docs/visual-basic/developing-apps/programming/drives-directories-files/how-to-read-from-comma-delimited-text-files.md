---
title: 'Jak: odczyt z plików tekstowych rozdzielanych przecinkami'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 9b93893e2221b156b65ce8e945089269ea28c989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335062"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="15c3a-102">Jak: odczyt z plików tekstowych rozdzielanych przecinkami w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15c3a-102">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="15c3a-103">Obiekt `TextFieldParser` umożliwia łatwą i wydajną analizowanie plików tekstowych strukturalnych, takich jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="15c3a-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="15c3a-104">Właściwość `TextFieldType` określa, czy jest to plik rozdzielany, czy plik o stałej szerokości tekstu.</span><span class="sxs-lookup"><span data-stu-id="15c3a-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="15c3a-105">Aby przeanalizować rozdzielony przecinek plik tekstowy</span><span class="sxs-lookup"><span data-stu-id="15c3a-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="15c3a-106">Utwórz nowy element `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="15c3a-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="15c3a-107">Poniższy kod `TextFieldParser` tworzy `MyReader` nazwany i `test.txt`otwiera plik .</span><span class="sxs-lookup"><span data-stu-id="15c3a-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="15c3a-108">Zdefiniuj `TextField` typ i ogranicznik.</span><span class="sxs-lookup"><span data-stu-id="15c3a-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="15c3a-109">Poniższy kod definiuje `TextFieldType` właściwość jako `Delimited` i ogranicznik jako ",".</span><span class="sxs-lookup"><span data-stu-id="15c3a-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="15c3a-110">Pętla przez pola w pliku.</span><span class="sxs-lookup"><span data-stu-id="15c3a-110">Loop through the fields in the file.</span></span> <span data-ttu-id="15c3a-111">Jeśli którekolwiek wiersze są uszkodzone, zgłoś błąd i kontynuuj analizowanie.</span><span class="sxs-lookup"><span data-stu-id="15c3a-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="15c3a-112">Następujący kod pętli za pośrednictwem pliku, wyświetlanie każdego pola po kolei i raportowania wszystkich pól, które są sformatowane niepoprawnie.</span><span class="sxs-lookup"><span data-stu-id="15c3a-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="15c3a-113">Zamknij `While` i `Using` bloki `End While` `End Using`z i .</span><span class="sxs-lookup"><span data-stu-id="15c3a-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="15c3a-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="15c3a-114">Example</span></span>  

 <span data-ttu-id="15c3a-115">W tym przykładzie `test.txt`odczytuje się z pliku .</span><span class="sxs-lookup"><span data-stu-id="15c3a-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="15c3a-116">Solidne programowanie</span><span class="sxs-lookup"><span data-stu-id="15c3a-116">Robust programming</span></span>  

 <span data-ttu-id="15c3a-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="15c3a-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="15c3a-118">Nie można przeanalizować wiersza przy<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>użyciu określonego formatu ( ).</span><span class="sxs-lookup"><span data-stu-id="15c3a-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="15c3a-119">Komunikat o wyjątku określa wiersz powodujący <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> wyjątek, podczas gdy właściwość jest przypisana do tekstu zawartego w wierszu.</span><span class="sxs-lookup"><span data-stu-id="15c3a-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="15c3a-120">Określony plik nie istnieje<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="15c3a-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="15c3a-121">Sytuacja częściowego zaufania, w której użytkownik nie ma wystarczających uprawnień dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="15c3a-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="15c3a-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="15c3a-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="15c3a-123">Ścieżka jest za<xref:System.IO.PathTooLongException>długa ( ).</span><span class="sxs-lookup"><span data-stu-id="15c3a-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="15c3a-124">Użytkownik nie ma wystarczających uprawnień dostępu<xref:System.UnauthorizedAccessException>do pliku ( ).</span><span class="sxs-lookup"><span data-stu-id="15c3a-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c3a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15c3a-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="15c3a-126">Porady: odczyt z plików testowych o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="15c3a-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="15c3a-127">Instrukcje: odczyt z plików tekstowych w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="15c3a-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="15c3a-128">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="15c3a-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="15c3a-129">Wskazówki: manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15c3a-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="15c3a-130">Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="15c3a-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
