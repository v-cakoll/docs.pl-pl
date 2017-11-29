---
title: "Porady: Odczyt z plików tekstowych rozdzielanych przecinkami w języku Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd88762179d9760bcce37b4c500a2bb118e09173
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="d55e2-102">Porady: Odczyt z plików tekstowych rozdzielanych przecinkami w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d55e2-102">How to: read from comma-delimited text files in Visual Basic</span></span>
<span data-ttu-id="d55e2-103">`TextFieldParser` Obiektu pozwala łatwo i efektywnie przeanalizować strukturyzowanych plików tekstowych, takich jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="d55e2-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="d55e2-104">`TextFieldType` Właściwość określa, czy jest rozdzielonym pliku lub jednego z pola o stałej szerokości tekstu.</span><span class="sxs-lookup"><span data-stu-id="d55e2-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="d55e2-105">Aby rozdzielić przecinkami rozdzielanego pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="d55e2-105">To parse a comma delimited text file</span></span>  
  
1.  <span data-ttu-id="d55e2-106">Utwórz nową `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="d55e2-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="d55e2-107">Poniższy kod tworzy `TextFieldParser` o nazwie `MyReader` i otwarcie pliku `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="d55e2-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  <span data-ttu-id="d55e2-108">Zdefiniuj `TextField` typu i znaku ogranicznika.</span><span class="sxs-lookup"><span data-stu-id="d55e2-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="d55e2-109">Poniższy kod definiuje `TextFieldType` właściwość jako `Delimited` i znaku ogranicznika jako ",".</span><span class="sxs-lookup"><span data-stu-id="d55e2-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  <span data-ttu-id="d55e2-110">Pętli pól w pliku.</span><span class="sxs-lookup"><span data-stu-id="d55e2-110">Loop through the fields in the file.</span></span> <span data-ttu-id="d55e2-111">Jeśli wiersze są uszkodzone, zgłoś błąd i kontynuować analizowanie.</span><span class="sxs-lookup"><span data-stu-id="d55e2-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="d55e2-112">Następujący kod w pętli pliku z kolei wyświetlania każdego pola i raportowanie wszystkich pól, które są niepoprawnie sformatowane.</span><span class="sxs-lookup"><span data-stu-id="d55e2-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  <span data-ttu-id="d55e2-113">Zamknij `While` i `Using` blokuje z `End While` i `End Using`.</span><span class="sxs-lookup"><span data-stu-id="d55e2-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="d55e2-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d55e2-114">Example</span></span>  
 <span data-ttu-id="d55e2-115">Ten przykład odczytuje z pliku `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="d55e2-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d55e2-116">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="d55e2-116">Robust programming</span></span>  
 <span data-ttu-id="d55e2-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="d55e2-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d55e2-118">Nie można analizować wiersza w określonym formacie (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="d55e2-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="d55e2-119">Komunikat o wyjątku Określa wiersz przyczyną tego wyjątku, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> właściwości przypisano tekst znajdujący się w wierszu.</span><span class="sxs-lookup"><span data-stu-id="d55e2-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
-   <span data-ttu-id="d55e2-120">Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d55e2-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="d55e2-121">Sytuacja częściowego zaufania, użytkownik nie ma wystarczających uprawnień dostępu do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="d55e2-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="d55e2-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d55e2-122">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d55e2-123">Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="d55e2-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="d55e2-124">Użytkownik nie ma wystarczających uprawnień do dostępu do pliku (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d55e2-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d55e2-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d55e2-125">See also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [<span data-ttu-id="d55e2-126">Porady: Odczyt z plików testowych o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="d55e2-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="d55e2-127">Porady: Odczyt z plików tekstowych w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="d55e2-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="d55e2-128">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="d55e2-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [<span data-ttu-id="d55e2-129">Wskazówki: Manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d55e2-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [<span data-ttu-id="d55e2-130">Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="d55e2-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
