---
title: 'Porady: Odczyt z plików testowych o stałej szerokości w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: b1581800c4e16e3bbbf43685508cee781efa6901
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634574"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="85f6f-102">Porady: Odczyt z plików testowych o stałej szerokości w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85f6f-102">How to: read from fixed-width text files in Visual Basic</span></span>
<span data-ttu-id="85f6f-103">`TextFieldParser` Obiekt umożliwia łatwe oraz efektywne analizowanie strukturyzowanych plików tekstowych, takie jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="85f6f-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="85f6f-104">`TextFieldType` Właściwość definiuje, czy przeanalizowany plik jest rozdzielany plik lub taki, który ma pola o stałej szerokości tekstu.</span><span class="sxs-lookup"><span data-stu-id="85f6f-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="85f6f-105">Plik tekstowy stałej szerokości pola na końcu mogą mieć szerokość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="85f6f-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="85f6f-106">Aby określić, że pole na końcu ma szerokość zmiennej, zdefiniuj ma szerokość mniejszą lub równą zero.</span><span class="sxs-lookup"><span data-stu-id="85f6f-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="85f6f-107">Aby przeanalizować plik tekstowy stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="85f6f-107">To parse a fixed-width text file</span></span>  
  
1.  <span data-ttu-id="85f6f-108">Utwórz nową `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="85f6f-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="85f6f-109">Poniższy kod tworzy `TextFieldParser` o nazwie `Reader` i otwiera plik `test.log`.</span><span class="sxs-lookup"><span data-stu-id="85f6f-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]  
  
2.  <span data-ttu-id="85f6f-110">Zdefiniuj `TextFieldType` właściwość jako `FixedWidth`, definiując szerokość i formatowanie.</span><span class="sxs-lookup"><span data-stu-id="85f6f-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="85f6f-111">Poniższy kod definiuje kolumny tekstu. Pierwsza to 5 znaki dwubajtowe, druga 10, 11 trzecia i czwarta to o zmiennej szerokości.</span><span class="sxs-lookup"><span data-stu-id="85f6f-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]  
  
3.  <span data-ttu-id="85f6f-112">W pętli poprzez pól w pliku.</span><span class="sxs-lookup"><span data-stu-id="85f6f-112">Loop through the fields in the file.</span></span> <span data-ttu-id="85f6f-113">Jeśli wiersze są uszkodzone, należy zgłosić błąd i kontynuować analizowanie.</span><span class="sxs-lookup"><span data-stu-id="85f6f-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]  
  
4.  <span data-ttu-id="85f6f-114">Zamknij `While` i `Using` blokuje z `End While` i `End Using`.</span><span class="sxs-lookup"><span data-stu-id="85f6f-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="85f6f-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="85f6f-115">Example</span></span>  
 <span data-ttu-id="85f6f-116">W tym przykładzie odczytuje z pliku `test.log`.</span><span class="sxs-lookup"><span data-stu-id="85f6f-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="85f6f-117">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="85f6f-117">Robust programming</span></span>  
 <span data-ttu-id="85f6f-118">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="85f6f-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="85f6f-119">Nie można przeanalizować wiersz w określonym formacie (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="85f6f-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="85f6f-120">Komunikat o wyjątku Określa wiersz, powoduje wyjątek, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> właściwość jest przypisany do tekstu w wierszu.</span><span class="sxs-lookup"><span data-stu-id="85f6f-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="85f6f-121">Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="85f6f-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="85f6f-122">Sytuacja częściowego zaufania, użytkownik nie ma wystarczających uprawnień dostępu do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="85f6f-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="85f6f-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="85f6f-123">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="85f6f-124">Ścieżka jest zbyt długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="85f6f-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="85f6f-125">Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="85f6f-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f6f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85f6f-126">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="85f6f-127">Instrukcje: Odczyt z plików tekstowych rozdzielonych przecinkami</span><span class="sxs-lookup"><span data-stu-id="85f6f-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="85f6f-128">Instrukcje: Odczyt z plików tekstowych w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="85f6f-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="85f6f-129">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="85f6f-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="85f6f-130">Przewodnik: Manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85f6f-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="85f6f-131">Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="85f6f-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)

