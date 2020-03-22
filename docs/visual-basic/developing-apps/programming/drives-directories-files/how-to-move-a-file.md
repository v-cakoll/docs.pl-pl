---
title: 'Porady: przenoszenie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 29c64a7a81028d47bf489212e6d8faec5e8dda75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335360"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="30019-102">Porady: przenoszenie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30019-102">How to: Move a File in Visual Basic</span></span>

<span data-ttu-id="30019-103">Metoda `My.Computer.FileSystem.MoveFile` ta może służyć do przenoszenia pliku do innego folderu.</span><span class="sxs-lookup"><span data-stu-id="30019-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="30019-104">Jeśli struktura docelowa nie istnieje, zostanie utworzona.</span><span class="sxs-lookup"><span data-stu-id="30019-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="30019-105">Aby przenieść plik</span><span class="sxs-lookup"><span data-stu-id="30019-105">To move a file</span></span>  
  
- <span data-ttu-id="30019-106">Użyj `MoveFile` metody przenoszenia pliku, określając nazwę pliku i lokalizację zarówno dla pliku źródłowego, jak i pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="30019-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="30019-107">W tym przykładzie `test.txt` `TestDir1` przenosi `TestDir2`plik o nazwie z do .</span><span class="sxs-lookup"><span data-stu-id="30019-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="30019-108">Należy zauważyć, że nazwa pliku docelowego jest określona, mimo że jest taka sama jak nazwa pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="30019-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="30019-109">Aby przenieść plik i zmienić jego nazwę</span><span class="sxs-lookup"><span data-stu-id="30019-109">To move a file and rename it</span></span>  
  
- <span data-ttu-id="30019-110">Użyj `MoveFile` metody, aby przenieść plik, określając nazwę i lokalizację pliku źródłowego, lokalizację docelową i nową nazwę w lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="30019-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="30019-111">W tym przykładzie `test.txt` `TestDir1` przenosi `TestDir2` nazwany plik `nexttest.txt`z do i zmienia jego nazwę .</span><span class="sxs-lookup"><span data-stu-id="30019-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="30019-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="30019-112">Robust Programming</span></span>  

 <span data-ttu-id="30019-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="30019-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="30019-114">Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="30019-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="30019-115">Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).</span><span class="sxs-lookup"><span data-stu-id="30019-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="30019-116">`destinationFileName`lub `Nothing` pusty ciąg<xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="30019-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="30019-117">Plik źródłowy jest nieprawidłowy lub<xref:System.IO.FileNotFoundException>nie istnieje ( ).</span><span class="sxs-lookup"><span data-stu-id="30019-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="30019-118">Połączona ścieżka wskazuje istniejący katalog, plik docelowy istnieje i `overwrite` jest ustawiony na `False`, plik w katalogu docelowym o tej samej nazwie jest<xref:System.IO.IOException>w użyciu lub użytkownik nie ma wystarczających uprawnień dostępu do pliku ( ).</span><span class="sxs-lookup"><span data-stu-id="30019-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="30019-119">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="30019-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="30019-120">`showUI`jest `True`ustawiona `onUserCancel` na `ThrowException`, i albo użytkownik anulował operację lub występuje nieokreślony błąd we/wy (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="30019-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="30019-121">Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).</span><span class="sxs-lookup"><span data-stu-id="30019-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="30019-122">Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).</span><span class="sxs-lookup"><span data-stu-id="30019-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="30019-123">Użytkownik nie ma wymaganych<xref:System.UnauthorizedAccessException>uprawnień ( ).</span><span class="sxs-lookup"><span data-stu-id="30019-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30019-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30019-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [<span data-ttu-id="30019-125">Porady: zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="30019-125">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [<span data-ttu-id="30019-126">Instrukcje: tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="30019-126">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="30019-127">Porady: analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="30019-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
