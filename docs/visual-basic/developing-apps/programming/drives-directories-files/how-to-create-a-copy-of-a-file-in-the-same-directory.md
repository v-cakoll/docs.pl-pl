---
title: 'Instrukcje: Tworzenie kopii pliku w tym samym katalogu w Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: b038cd0f780332e195e2f80c2f77cccac01dcc74
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830087"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="46bd0-102">Instrukcje: Tworzenie kopii pliku w tym samym katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46bd0-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>
<span data-ttu-id="46bd0-103">Użyj `My.Computer.FileSystem.CopyFile` metoda kopiowania plików.</span><span class="sxs-lookup"><span data-stu-id="46bd0-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="46bd0-104">Parametry umożliwiają Nadpisz istniejące pliki, Zmień nazwę pliku, wyświetlić postęp operacji i umożliwia użytkownikowi anulować operację.</span><span class="sxs-lookup"><span data-stu-id="46bd0-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="46bd0-105">Aby utworzyć kopię pliku, w tym samym folderze</span><span class="sxs-lookup"><span data-stu-id="46bd0-105">To create a copy of a file in the same folder</span></span>  
  
-   <span data-ttu-id="46bd0-106">Użyj `CopyFile` metodę podawania pliku docelowego i lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="46bd0-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="46bd0-107">Poniższy przykład tworzy kopię `test.txt` o nazwie `test2.txt`.</span><span class="sxs-lookup"><span data-stu-id="46bd0-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="46bd0-108">Aby utworzyć kopię pliku, w tym samym folderze, zastępując istniejące pliki</span><span class="sxs-lookup"><span data-stu-id="46bd0-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
-   <span data-ttu-id="46bd0-109">Użyj `CopyFile` metody dostarczenie pliku docelowego i lokalizację, a ustawienie `overwrite` do `True`.</span><span class="sxs-lookup"><span data-stu-id="46bd0-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="46bd0-110">Poniższy przykład tworzy kopię `test.txt` o nazwie `test2.txt` i zastępuje wszelkie istniejące pliki o tej nazwie.</span><span class="sxs-lookup"><span data-stu-id="46bd0-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="46bd0-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="46bd0-111">Robust Programming</span></span>  
 <span data-ttu-id="46bd0-112">Następujące warunki mogą spowodować zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="46bd0-112">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="46bd0-113">Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="46bd0-114">System nie może pobrać ścieżki bezwzględnej (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="46bd0-115">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="46bd0-116">Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="46bd0-117">Połączone ścieżka wskazuje na istniejący katalog (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="46bd0-118">Plik docelowy istnieje i `overwrite` ustawiono `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="46bd0-119">Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="46bd0-120">Plik w folderze docelowym o takiej samej nazwie jest w użyciu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="46bd0-121">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="46bd0-122">`ShowUI` ustawiono `True`, `onUserCancel` ustawiono `ThrowException`, a użytkownik anulował operację (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="46bd0-123">`ShowUI` ustawiono `True`, `onUserCancel` ustawiono `ThrowException`, i nieokreślony błąd We/Wy (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="46bd0-124">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="46bd0-125">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="46bd0-126">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="46bd0-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46bd0-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46bd0-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="46bd0-128">Instrukcje: Kopiowanie plików z określonym wzorcem do katalogu</span><span class="sxs-lookup"><span data-stu-id="46bd0-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="46bd0-129">Instrukcje: Tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="46bd0-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="46bd0-130">Instrukcje: Kopiowanie katalogu do innego katalogu</span><span class="sxs-lookup"><span data-stu-id="46bd0-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="46bd0-131">Instrukcje: Zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="46bd0-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
