---
title: 'Instrukcje: Zmienianie nazwy pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 3de41ee6627315f0e26964b75f564ff98fe472ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411593"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="3ac64-102">Porady: zmienianie nazwy pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3ac64-102">How to: Rename a File in Visual Basic</span></span>

<span data-ttu-id="3ac64-103">Użyj `RenameFile` metody `My.Computer.FileSystem` obiektu, aby zmienić nazwę pliku, dostarczając bieżącą lokalizację, nazwę pliku i nową nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="3ac64-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="3ac64-104">Nie można użyć tej metody do przeniesienia pliku; Użyj `MoveFile` metody, aby przenieść plik i zmienić jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="3ac64-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="3ac64-105">Aby zmienić nazwę pliku</span><span class="sxs-lookup"><span data-stu-id="3ac64-105">To rename a file</span></span>  
  
- <span data-ttu-id="3ac64-106">Użyj `My.Computer.FileSystem.RenameFile` metody, aby zmienić nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="3ac64-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="3ac64-107">Ten przykład zmienia nazwę pliku o nazwie `Test.txt` na `SecondTest.txt` .</span><span class="sxs-lookup"><span data-stu-id="3ac64-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="3ac64-108">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3ac64-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="3ac64-109">W selektorze fragmentów kodu wstawka znajduje się w **systemie plików — dyski, foldery i pliki**.</span><span class="sxs-lookup"><span data-stu-id="3ac64-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="3ac64-110">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="3ac64-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3ac64-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="3ac64-111">Robust Programming</span></span>  

 <span data-ttu-id="3ac64-112">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="3ac64-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="3ac64-113">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="3ac64-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="3ac64-114">`newName`zawiera informacje o ścieżce ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="3ac64-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="3ac64-115">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="3ac64-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="3ac64-116">`newName`jest `Nothing` lub ciągiem pustym ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="3ac64-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="3ac64-117">Plik źródłowy jest nieprawidłowy lub nie istnieje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="3ac64-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="3ac64-118">Istnieje plik lub katalog o nazwie określonej w `newName` ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="3ac64-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="3ac64-119">Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="3ac64-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="3ac64-120">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="3ac64-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="3ac64-121">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="3ac64-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="3ac64-122">Użytkownik nie ma wymaganego uprawnienia ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="3ac64-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac64-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ac64-123">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="3ac64-124">Instrukcje: Przenoszenie pliku</span><span class="sxs-lookup"><span data-stu-id="3ac64-124">How to: Move a File</span></span>](how-to-move-a-file.md)
- [<span data-ttu-id="3ac64-125">Tworzenie, usuwanie i przenoszenie plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="3ac64-125">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="3ac64-126">Instrukcje: Tworzenie kopii pliku w tym samym katalogu</span><span class="sxs-lookup"><span data-stu-id="3ac64-126">How to: Create a Copy of a File in the Same Directory</span></span>](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="3ac64-127">Instrukcje: Tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="3ac64-127">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
