---
title: 'How to: Read from text files with multiple formats'
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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334574"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="b134b-102">How to: Read from fext files with multiple formats in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b134b-102">How to: Read from fext files with multiple formats in Visual Basic</span></span>

<span data-ttu-id="b134b-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span><span class="sxs-lookup"><span data-stu-id="b134b-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="b134b-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span><span class="sxs-lookup"><span data-stu-id="b134b-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="b134b-105">To parse a text file with multiple formats</span><span class="sxs-lookup"><span data-stu-id="b134b-105">To parse a text file with multiple formats</span></span>

1. <span data-ttu-id="b134b-106">Add a text file named *testfile.txt* to your project.</span><span class="sxs-lookup"><span data-stu-id="b134b-106">Add a text file named *testfile.txt* to your project.</span></span> <span data-ttu-id="b134b-107">Add the following content to the text file:</span><span class="sxs-lookup"><span data-stu-id="b134b-107">Add the following content to the text file:</span></span>

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. <span data-ttu-id="b134b-108">Define the expected format and the format used when an error is reported.</span><span class="sxs-lookup"><span data-stu-id="b134b-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="b134b-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span><span class="sxs-lookup"><span data-stu-id="b134b-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="b134b-110">This occurs when the last entry in the array is less than or equal to 0.</span><span class="sxs-lookup"><span data-stu-id="b134b-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. <span data-ttu-id="b134b-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span><span class="sxs-lookup"><span data-stu-id="b134b-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. <span data-ttu-id="b134b-112">Loop through the rows, testing for format before reading.</span><span class="sxs-lookup"><span data-stu-id="b134b-112">Loop through the rows, testing for format before reading.</span></span>

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. <span data-ttu-id="b134b-113">Write errors to the console.</span><span class="sxs-lookup"><span data-stu-id="b134b-113">Write errors to the console.</span></span>

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a><span data-ttu-id="b134b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="b134b-114">Example</span></span>

<span data-ttu-id="b134b-115">The following is the complete example that reads from the file `testfile.txt`:</span><span class="sxs-lookup"><span data-stu-id="b134b-115">The following is the complete example that reads from the file `testfile.txt`:</span></span>

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a><span data-ttu-id="b134b-116">Robust programming</span><span class="sxs-lookup"><span data-stu-id="b134b-116">Robust programming</span></span>

<span data-ttu-id="b134b-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="b134b-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b134b-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="b134b-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="b134b-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span><span class="sxs-lookup"><span data-stu-id="b134b-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>
- <span data-ttu-id="b134b-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="b134b-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>
- <span data-ttu-id="b134b-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span><span class="sxs-lookup"><span data-stu-id="b134b-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="b134b-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b134b-122">(<xref:System.Security.SecurityException>).</span></span>
- <span data-ttu-id="b134b-123">The path is too long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b134b-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>
- <span data-ttu-id="b134b-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="b134b-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="b134b-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b134b-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="b134b-126">Instrukcje: odczyt z rozdzielonych przecinkami plików testowych</span><span class="sxs-lookup"><span data-stu-id="b134b-126">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="b134b-127">Instrukcje: odczyt z plików testowych o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="b134b-127">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="b134b-128">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="b134b-128">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
