---
title: 'Porady: przenoszenie pliku w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96c6d1d89c0dfe4720637202b42414047e96f146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="339ae-102">Porady: przenoszenie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="339ae-102">How to: Move a File in Visual Basic</span></span>
<span data-ttu-id="339ae-103">`My.Computer.FileSystem.MoveFile` Metody można użyć do przeniesienia pliku do innego folderu.</span><span class="sxs-lookup"><span data-stu-id="339ae-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="339ae-104">Strukturze docelowej nie istnieje, zostanie utworzona.</span><span class="sxs-lookup"><span data-stu-id="339ae-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="339ae-105">Aby przenieść plik</span><span class="sxs-lookup"><span data-stu-id="339ae-105">To move a file</span></span>  
  
-   <span data-ttu-id="339ae-106">Użyj `MoveFile` metodę, aby przenieść plik, określając nazwę pliku i lokalizację dla pliku źródłowego i docelowego pliku.</span><span class="sxs-lookup"><span data-stu-id="339ae-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="339ae-107">W tym przykładzie przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="339ae-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="339ae-108">Należy pamiętać, że nazwa pliku docelowego jest określony, mimo że jest taka sama jak nazwa pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="339ae-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="339ae-109">Aby przenieść plik i zmień jego nazwę</span><span class="sxs-lookup"><span data-stu-id="339ae-109">To move a file and rename it</span></span>  
  
-   <span data-ttu-id="339ae-110">Użyj `MoveFile` metodę, aby przenieść plik, określając nazwa pliku źródłowego i lokalizacji, lokalizacji docelowej i nową nazwę w lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="339ae-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="339ae-111">W tym przykładzie przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2` i zmienia jego nazwę `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="339ae-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="339ae-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="339ae-112">Robust Programming</span></span>  
 <span data-ttu-id="339ae-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="339ae-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="339ae-114">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="339ae-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="339ae-115">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="339ae-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="339ae-116">`destinationFileName`jest `Nothing` lub ciąg pusty (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="339ae-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="339ae-117">Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="339ae-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="339ae-118">Punkty połączoną ścieżkę do istniejącego katalogu, plik docelowy istnieje i `overwrite` ustawiono `False`, plik w katalogu docelowym o takiej samej nazwie jest używany, lub użytkownik nie ma wystarczających uprawnień do dostępu do pliku (<xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="339ae-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="339ae-119">Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="339ae-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="339ae-120">`showUI`ustawiono `True`, `onUserCancel` ustawiono `ThrowException`i użytkownik anulował operację lub występuje Wystąpił nieokreślony błąd We/Wy (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="339ae-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="339ae-121">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="339ae-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="339ae-122">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="339ae-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="339ae-123">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="339ae-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339ae-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="339ae-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>  
 [<span data-ttu-id="339ae-125">Porady: Zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="339ae-125">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [<span data-ttu-id="339ae-126">Porady: tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="339ae-126">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [<span data-ttu-id="339ae-127">Porady: analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="339ae-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
