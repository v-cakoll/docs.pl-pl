---
title: 'Porady: tworzenie kopii pliku w innym katalogu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 1584e2a768562670662d3a9636d23f0ffe38547e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="05ed3-102">Porady: tworzenie kopii pliku w innym katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05ed3-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>
<span data-ttu-id="05ed3-103">`My.Computer.FileSystem.CopyFile` Metoda służy do kopiowania plików.</span><span class="sxs-lookup"><span data-stu-id="05ed3-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="05ed3-104">Parametry umożliwiają zastąpienie istniejących plików, Zmień nazwę pliku, Pokaż postęp operacji i Zezwalaj użytkownikowi na anulowanie operacji.</span><span class="sxs-lookup"><span data-stu-id="05ed3-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="05ed3-105">Aby skopiować plik tekstowy do innego folderu</span><span class="sxs-lookup"><span data-stu-id="05ed3-105">To copy a text file to another folder</span></span>  
  
-   <span data-ttu-id="05ed3-106">Użyj `CopyFile` metoda kopiowania pliku, określając plik źródłowy i katalog docelowy.</span><span class="sxs-lookup"><span data-stu-id="05ed3-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="05ed3-107">`overwrite` Parametr umożliwia określenie, czy chcesz zastąpić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="05ed3-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="05ed3-108">W poniższych przykładach kodu pokazano sposób użycia `CopyFile`.</span><span class="sxs-lookup"><span data-stu-id="05ed3-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="05ed3-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="05ed3-109">Robust Programming</span></span>  
 <span data-ttu-id="05ed3-110">Poniższe warunki mogą spowodować wyjątków:</span><span class="sxs-lookup"><span data-stu-id="05ed3-110">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="05ed3-111">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="05ed3-112">System nie może pobrać ścieżkę bezwzględną (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="05ed3-113">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="05ed3-114">Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="05ed3-115">Łączna ścieżka wskazuje na istniejący katalog (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="05ed3-116">Plik docelowy istnieje i `overwrite` ustawiono `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="05ed3-117">Użytkownik nie ma wystarczających uprawnień do dostępu do pliku (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="05ed3-118">Plik w folderze docelowym o takiej samej nazwie jest w użyciu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="05ed3-119">Nazwę pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="05ed3-120">`ShowUI` ustawiono `True`, `onUserCancel` ustawiono `ThrowException`, a użytkownik anulował operację (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="05ed3-121">`ShowUI` ustawiono `True`, `onUserCancel` ustawiono `ThrowException`, i występuje Wystąpił nieokreślony błąd We/Wy (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="05ed3-122">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="05ed3-123">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="05ed3-124">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="05ed3-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ed3-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05ed3-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [<span data-ttu-id="05ed3-126">Instrukcje: kopiowanie plików z określonym wzorcem do katalogu</span><span class="sxs-lookup"><span data-stu-id="05ed3-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [<span data-ttu-id="05ed3-127">Instrukcje: tworzenie kopii pliku w tym samym katalogu</span><span class="sxs-lookup"><span data-stu-id="05ed3-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [<span data-ttu-id="05ed3-128">Instrukcje: kopiowanie katalogu do innego katalogu</span><span class="sxs-lookup"><span data-stu-id="05ed3-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [<span data-ttu-id="05ed3-129">Instrukcje: zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="05ed3-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
