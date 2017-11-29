---
title: "Porady: znajdowanie plików z określonym wzorcem w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce37e7241eb33c3d4f18355d3b5375e0de95b28f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="db45f-102">Porady: znajdowanie plików z określonym wzorcem w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="db45f-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="db45f-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda zwraca zbiór ciągów reprezentujących nazw ścieżek do plików tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="db45f-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="db45f-104">Można użyć `wildCards` parametr, aby określić określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="db45f-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="db45f-105">Jeśli chcesz w wyszukiwaniu uwzględnić podkatalogów, ustaw `searchType` parametr `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="db45f-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="db45f-106">Pusta kolekcja jest zwracany, jeśli znaleziono nie plików zgodnych z określonym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="db45f-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db45f-107">Aby uzyskać informacje dotyczące zwracania listy plików za pomocą `DirectoryInfo` klasy `System.IO` przestrzeni nazw, zobacz <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="db45f-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="db45f-108">Aby znaleźć plików z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="db45f-108">To find files with a specified pattern</span></span>  
  
-   <span data-ttu-id="db45f-109">Użyj `GetFiles` metody, podając nazwę i ścieżkę katalogu do przeszukania, a następnie określając wzorzec.</span><span class="sxs-lookup"><span data-stu-id="db45f-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="db45f-110">Poniższy przykład zwraca wszystkie pliki z rozszerzeniem `.dll` w katalogu i dodaje je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="db45f-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-files-with-a-specific-pattern_1.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="db45f-111">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="db45f-111">.NET Framework Security</span></span>  
 <span data-ttu-id="db45f-112">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="db45f-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="db45f-113">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="db45f-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="db45f-114">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="db45f-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="db45f-115">`directory`nie istnieje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="db45f-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="db45f-116">`directory`Wskazuje istniejący plik (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="db45f-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="db45f-117">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="db45f-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="db45f-118">Nazwę pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="db45f-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="db45f-119">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="db45f-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="db45f-120">Użytkownik nie ma wystarczających uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="db45f-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db45f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db45f-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>  
 [<span data-ttu-id="db45f-122">Porady: znajdowanie podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="db45f-122">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [<span data-ttu-id="db45f-123">Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="db45f-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [<span data-ttu-id="db45f-124">Porady: pobieranie kolekcji plików z katalogu</span><span class="sxs-lookup"><span data-stu-id="db45f-124">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
