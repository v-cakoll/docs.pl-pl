---
title: 'Instrukcje: odczyt z plików tekstowych o stałej szerokości'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 3cea9bfe2388f0ca510b15cb020f899b81c4603c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334626"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="d7a54-102">Instrukcje: odczyt z plików tekstowych o stałej szerokości w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7a54-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="d7a54-103">`TextFieldParser` Obiekt umożliwia łatwe i wydajne analizowanie strukturalnych plików tekstowych, takich jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="d7a54-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="d7a54-104">`TextFieldType` Właściwość określa, czy przeanalizowany plik jest plikiem rozdzielanym, czy też ma pola o stałej szerokości tekstu.</span><span class="sxs-lookup"><span data-stu-id="d7a54-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="d7a54-105">W pliku tekstowym o stałej szerokości pole na końcu może mieć zmienną szerokość.</span><span class="sxs-lookup"><span data-stu-id="d7a54-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="d7a54-106">Aby określić, że pole na końcu ma zmienną szerokość, zdefiniuj ją tak, aby miała szerokość mniejszą lub równą zero.</span><span class="sxs-lookup"><span data-stu-id="d7a54-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="d7a54-107">Aby przeanalizować plik tekstowy o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="d7a54-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="d7a54-108">Utwórz nowy element `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="d7a54-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="d7a54-109">Poniższy kod tworzy `TextFieldParser` nazwę `Reader` i otwiera plik. `test.log`</span><span class="sxs-lookup"><span data-stu-id="d7a54-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="d7a54-110">Zdefiniuj `TextFieldType` właściwość jako `FixedWidth`definiującą szerokość i format.</span><span class="sxs-lookup"><span data-stu-id="d7a54-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="d7a54-111">Poniższy kod definiuje kolumny tekstu. pierwsze z nich to 5 znaków szerokości, drugi 10, trzeci 11, a czwarta jest szerokość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d7a54-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="d7a54-112">Przepętlenie przez pola w pliku.</span><span class="sxs-lookup"><span data-stu-id="d7a54-112">Loop through the fields in the file.</span></span> <span data-ttu-id="d7a54-113">Jeśli wszystkie wiersze są uszkodzone, zgłoś błąd i Kontynuuj analizowanie.</span><span class="sxs-lookup"><span data-stu-id="d7a54-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="d7a54-114">Zamknij bloki `While` `Using` `End While` i i `End Using`.</span><span class="sxs-lookup"><span data-stu-id="d7a54-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="d7a54-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7a54-115">Example</span></span>  

 <span data-ttu-id="d7a54-116">Ten przykład odczytuje z pliku `test.log`.</span><span class="sxs-lookup"><span data-stu-id="d7a54-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d7a54-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="d7a54-117">Robust programming</span></span>  

 <span data-ttu-id="d7a54-118">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="d7a54-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d7a54-119">Nie można przeanalizować wiersza przy użyciu określonego formatu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="d7a54-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="d7a54-120">Komunikat o wyjątku określa wiersz powodujący wyjątek, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> właściwość jest przypisana do tekstu zawartego w wierszu.</span><span class="sxs-lookup"><span data-stu-id="d7a54-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="d7a54-121">Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d7a54-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="d7a54-122">Sytuacja częściowej relacji zaufania, w której użytkownik nie ma wystarczających uprawnień dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="d7a54-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="d7a54-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d7a54-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="d7a54-124">Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="d7a54-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="d7a54-125">Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d7a54-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a54-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7a54-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="d7a54-127">Porady: odczyt z rozdzielonych przecinkami plików testowych</span><span class="sxs-lookup"><span data-stu-id="d7a54-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="d7a54-128">Instrukcje: odczyt z plików tekstowych w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="d7a54-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="d7a54-129">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="d7a54-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="d7a54-130">Wskazówki: manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7a54-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="d7a54-131">Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="d7a54-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
