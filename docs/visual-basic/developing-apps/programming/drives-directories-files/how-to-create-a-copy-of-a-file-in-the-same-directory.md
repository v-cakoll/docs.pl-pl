---
title: 'Porady: tworzenie kopii pliku w tym samym katalogu'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 33a4f5424ac50de7b5dc988034ca15127dc1ed02
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348824"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="21f35-102">Porady: tworzenie kopii pliku w tym samym katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21f35-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="21f35-103">Użyj metody `My.Computer.FileSystem.CopyFile`, aby skopiować pliki.</span><span class="sxs-lookup"><span data-stu-id="21f35-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="21f35-104">Parametry umożliwiają zastąpienie istniejących plików, zmiana nazwy pliku, wyświetlenie postępu operacji i umożliwienie użytkownikowi anulowania operacji.</span><span class="sxs-lookup"><span data-stu-id="21f35-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="21f35-105">Aby utworzyć kopię pliku w tym samym folderze</span><span class="sxs-lookup"><span data-stu-id="21f35-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="21f35-106">Użyj metody `CopyFile`, podając plik docelowy i lokalizację.</span><span class="sxs-lookup"><span data-stu-id="21f35-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="21f35-107">Poniższy przykład tworzy kopię `test.txt` o nazwie `test2.txt`.</span><span class="sxs-lookup"><span data-stu-id="21f35-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="21f35-108">Aby utworzyć kopię pliku w tym samym folderze, zastępując istniejące pliki</span><span class="sxs-lookup"><span data-stu-id="21f35-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="21f35-109">Użyj metody `CopyFile`, podając docelowy plik i lokalizację, a następnie ustaw `overwrite` do `True`.</span><span class="sxs-lookup"><span data-stu-id="21f35-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="21f35-110">Poniższy przykład tworzy kopię `test.txt` o nazwie `test2.txt` i zastępuje wszystkie istniejące pliki o tej nazwie.</span><span class="sxs-lookup"><span data-stu-id="21f35-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="21f35-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="21f35-111">Robust Programming</span></span>  

 <span data-ttu-id="21f35-112">Następujące warunki mogą spowodować zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="21f35-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="21f35-113">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="21f35-114">System nie może pobrać ścieżki bezwzględnej (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="21f35-115">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="21f35-116">Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="21f35-117">Połączona ścieżka wskazuje istniejący katalog (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="21f35-118">Plik docelowy istnieje i `overwrite` jest ustawiony na `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="21f35-119">Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="21f35-120">Plik w folderze docelowym o tej samej nazwie jest używany (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="21f35-121">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="21f35-122">`ShowUI` jest ustawiona na `True`, `onUserCancel` jest ustawiona na `ThrowException`, a użytkownik anulował operację (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="21f35-123">`ShowUI` jest ustawiona na `True`, `onUserCancel` jest ustawiona na `ThrowException`i Wystąpił nieokreślony błąd we/wy (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="21f35-124">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="21f35-125">Użytkownik nie ma wymaganego uprawnienia (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="21f35-126">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="21f35-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f35-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21f35-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="21f35-128">Instrukcje: kopiowanie plików z określonym wzorcem do katalogu</span><span class="sxs-lookup"><span data-stu-id="21f35-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="21f35-129">Instrukcje: tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="21f35-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="21f35-130">Instrukcje: kopiowanie katalogu do innego katalogu</span><span class="sxs-lookup"><span data-stu-id="21f35-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="21f35-131">Instrukcje: zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="21f35-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
