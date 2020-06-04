---
title: 'Instrukcje: Pobieranie kolekcji plików z katalogu'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: 055151d4b3e3aba6be9b9b03ac9abffc6eb7b734
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401618"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="8d6ac-102">Porady: pobieranie kolekcji plików z katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d6ac-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>

<span data-ttu-id="8d6ac-103">Przeciążenia <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> metody zwracają kolekcję ciągów reprezentujących tylko do odczytu, które reprezentują nazwy plików w katalogu:</span><span class="sxs-lookup"><span data-stu-id="8d6ac-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
- <span data-ttu-id="8d6ac-104">Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> przeciążenia dla prostego wyszukiwania plików w określonym katalogu bez przeszukiwania podkatalogów.</span><span class="sxs-lookup"><span data-stu-id="8d6ac-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
- <span data-ttu-id="8d6ac-105">Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> przeciążenia, aby określić dodatkowe opcje dla wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="8d6ac-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="8d6ac-106">Możesz użyć parametru, `wildCards` Aby określić wzorzec wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="8d6ac-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="8d6ac-107">Aby uwzględnić podkatalogi w wyszukiwaniu, ustaw `searchType` parametr na <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8d6ac-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="8d6ac-108">Pusta kolekcja jest zwracana, jeśli nie znaleziono plików zgodnych z określonym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="8d6ac-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="8d6ac-109">Aby wyświetlić listę plików w katalogu</span><span class="sxs-lookup"><span data-stu-id="8d6ac-109">To list files in a directory</span></span>  
  
- <span data-ttu-id="8d6ac-110">Użyj jednego z <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> przeciążeń metody, podając nazwę i ścieżkę katalogu do wyszukania w `directory` parametrze.</span><span class="sxs-lookup"><span data-stu-id="8d6ac-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="8d6ac-111">Poniższy przykład zwraca wszystkie pliki w katalogu i dodaje je do `ListBox1` .</span><span class="sxs-lookup"><span data-stu-id="8d6ac-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8d6ac-112">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="8d6ac-112">Robust Programming</span></span>  

 <span data-ttu-id="8d6ac-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="8d6ac-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8d6ac-114">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="8d6ac-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="8d6ac-115">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="8d6ac-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="8d6ac-116">`directory`nie istnieje ( <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="8d6ac-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="8d6ac-117">`directory`wskazuje istniejący plik ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="8d6ac-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="8d6ac-118">Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="8d6ac-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="8d6ac-119">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="8d6ac-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="8d6ac-120">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="8d6ac-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="8d6ac-121">Użytkownik nie ma wymaganych uprawnień ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="8d6ac-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6ac-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d6ac-122">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="8d6ac-123">Instrukcje: Znajdowanie plików z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="8d6ac-123">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="8d6ac-124">Instrukcje: Znajdowanie podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="8d6ac-124">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
