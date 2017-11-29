---
title: 'Porady: tworzenie kopii pliku w tym samym katalogu w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af592e16bb1f7f0bbb188b2ea39394ec1074d302
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="fcef6-102">Porady: tworzenie kopii pliku w tym samym katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcef6-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>
<span data-ttu-id="fcef6-103">Użyj `My.Computer.FileSystem.CopyFile` metoda kopiowania plików.</span><span class="sxs-lookup"><span data-stu-id="fcef6-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="fcef6-104">Parametry pozwalają na zastąpienie istniejących plików, Zmień nazwę pliku, Pokaż postęp operacji i Zezwalaj użytkownikowi na anulowanie operacji.</span><span class="sxs-lookup"><span data-stu-id="fcef6-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="fcef6-105">Aby utworzyć kopię pliku w folderze</span><span class="sxs-lookup"><span data-stu-id="fcef6-105">To create a copy of a file in the same folder</span></span>  
  
-   <span data-ttu-id="fcef6-106">Użyj `CopyFile` metody dostarczania pliku docelowego i lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="fcef6-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="fcef6-107">Poniższy przykład tworzy kopię `test.txt` o nazwie `test2.txt`.</span><span class="sxs-lookup"><span data-stu-id="fcef6-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="fcef6-108">Aby utworzyć kopii pliku w tym samym folderze, zastępując istniejące pliki</span><span class="sxs-lookup"><span data-stu-id="fcef6-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
-   <span data-ttu-id="fcef6-109">Użyj `CopyFile` metody, podając pliku docelowego i lokalizacji, a ustawienie `overwrite` do `True`.</span><span class="sxs-lookup"><span data-stu-id="fcef6-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="fcef6-110">Poniższy przykład tworzy kopię `test.txt` o nazwie `test2.txt` i zastępuje istniejące pliki o tej nazwie.</span><span class="sxs-lookup"><span data-stu-id="fcef6-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fcef6-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="fcef6-111">Robust Programming</span></span>  
 <span data-ttu-id="fcef6-112">Poniższe warunki mogą spowodować wyjątków:</span><span class="sxs-lookup"><span data-stu-id="fcef6-112">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="fcef6-113">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="fcef6-114">System nie może pobrać ścieżkę bezwzględną (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="fcef6-115">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="fcef6-116">Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="fcef6-117">Łączna ścieżka wskazuje na istniejący katalog (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="fcef6-118">Plik docelowy istnieje i `overwrite` ustawiono `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="fcef6-119">Użytkownik nie ma wystarczających uprawnień do dostępu do pliku (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="fcef6-120">Plik w folderze docelowym o takiej samej nazwie jest w użyciu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="fcef6-121">Nazwę pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="fcef6-122">`ShowUI`ustawiono `True`, `onUserCancel` ustawiono `ThrowException`, a użytkownik anulował operację (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="fcef6-123">`ShowUI`ustawiono `True`, `onUserCancel` ustawiono `ThrowException`, i występuje Wystąpił nieokreślony błąd We/Wy (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="fcef6-124">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="fcef6-125">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="fcef6-126">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="fcef6-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcef6-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcef6-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [<span data-ttu-id="fcef6-128">Porady: kopiowanie plików z określonym wzorcem do katalogu</span><span class="sxs-lookup"><span data-stu-id="fcef6-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [<span data-ttu-id="fcef6-129">Porady: tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="fcef6-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [<span data-ttu-id="fcef6-130">Porady: kopiowanie katalogu do innego katalogu</span><span class="sxs-lookup"><span data-stu-id="fcef6-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [<span data-ttu-id="fcef6-131">Porady: Zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="fcef6-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
