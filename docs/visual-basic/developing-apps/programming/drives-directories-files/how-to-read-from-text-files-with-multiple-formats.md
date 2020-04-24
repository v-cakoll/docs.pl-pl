---
title: 'Instrukcje: odczyt z plików tekstowych z wieloma formatami'
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: b36c781d5f8333749d346bb8f19540f0d1bd1692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334574"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="21c36-102">Instrukcje: odczyt z plików fext z wieloma formatami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21c36-102">How to: Read from fext files with multiple formats in Visual Basic</span></span>

<span data-ttu-id="21c36-103"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Obiekt umożliwia łatwe i wydajne analizowanie strukturalnych plików tekstowych, takich jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="21c36-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="21c36-104">Można przetworzyć plik z wieloma formatami przy użyciu `PeekChars` metody, aby określić format każdego wiersza podczas analizowania przez plik.</span><span class="sxs-lookup"><span data-stu-id="21c36-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="21c36-105">Aby przeanalizować plik tekstowy z wieloma formatami</span><span class="sxs-lookup"><span data-stu-id="21c36-105">To parse a text file with multiple formats</span></span>

1. <span data-ttu-id="21c36-106">Dodaj plik tekstowy o nazwie *TestFile. txt* do projektu.</span><span class="sxs-lookup"><span data-stu-id="21c36-106">Add a text file named *testfile.txt* to your project.</span></span> <span data-ttu-id="21c36-107">Dodaj następującą zawartość do pliku tekstowego:</span><span class="sxs-lookup"><span data-stu-id="21c36-107">Add the following content to the text file:</span></span>

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. <span data-ttu-id="21c36-108">Zdefiniuj oczekiwany format i format używany, gdy zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="21c36-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="21c36-109">Ostatni wpis w każdej tablicy to-1, w związku z czym przyjmuje się, że ostatnie pole ma szerokość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="21c36-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="21c36-110">Dzieje się tak, gdy ostatni wpis w tablicy jest mniejszy lub równy 0.</span><span class="sxs-lookup"><span data-stu-id="21c36-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. <span data-ttu-id="21c36-111">Utwórz nowy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> obiekt definiujący szerokość i format.</span><span class="sxs-lookup"><span data-stu-id="21c36-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. <span data-ttu-id="21c36-112">Przechodzenie między wierszami, testowanie formatu przed odczytem.</span><span class="sxs-lookup"><span data-stu-id="21c36-112">Loop through the rows, testing for format before reading.</span></span>

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. <span data-ttu-id="21c36-113">Zapisuj błędy w konsoli.</span><span class="sxs-lookup"><span data-stu-id="21c36-113">Write errors to the console.</span></span>

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a><span data-ttu-id="21c36-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="21c36-114">Example</span></span>

<span data-ttu-id="21c36-115">Oto kompletny przykład, który odczytuje z pliku `testfile.txt`:</span><span class="sxs-lookup"><span data-stu-id="21c36-115">The following is the complete example that reads from the file `testfile.txt`:</span></span>

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a><span data-ttu-id="21c36-116">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="21c36-116">Robust programming</span></span>

<span data-ttu-id="21c36-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="21c36-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="21c36-118">Nie można przeanalizować wiersza przy użyciu określonego formatu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="21c36-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="21c36-119">Komunikat o wyjątku określa wiersz powodujący wyjątek, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> właściwość jest przypisana do tekstu zawartego w wierszu.</span><span class="sxs-lookup"><span data-stu-id="21c36-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>
- <span data-ttu-id="21c36-120">Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="21c36-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>
- <span data-ttu-id="21c36-121">Sytuacja częściowej relacji zaufania, w której użytkownik nie ma wystarczających uprawnień dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="21c36-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="21c36-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="21c36-122">(<xref:System.Security.SecurityException>).</span></span>
- <span data-ttu-id="21c36-123">Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="21c36-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>
- <span data-ttu-id="21c36-124">Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="21c36-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="21c36-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21c36-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="21c36-126">Porady: odczyt z rozdzielonych przecinkami plików testowych</span><span class="sxs-lookup"><span data-stu-id="21c36-126">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="21c36-127">Porady: odczyt z plików testowych o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="21c36-127">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="21c36-128">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="21c36-128">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
