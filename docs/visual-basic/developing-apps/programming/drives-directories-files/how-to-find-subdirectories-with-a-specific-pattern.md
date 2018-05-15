---
title: 'Porady: znajdowanie podkatalogów z określonym wzorcem w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: b3c80fccea06a48c78f37dc7d1c8dcc88e143de4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="a5b77-102">Porady: znajdowanie podkatalogów z określonym wzorcem w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5b77-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="a5b77-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Metoda zwraca zbiór ciągów reprezentujących nazwy ścieżki dla podkatalogów w katalogu tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="a5b77-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="a5b77-104">Można użyć `wildCards` parametr, aby określić określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="a5b77-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="a5b77-105">Jeśli chcesz w wyszukiwaniu uwzględnić zawartość podkatalogów, ustaw `searchType` parametr `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="a5b77-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="a5b77-106">Pusta kolekcja jest zwracany, gdy zostaną znalezione nie katalogi zgodne z określonym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="a5b77-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="a5b77-107">Aby znajdowanie podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="a5b77-107">To find subdirectories with a specific pattern</span></span>  
  
-   <span data-ttu-id="a5b77-108">Użyj `GetDirectories` metody, podając nazwę i ścieżkę katalogu do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="a5b77-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="a5b77-109">Poniższy przykład zwraca wszystkie katalogi w strukturze katalogów, zawierające słowo "Dzienniki" w nazwie, a następnie dodanie ich do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="a5b77-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-subdirectories-with-a-specific-pattern_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a5b77-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a5b77-110">Robust Programming</span></span>  
 <span data-ttu-id="a5b77-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a5b77-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a5b77-112">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="a5b77-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="a5b77-113">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="a5b77-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="a5b77-114">Co najmniej jeden określony symboli wieloznacznych jest `Nothing`, ciągiem pustym lub zawiera tylko spacje (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="a5b77-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="a5b77-115">`directory` nie istnieje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="a5b77-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="a5b77-116">`directory` Wskazuje istniejący plik (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="a5b77-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="a5b77-117">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="a5b77-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="a5b77-118">Nazwę pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="a5b77-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="a5b77-119">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a5b77-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="a5b77-120">Użytkownik nie ma wystarczających uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="a5b77-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b77-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5b77-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>  
 [<span data-ttu-id="a5b77-122">Instrukcje: znajdowanie plików z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="a5b77-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
