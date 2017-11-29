---
title: 'Porady: zmienianie nazwy pliku w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34316fabf63959389eee498a6063ac7c9a7b320a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="90df3-102">Porady: zmienianie nazwy pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90df3-102">How to: Rename a File in Visual Basic</span></span>
<span data-ttu-id="90df3-103">Użyj `RenameFile` metody `My.Computer.FileSystem` obiektu, aby zmienić nazwę pliku, dostarczając bieżącą lokalizację, nazwy pliku i nową nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="90df3-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="90df3-104">Nie można użyć tej metody można przenieść pliku; Użyj `MoveFile` metody przenoszenia i Zmień nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="90df3-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="90df3-105">Aby zmienić nazwę pliku</span><span class="sxs-lookup"><span data-stu-id="90df3-105">To rename a file</span></span>  
  
-   <span data-ttu-id="90df3-106">Użyj `My.Computer.FileSystem.RenameFile` metody, aby zmienić nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="90df3-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="90df3-107">W tym przykładzie zmienia nazwę pliku o nazwie `Test.txt` do `SecondTest.txt`.</span><span class="sxs-lookup"><span data-stu-id="90df3-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 <span data-ttu-id="90df3-108">W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="90df3-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="90df3-109">W selektor wstawek kodu, fragment znajduje się w **systemu - przetwarzanie napędów, folderów i plików plików**.</span><span class="sxs-lookup"><span data-stu-id="90df3-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="90df3-110">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="90df3-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="90df3-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="90df3-111">Robust Programming</span></span>  
 <span data-ttu-id="90df3-112">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="90df3-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="90df3-113">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="90df3-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="90df3-114">`newName`zawiera informacje o ścieżce (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="90df3-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="90df3-115">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="90df3-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="90df3-116">`newName`jest `Nothing` lub ciąg pusty (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="90df3-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="90df3-117">Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="90df3-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="90df3-118">Brak istniejący plik lub katalog o nazwie określonej w `newName` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="90df3-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="90df3-119">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="90df3-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="90df3-120">Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="90df3-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="90df3-121">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="90df3-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="90df3-122">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="90df3-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90df3-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90df3-123">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>  
 [<span data-ttu-id="90df3-124">Porady: przenoszenie pliku</span><span class="sxs-lookup"><span data-stu-id="90df3-124">How to: Move a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)  
 [<span data-ttu-id="90df3-125">Tworzenie, usuwanie i przenoszenie plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="90df3-125">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 [<span data-ttu-id="90df3-126">Porady: tworzenie kopii pliku w tym samym katalogu</span><span class="sxs-lookup"><span data-stu-id="90df3-126">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [<span data-ttu-id="90df3-127">Porady: tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="90df3-127">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
