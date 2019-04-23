---
title: 'Porady: Odczyt z plików tekstowych rozdzielonych przecinkami, w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: f241a8fcb971cfcd94cb32f0b3c0273552954349
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314207"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="d6095-102">Porady: Odczyt z plików tekstowych rozdzielonych przecinkami, w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6095-102">How to: read from comma-delimited text files in Visual Basic</span></span>
<span data-ttu-id="d6095-103">`TextFieldParser` Obiekt umożliwia łatwe oraz efektywne analizowanie strukturyzowanych plików tekstowych, takie jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="d6095-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="d6095-104">`TextFieldType` Właściwość definiuje, czy jest rozdzielonym pliku lub jednego z polami o stałej szerokości tekstu.</span><span class="sxs-lookup"><span data-stu-id="d6095-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="d6095-105">Aby przeanalizować z przecinkiem na końcu, rozdzielanego pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="d6095-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="d6095-106">Utwórz nową `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="d6095-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="d6095-107">Poniższy kod tworzy `TextFieldParser` o nazwie `MyReader` i otwiera plik `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="d6095-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="d6095-108">Zdefiniuj `TextField` typu i ogranicznik.</span><span class="sxs-lookup"><span data-stu-id="d6095-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="d6095-109">Poniższy kod definiuje `TextFieldType` właściwość jako `Delimited` i ogranicznik jako ",".</span><span class="sxs-lookup"><span data-stu-id="d6095-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="d6095-110">W pętli poprzez pól w pliku.</span><span class="sxs-lookup"><span data-stu-id="d6095-110">Loop through the fields in the file.</span></span> <span data-ttu-id="d6095-111">Jeśli wiersze są uszkodzone, należy zgłosić błąd i kontynuować analizowanie.</span><span class="sxs-lookup"><span data-stu-id="d6095-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="d6095-112">Poniższy kod wykonuje pętlę za pomocą pliku, z kolei wyświetlania poszczególnych pól i raportowanie wszystkich pól, które są niepoprawnie sformatowane.</span><span class="sxs-lookup"><span data-stu-id="d6095-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="d6095-113">Zamknij `While` i `Using` blokuje z `End While` i `End Using`.</span><span class="sxs-lookup"><span data-stu-id="d6095-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="d6095-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6095-114">Example</span></span>  
 <span data-ttu-id="d6095-115">W tym przykładzie odczytuje z pliku `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="d6095-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d6095-116">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="d6095-116">Robust programming</span></span>  
 <span data-ttu-id="d6095-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="d6095-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d6095-118">Nie można przeanalizować wiersz w określonym formacie (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="d6095-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="d6095-119">Komunikat o wyjątku Określa wiersz, powoduje wyjątek, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> właściwość jest przypisany tekst zawarty w wierszu.</span><span class="sxs-lookup"><span data-stu-id="d6095-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
-   <span data-ttu-id="d6095-120">Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d6095-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="d6095-121">Sytuacja częściowego zaufania, użytkownik nie ma wystarczających uprawnień dostępu do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="d6095-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="d6095-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d6095-122">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d6095-123">Ścieżka jest zbyt długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="d6095-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="d6095-124">Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d6095-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6095-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6095-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="d6095-126">Instrukcje: Odczyt z plików testowych o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="d6095-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="d6095-127">Instrukcje: Odczyt z plików tekstowych w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="d6095-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="d6095-128">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="d6095-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="d6095-129">Przewodnik: Manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6095-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="d6095-130">Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="d6095-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
