---
title: 'Instrukcje: Przenoszenie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 2dafeb3b5f8b8c3a8976b25c1a57f405aebb32b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401605"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="e9fc6-102">Porady: przenoszenie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9fc6-102">How to: Move a File in Visual Basic</span></span>

<span data-ttu-id="e9fc6-103">`My.Computer.FileSystem.MoveFile`Metoda może służyć do przenoszenia pliku do innego folderu.</span><span class="sxs-lookup"><span data-stu-id="e9fc6-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="e9fc6-104">Jeśli struktura docelowa nie istnieje, zostanie utworzona.</span><span class="sxs-lookup"><span data-stu-id="e9fc6-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="e9fc6-105">Aby przenieść plik</span><span class="sxs-lookup"><span data-stu-id="e9fc6-105">To move a file</span></span>  
  
- <span data-ttu-id="e9fc6-106">Użyj `MoveFile` metody, aby przenieść plik, określić nazwę pliku i lokalizację zarówno dla pliku źródłowego, jak i pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="e9fc6-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="e9fc6-107">Ten przykład przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2` .</span><span class="sxs-lookup"><span data-stu-id="e9fc6-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="e9fc6-108">Należy pamiętać, że nazwa pliku docelowego jest określona, mimo że jest taka sama jak nazwa pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e9fc6-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="e9fc6-109">Aby przenieść plik i zmienić jego nazwę</span><span class="sxs-lookup"><span data-stu-id="e9fc6-109">To move a file and rename it</span></span>  
  
- <span data-ttu-id="e9fc6-110">Użyj `MoveFile` metody, aby przenieść plik, określić nazwę i lokalizację pliku źródłowego, lokalizację docelową oraz nową nazwę w lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="e9fc6-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="e9fc6-111">Ten przykład przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2` i zmienia jego nazwę `nexttest.txt` .</span><span class="sxs-lookup"><span data-stu-id="e9fc6-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e9fc6-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="e9fc6-112">Robust Programming</span></span>  

 <span data-ttu-id="e9fc6-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="e9fc6-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e9fc6-114">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e9fc6-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="e9fc6-115">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="e9fc6-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="e9fc6-116">`destinationFileName`jest `Nothing` lub ciągiem pustym ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="e9fc6-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="e9fc6-117">Plik źródłowy jest nieprawidłowy lub nie istnieje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="e9fc6-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="e9fc6-118">Połączona ścieżka wskazuje istniejący katalog, plik docelowy istnieje i `overwrite` ma ustawioną wartość `False` , plik w katalogu docelowym o tej samej nazwie jest używany lub użytkownik nie ma wystarczających uprawnień dostępu do pliku ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="e9fc6-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="e9fc6-119">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="e9fc6-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="e9fc6-120">`showUI`jest ustawiona na `True` , `onUserCancel` jest ustawiona na `ThrowException` , a użytkownik anulował operację lub Wystąpił nieokreślony błąd we/wy ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="e9fc6-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="e9fc6-121">Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="e9fc6-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="e9fc6-122">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="e9fc6-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="e9fc6-123">Użytkownik nie ma wymaganego uprawnienia ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="e9fc6-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9fc6-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9fc6-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [<span data-ttu-id="e9fc6-125">Instrukcje: Zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="e9fc6-125">How to: Rename a File</span></span>](how-to-rename-a-file.md)
- [<span data-ttu-id="e9fc6-126">Instrukcje: Tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="e9fc6-126">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="e9fc6-127">Instrukcje: Analizowanie ścieżek plików</span><span class="sxs-lookup"><span data-stu-id="e9fc6-127">How to: Parse File Paths</span></span>](how-to-parse-file-paths.md)
