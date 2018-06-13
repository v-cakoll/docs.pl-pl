---
title: 'Porady: kopiowanie plików z określonym wzorcem do katalogu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 6b8df24014cf809326993958472df4dae213dbab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586689"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="a5a19-102">Porady: kopiowanie plików z określonym wzorcem do katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5a19-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>
<span data-ttu-id="a5a19-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda zwraca zbiór ciągów reprezentujących nazw ścieżek do plików tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="a5a19-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="a5a19-104">Można użyć `wildCards` parametr, aby określić określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="a5a19-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="a5a19-105">W przypadku znalezienia pasujących plików, zwracana jest pustej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a5a19-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="a5a19-106">Można użyć <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> metodę, aby skopiować pliki do katalogu.</span><span class="sxs-lookup"><span data-stu-id="a5a19-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="a5a19-107">Aby skopiować pliki z określonym wzorcem do katalogu</span><span class="sxs-lookup"><span data-stu-id="a5a19-107">To copy files with a specific pattern to a directory</span></span>  
  
1.  <span data-ttu-id="a5a19-108">Użyj `GetFiles` metodę, aby zwrócić listę plików.</span><span class="sxs-lookup"><span data-stu-id="a5a19-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="a5a19-109">W tym przykładzie zwraca wszystkie .rtf — pliki w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a5a19-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_1.vb)]  
  
2.  <span data-ttu-id="a5a19-110">Użyj `CopyFile` metodę, aby skopiować pliki.</span><span class="sxs-lookup"><span data-stu-id="a5a19-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="a5a19-111">W tym przykładzie kopiuje pliki do katalogu o nazwie `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="a5a19-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_2.vb)]  
  
3.  <span data-ttu-id="a5a19-112">Zamknij `For` instrukcji z `Next` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a5a19-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="a5a19-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5a19-113">Example</span></span>  
 <span data-ttu-id="a5a19-114">Poniższy przykład przedstawia powyżej fragmentów w pełnej postaci kopiuje wszystkie pliki .rtf w określonym katalogu katalog o nazwie `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="a5a19-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_4.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="a5a19-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a5a19-115">.NET Framework Security</span></span>  
 <span data-ttu-id="a5a19-116">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a5a19-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a5a19-117">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="a5a19-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="a5a19-118">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="a5a19-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="a5a19-119">Katalog nie istnieje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="a5a19-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="a5a19-120">Punkty katalogu do istniejącego pliku (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="a5a19-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="a5a19-121">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="a5a19-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="a5a19-122">Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="a5a19-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="a5a19-123">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a5a19-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="a5a19-124">Użytkownik nie ma wystarczających uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="a5a19-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a19-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5a19-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>  
 [<span data-ttu-id="a5a19-126">Instrukcje: znajdowanie podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="a5a19-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [<span data-ttu-id="a5a19-127">Rozwiązywanie problemów: odczytywanie z plików tekstowych oraz zapisywanie w nich</span><span class="sxs-lookup"><span data-stu-id="a5a19-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [<span data-ttu-id="a5a19-128">Instrukcje: pobieranie kolekcji plików z katalogu</span><span class="sxs-lookup"><span data-stu-id="a5a19-128">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
