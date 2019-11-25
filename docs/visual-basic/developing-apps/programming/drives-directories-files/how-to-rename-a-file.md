---
title: 'Porady: zmienianie nazwy pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: e69dad9ad7f59002ad62b7a06299ff012488e534
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334552"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="01e5a-102">Porady: zmienianie nazwy pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01e5a-102">How to: Rename a File in Visual Basic</span></span>

<span data-ttu-id="01e5a-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span><span class="sxs-lookup"><span data-stu-id="01e5a-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="01e5a-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span><span class="sxs-lookup"><span data-stu-id="01e5a-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="01e5a-105">To rename a file</span><span class="sxs-lookup"><span data-stu-id="01e5a-105">To rename a file</span></span>  
  
- <span data-ttu-id="01e5a-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span><span class="sxs-lookup"><span data-stu-id="01e5a-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="01e5a-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span><span class="sxs-lookup"><span data-stu-id="01e5a-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="01e5a-108">This code example is also available as an IntelliSense code snippet.</span><span class="sxs-lookup"><span data-stu-id="01e5a-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="01e5a-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span><span class="sxs-lookup"><span data-stu-id="01e5a-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="01e5a-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="01e5a-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="01e5a-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="01e5a-111">Robust Programming</span></span>  

 <span data-ttu-id="01e5a-112">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="01e5a-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="01e5a-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="01e5a-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="01e5a-114">`newName` contains path information (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="01e5a-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="01e5a-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="01e5a-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="01e5a-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="01e5a-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="01e5a-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="01e5a-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="01e5a-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="01e5a-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="01e5a-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="01e5a-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="01e5a-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="01e5a-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="01e5a-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="01e5a-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="01e5a-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="01e5a-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e5a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01e5a-123">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="01e5a-124">Instrukcje: przenoszenie pliku</span><span class="sxs-lookup"><span data-stu-id="01e5a-124">How to: Move a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [<span data-ttu-id="01e5a-125">Tworzenie, usuwanie i przenoszenie plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="01e5a-125">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="01e5a-126">Instrukcje: tworzenie kopii pliku w tym samym katalogu</span><span class="sxs-lookup"><span data-stu-id="01e5a-126">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="01e5a-127">Instrukcje: tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="01e5a-127">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
