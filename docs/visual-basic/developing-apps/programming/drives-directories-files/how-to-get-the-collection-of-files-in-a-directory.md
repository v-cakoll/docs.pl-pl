---
title: "Porady: pobieranie kolekcji plików z katalogu w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c9245ab2593dfed5201640ecf84713582890334
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="becda-102">Porady: pobieranie kolekcji plików z katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="becda-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>
<span data-ttu-id="becda-103">Przeciążeń <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> metoda zwraca zbiór ciągów reprezentujących nazwy plików w katalogu tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="becda-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
-   <span data-ttu-id="becda-104">Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> przeciążenia wyszukiwania prostego pliku w określonym katalogu, bez podkatalogi wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="becda-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
-   <span data-ttu-id="becda-105">Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> przeciążenia, aby określić dodatkowe opcje wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="becda-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="becda-106">Można użyć `wildCards` parametr, aby określić kryteria wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="becda-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="becda-107">Aby w wyszukiwaniu uwzględnić podkatalogów, ustaw `searchType` parametr <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="becda-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="becda-108">Pusta kolekcja jest zwracany, jeśli znaleziono nie plików zgodnych z określonym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="becda-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="becda-109">Aby wyświetlić listę plików w katalogu</span><span class="sxs-lookup"><span data-stu-id="becda-109">To list files in a directory</span></span>  
  
-   <span data-ttu-id="becda-110">Użyj jednej z <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> przeciążenia metody, podając nazwę i ścieżkę katalogu do przeszukania `directory` parametru.</span><span class="sxs-lookup"><span data-stu-id="becda-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="becda-111">Poniższy przykład zwraca wszystkie pliki w katalogu i dodaje je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="becda-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="becda-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="becda-112">Robust Programming</span></span>  
 <span data-ttu-id="becda-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="becda-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="becda-114">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="becda-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="becda-115">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="becda-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="becda-116">`directory`nie istnieje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="becda-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="becda-117">`directory`Wskazuje istniejący plik (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="becda-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="becda-118">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="becda-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="becda-119">Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="becda-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="becda-120">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="becda-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="becda-121">Użytkownik nie ma wystarczających uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="becda-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="becda-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="becda-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>  
 [<span data-ttu-id="becda-123">Porady: znajdowanie plików z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="becda-123">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)  
 [<span data-ttu-id="becda-124">Porady: znajdowanie podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="becda-124">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
