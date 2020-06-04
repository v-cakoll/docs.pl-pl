---
title: 'Instrukcje: Tworzenie kopii pliku w tym samym katalogu'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 741f0c80ba268369ebdd598460e9d5fa13d09571
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401683"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="3b0aa-102">Porady: tworzenie kopii pliku w tym samym katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b0aa-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="3b0aa-103">Użyj `My.Computer.FileSystem.CopyFile` metody, aby skopiować pliki.</span><span class="sxs-lookup"><span data-stu-id="3b0aa-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="3b0aa-104">Parametry umożliwiają zastąpienie istniejących plików, zmiana nazwy pliku, wyświetlenie postępu operacji i umożliwienie użytkownikowi anulowania operacji.</span><span class="sxs-lookup"><span data-stu-id="3b0aa-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="3b0aa-105">Aby utworzyć kopię pliku w tym samym folderze</span><span class="sxs-lookup"><span data-stu-id="3b0aa-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="3b0aa-106">Użyj `CopyFile` metody, dostarczając plik docelowy i lokalizację.</span><span class="sxs-lookup"><span data-stu-id="3b0aa-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="3b0aa-107">Poniższy przykład tworzy kopię o `test.txt` nazwie `test2.txt` .</span><span class="sxs-lookup"><span data-stu-id="3b0aa-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="3b0aa-108">Aby utworzyć kopię pliku w tym samym folderze, zastępując istniejące pliki</span><span class="sxs-lookup"><span data-stu-id="3b0aa-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="3b0aa-109">Użyj `CopyFile` metody, podając docelowy plik i lokalizację, a następnie ustaw wartość `overwrite` `True` .</span><span class="sxs-lookup"><span data-stu-id="3b0aa-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="3b0aa-110">Poniższy przykład tworzy kopię o `test.txt` nazwie `test2.txt` i zastępuje wszystkie istniejące pliki o tej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3b0aa-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3b0aa-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="3b0aa-111">Robust Programming</span></span>  

 <span data-ttu-id="3b0aa-112">Następujące warunki mogą spowodować zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="3b0aa-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="3b0aa-113">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="3b0aa-114">System nie może pobrać ścieżki bezwzględnej ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="3b0aa-115">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="3b0aa-116">Plik źródłowy jest nieprawidłowy lub nie istnieje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="3b0aa-117">Połączona ścieżka wskazuje istniejący katalog ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="3b0aa-118">Plik docelowy istnieje i `overwrite` ma ustawioną wartość `False` ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="3b0aa-119">Użytkownik nie ma wystarczających uprawnień dostępu do pliku ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="3b0aa-120">Plik w folderze docelowym o tej samej nazwie jest używany ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="3b0aa-121">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="3b0aa-122">`ShowUI`jest ustawiona na `True` , `onUserCancel` jest ustawiona na `ThrowException` , a użytkownik anulował operację ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="3b0aa-123">`ShowUI`jest ustawiona na `True` , `onUserCancel` jest ustawiona na `ThrowException` , i Wystąpił nieokreślony błąd we/wy ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="3b0aa-124">Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="3b0aa-125">Użytkownik nie ma wymaganego uprawnienia ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="3b0aa-126">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="3b0aa-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0aa-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b0aa-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="3b0aa-128">Instrukcje: Kopiowanie plików z określonym wzorcem do katalogu</span><span class="sxs-lookup"><span data-stu-id="3b0aa-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="3b0aa-129">Instrukcje: Tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="3b0aa-129">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="3b0aa-130">Instrukcje: Kopiowanie katalogu do innego katalogu</span><span class="sxs-lookup"><span data-stu-id="3b0aa-130">How to: Copy a Directory to Another Directory</span></span>](how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="3b0aa-131">Instrukcje: Zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="3b0aa-131">How to: Rename a File</span></span>](how-to-rename-a-file.md)
