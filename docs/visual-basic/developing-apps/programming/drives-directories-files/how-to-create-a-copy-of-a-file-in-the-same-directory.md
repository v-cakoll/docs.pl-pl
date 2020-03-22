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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348824"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="cc4e8-102">Porady: tworzenie kopii pliku w tym samym katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc4e8-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="cc4e8-103">Użyj `My.Computer.FileSystem.CopyFile` metody kopiowania plików.</span><span class="sxs-lookup"><span data-stu-id="cc4e8-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="cc4e8-104">Parametry umożliwiają zastąpienie istniejących plików, zmianę nazwy pliku, wyświetlenie postępu operacji i umożliwienie użytkownikowi anulowania operacji.</span><span class="sxs-lookup"><span data-stu-id="cc4e8-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="cc4e8-105">Aby utworzyć kopię pliku w tym samym folderze</span><span class="sxs-lookup"><span data-stu-id="cc4e8-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="cc4e8-106">Użyj `CopyFile` metody, podając plik docelowy i lokalizację.</span><span class="sxs-lookup"><span data-stu-id="cc4e8-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="cc4e8-107">Poniższy przykład tworzy `test.txt` kopię `test2.txt`wywoływanego .</span><span class="sxs-lookup"><span data-stu-id="cc4e8-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="cc4e8-108">Aby utworzyć kopię pliku w tym samym folderze, zastępowanie istniejących plików</span><span class="sxs-lookup"><span data-stu-id="cc4e8-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="cc4e8-109">Użyj `CopyFile` metody, podając plik docelowy i `overwrite` `True`lokalizację oraz ustawiając na .</span><span class="sxs-lookup"><span data-stu-id="cc4e8-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="cc4e8-110">Poniższy przykład tworzy `test.txt` kopię `test2.txt` wywoływane i zastępuje wszystkie istniejące pliki o tej nazwie.</span><span class="sxs-lookup"><span data-stu-id="cc4e8-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cc4e8-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="cc4e8-111">Robust Programming</span></span>  

 <span data-ttu-id="cc4e8-112">Następujące warunki mogą powodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="cc4e8-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="cc4e8-113">Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="cc4e8-114">System nie może pobrać ścieżki<xref:System.ArgumentException>bezwzględnej ( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="cc4e8-115">Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="cc4e8-116">Plik źródłowy jest nieprawidłowy lub<xref:System.IO.FileNotFoundException>nie istnieje ( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="cc4e8-117">Połączona ścieżka wskazuje istniejący<xref:System.IO.IOException>katalog ( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cc4e8-118">Plik docelowy istnieje `overwrite` i `False` jest<xref:System.IO.IOException>ustawiony na ( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cc4e8-119">Użytkownik nie ma wystarczających uprawnień dostępu<xref:System.IO.IOException>do pliku ( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cc4e8-120">Plik w folderze docelowym o tej<xref:System.IO.IOException>samej nazwie jest używany ( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cc4e8-121">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="cc4e8-122">`ShowUI`jest `True`ustawiona `onUserCancel` na `ThrowException`, a użytkownik anulował operację<xref:System.OperationCanceledException>( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="cc4e8-123">`ShowUI`jest `True`ustawiona `onUserCancel` na `ThrowException`, i występuje nieokreślony błąd we/wy (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="cc4e8-124">Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="cc4e8-125">Użytkownik nie ma wymaganych<xref:System.UnauthorizedAccessException>uprawnień ( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="cc4e8-126">Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).</span><span class="sxs-lookup"><span data-stu-id="cc4e8-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc4e8-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc4e8-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="cc4e8-128">Instrukcje: kopiowanie plików z określonym wzorcem do katalogu</span><span class="sxs-lookup"><span data-stu-id="cc4e8-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="cc4e8-129">Instrukcje: tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="cc4e8-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="cc4e8-130">Porady: kopiowanie katalogu do innego katalogu</span><span class="sxs-lookup"><span data-stu-id="cc4e8-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="cc4e8-131">Porady: zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="cc4e8-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
