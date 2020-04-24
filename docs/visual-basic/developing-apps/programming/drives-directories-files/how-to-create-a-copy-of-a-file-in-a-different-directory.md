---
title: 'Porady: tworzenie kopii pliku w innym katalogu'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: e9a14e1f3743979548b92a3db653d09a470a1875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348834"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="dc59e-102">Porady: tworzenie kopii pliku w innym katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc59e-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>

<span data-ttu-id="dc59e-103">`My.Computer.FileSystem.CopyFile` Metoda umożliwia kopiowanie plików.</span><span class="sxs-lookup"><span data-stu-id="dc59e-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="dc59e-104">Jego parametry zapewniają możliwość zastępowania istniejących plików, zmiany nazwy pliku, wyświetlenia postępu operacji i umożliwienia użytkownikowi anulowania operacji.</span><span class="sxs-lookup"><span data-stu-id="dc59e-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="dc59e-105">Aby skopiować plik tekstowy do innego folderu</span><span class="sxs-lookup"><span data-stu-id="dc59e-105">To copy a text file to another folder</span></span>  
  
- <span data-ttu-id="dc59e-106">Użyj `CopyFile` metody, aby skopiować plik, określić plik źródłowy i katalog docelowy.</span><span class="sxs-lookup"><span data-stu-id="dc59e-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="dc59e-107">`overwrite` Parametr pozwala określić, czy zastąpić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="dc59e-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="dc59e-108">Poniższy przykład kodu pokazuje, jak korzystać `CopyFile`z programu.</span><span class="sxs-lookup"><span data-stu-id="dc59e-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a><span data-ttu-id="dc59e-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="dc59e-109">Robust Programming</span></span>  

 <span data-ttu-id="dc59e-110">Następujące warunki mogą spowodować zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="dc59e-110">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="dc59e-111">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="dc59e-112">System nie może pobrać ścieżki bezwzględnej (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="dc59e-113">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="dc59e-114">Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="dc59e-115">Połączona ścieżka wskazuje istniejący katalog (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="dc59e-116">Plik docelowy istnieje i `overwrite` ma ustawioną wartość `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="dc59e-117">Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="dc59e-118">Plik w folderze docelowym o tej samej nazwie jest używany (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="dc59e-119">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="dc59e-120">`ShowUI`jest ustawiona na `True`, `onUserCancel` jest ustawiona na `ThrowException`, a użytkownik anulował operację (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="dc59e-121">`ShowUI`jest ustawiona na `True`, `onUserCancel` jest ustawiona na `ThrowException`, i Wystąpił nieokreślony błąd we/wy (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="dc59e-122">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="dc59e-123">Użytkownik nie ma wymaganego uprawnienia (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="dc59e-124">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="dc59e-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc59e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc59e-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="dc59e-126">Instrukcje: kopiowanie plików z określonym wzorcem do katalogu</span><span class="sxs-lookup"><span data-stu-id="dc59e-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="dc59e-127">Instrukcje: tworzenie kopii pliku w tym samym katalogu</span><span class="sxs-lookup"><span data-stu-id="dc59e-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="dc59e-128">Porady: kopiowanie katalogu do innego katalogu</span><span class="sxs-lookup"><span data-stu-id="dc59e-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="dc59e-129">Porady: zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="dc59e-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
