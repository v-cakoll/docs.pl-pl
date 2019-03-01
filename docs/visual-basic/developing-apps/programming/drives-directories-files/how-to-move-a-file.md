---
title: 'Instrukcje: Przenieś plik w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 90f315bc9153fd79f12e3dcbbfe0f238f4090b25
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976879"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="5b12e-102">Instrukcje: Przenieś plik w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b12e-102">How to: Move a File in Visual Basic</span></span>
<span data-ttu-id="5b12e-103">`My.Computer.FileSystem.MoveFile` Metoda może służyć do przenoszenia pliku do innego folderu.</span><span class="sxs-lookup"><span data-stu-id="5b12e-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="5b12e-104">Struktura docelowa nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="5b12e-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="5b12e-105">Aby przenieść plik</span><span class="sxs-lookup"><span data-stu-id="5b12e-105">To move a file</span></span>  
  
-   <span data-ttu-id="5b12e-106">Użyj `MoveFile` metodę, aby przenieść plik, określając nazwę pliku i lokalizację pliku źródłowego i pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="5b12e-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="5b12e-107">W tym przykładzie przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="5b12e-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="5b12e-108">Należy pamiętać, że nazwa pliku docelowego jest określony, nawet jeśli jest taka sama jak nazwa pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5b12e-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="5b12e-109">Aby przenieść plik i zmień jego nazwę</span><span class="sxs-lookup"><span data-stu-id="5b12e-109">To move a file and rename it</span></span>  
  
-   <span data-ttu-id="5b12e-110">Użyj `MoveFile` metodę, aby przenieść plik, określając nazwę pliku źródłowego i lokalizacji, lokalizacji docelowej i Nowa nazwa w lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="5b12e-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="5b12e-111">W tym przykładzie przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2` i zmienia ją `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="5b12e-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5b12e-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5b12e-112">Robust Programming</span></span>  
 <span data-ttu-id="5b12e-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="5b12e-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="5b12e-114">Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5b12e-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="5b12e-115">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5b12e-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="5b12e-116">`destinationFileName` jest `Nothing` ani być pustym ciągiem (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5b12e-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="5b12e-117">Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="5b12e-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="5b12e-118">Punkty połączone ścieżki do istniejącego katalogu, plik docelowy istnieje i `overwrite` ustawiono `False`, plik w katalogu docelowym o takiej samej nazwie jest używany, lub użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="5b12e-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="5b12e-119">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5b12e-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="5b12e-120">`showUI` ustawiono `True`, `onUserCancel` ustawiono `ThrowException`oraz użytkownik anulował operację lub nieokreślony błąd We/Wy (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="5b12e-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="5b12e-121">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="5b12e-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="5b12e-122">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="5b12e-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="5b12e-123">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="5b12e-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b12e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b12e-124">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [<span data-ttu-id="5b12e-125">Instrukcje: Zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="5b12e-125">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [<span data-ttu-id="5b12e-126">Instrukcje: Tworzenie kopii pliku w innym katalogu</span><span class="sxs-lookup"><span data-stu-id="5b12e-126">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="5b12e-127">Instrukcje: Analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="5b12e-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
