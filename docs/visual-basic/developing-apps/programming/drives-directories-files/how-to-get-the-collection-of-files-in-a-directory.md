---
title: 'Instrukcje: Pobieranie kolekcji plików z katalogu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: a708d9cfd7b1a5ded3088ee567660bd0b3a5423f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731936"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="c774d-102">Instrukcje: Pobieranie kolekcji plików z katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c774d-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>
<span data-ttu-id="c774d-103">Przeciążenia <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> zwracany przez metodę tylko do odczytu kolekcji ciągów reprezentujących nazwy plików w katalogu:</span><span class="sxs-lookup"><span data-stu-id="c774d-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
-   <span data-ttu-id="c774d-104">Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> przeciążenia pliku prostego wyszukiwania w określonym katalogu, bez podkatalogi wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c774d-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
-   <span data-ttu-id="c774d-105">Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> przeciążenia, aby określić dodatkowe opcje wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c774d-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="c774d-106">Możesz użyć `wildCards` parametru, aby określić kryteria wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c774d-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="c774d-107">Aby w wyszukiwaniu uwzględnić podkatalogi, należy ustawić `searchType` parametr <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c774d-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c774d-108">Pusta kolekcja jest zwracany, jeśli nie zostaną znalezione żadne pliki pasujące do wzorca określonego.</span><span class="sxs-lookup"><span data-stu-id="c774d-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="c774d-109">Aby wyświetlić listę plików w katalogu</span><span class="sxs-lookup"><span data-stu-id="c774d-109">To list files in a directory</span></span>  
  
-   <span data-ttu-id="c774d-110">Użyj jednej z <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> przeciążenia metody, podając nazwę i ścieżkę katalogu do przeszukania `directory` parametru.</span><span class="sxs-lookup"><span data-stu-id="c774d-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="c774d-111">Poniższy przykład zwraca wszystkie pliki w katalogu i doda je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="c774d-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c774d-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="c774d-112">Robust Programming</span></span>  
 <span data-ttu-id="c774d-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="c774d-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c774d-114">Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="c774d-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="c774d-115">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="c774d-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="c774d-116">`directory` nie istnieje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="c774d-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="c774d-117">`directory` wskazuje na istniejący plik (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="c774d-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="c774d-118">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="c774d-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="c774d-119">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="c774d-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="c774d-120">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c774d-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="c774d-121">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="c774d-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c774d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c774d-122">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="c774d-123">Instrukcje: Znajdowanie plików z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="c774d-123">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="c774d-124">Instrukcje: Znajdowanie podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="c774d-124">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
