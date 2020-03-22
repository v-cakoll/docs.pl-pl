---
title: 'Jak: czytać z tekstu o stałej szerokości Pliki'
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
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="b9846-102">Jak: odczyt z plików tekstowych o stałej szerokości w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9846-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="b9846-103">Obiekt `TextFieldParser` umożliwia łatwą i wydajną analizowanie plików tekstowych strukturalnych, takich jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="b9846-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="b9846-104">Właściwość `TextFieldType` określa, czy analizowany plik jest plikiem rozdzielanym, czy plikiem zawierającym pola tekstu o stałej szerokości.</span><span class="sxs-lookup"><span data-stu-id="b9846-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="b9846-105">W pliku tekstowym o stałej szerokości pole na końcu może mieć zmienną szerokość.</span><span class="sxs-lookup"><span data-stu-id="b9846-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="b9846-106">Aby określić, że pole na końcu ma zmienną szerokość, zdefiniuj go tak, aby szerokość była mniejsza lub równa zeru.</span><span class="sxs-lookup"><span data-stu-id="b9846-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="b9846-107">Aby przeanalizować plik tekstowy o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="b9846-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="b9846-108">Utwórz nowy element `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="b9846-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="b9846-109">Poniższy kod `TextFieldParser` tworzy `Reader` nazwany i `test.log`otwiera plik .</span><span class="sxs-lookup"><span data-stu-id="b9846-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="b9846-110">Zdefiniuj `TextFieldType` właściwość jako `FixedWidth`, definiując szerokość i format.</span><span class="sxs-lookup"><span data-stu-id="b9846-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="b9846-111">Poniższy kod definiuje kolumny tekstu; pierwszy ma szerokość 5 znaków, drugi 10, trzeci 11, a czwarty ma zmienną szerokość.</span><span class="sxs-lookup"><span data-stu-id="b9846-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="b9846-112">Pętla przez pola w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9846-112">Loop through the fields in the file.</span></span> <span data-ttu-id="b9846-113">Jeśli którekolwiek wiersze są uszkodzone, zgłoś błąd i kontynuuj analizowanie.</span><span class="sxs-lookup"><span data-stu-id="b9846-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="b9846-114">Zamknij `While` i `Using` bloki `End While` `End Using`z i .</span><span class="sxs-lookup"><span data-stu-id="b9846-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="b9846-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9846-115">Example</span></span>  

 <span data-ttu-id="b9846-116">W tym przykładzie `test.log`odczytuje się z pliku .</span><span class="sxs-lookup"><span data-stu-id="b9846-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b9846-117">Solidne programowanie</span><span class="sxs-lookup"><span data-stu-id="b9846-117">Robust programming</span></span>  

 <span data-ttu-id="b9846-118">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="b9846-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b9846-119">Nie można przeanalizować wiersza przy<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>użyciu określonego formatu ( ).</span><span class="sxs-lookup"><span data-stu-id="b9846-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="b9846-120">Komunikat o wyjątku określa wiersz powodujący <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> wyjątek, podczas gdy właściwość jest przypisana do tekstu zawartego w wierszu.</span><span class="sxs-lookup"><span data-stu-id="b9846-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="b9846-121">Określony plik nie istnieje<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="b9846-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="b9846-122">Sytuacja częściowego zaufania, w której użytkownik nie ma wystarczających uprawnień dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="b9846-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="b9846-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b9846-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="b9846-124">Ścieżka jest za<xref:System.IO.PathTooLongException>długa ( ).</span><span class="sxs-lookup"><span data-stu-id="b9846-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="b9846-125">Użytkownik nie ma wystarczających uprawnień dostępu<xref:System.UnauthorizedAccessException>do pliku ( ).</span><span class="sxs-lookup"><span data-stu-id="b9846-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9846-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9846-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="b9846-127">Porady: odczyt z rozdzielonych przecinkami plików testowych</span><span class="sxs-lookup"><span data-stu-id="b9846-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="b9846-128">Instrukcje: odczyt z plików tekstowych w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="b9846-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="b9846-129">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="b9846-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="b9846-130">Wskazówki: manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9846-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="b9846-131">Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="b9846-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
