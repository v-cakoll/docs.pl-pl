---
title: 'Instrukcje: Znajdowanie podkatalogów z określonym wzorcem w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: df5376155d20ec4809962a26c92167eee6568dc1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972849"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="505ce-102">Instrukcje: Znajdowanie podkatalogów z określonym wzorcem w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="505ce-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="505ce-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Metoda zwraca kolekcję tylko do odczytu ciągów reprezentujących nazwy ścieżek do podkatalogów w katalogu.</span><span class="sxs-lookup"><span data-stu-id="505ce-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="505ce-104">Możesz użyć `wildCards` parametru do określenia określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="505ce-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="505ce-105">Jeśli chcesz uwzględnić zawartość podkatalogów w wyszukiwaniu, ustaw `searchType` parametr `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="505ce-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="505ce-106">Jeśli nie zostaną znalezione żadne katalogi pasujących do wybranego wzorca, zwracany jest pustą kolekcją.</span><span class="sxs-lookup"><span data-stu-id="505ce-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="505ce-107">Aby znaleźć podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="505ce-107">To find subdirectories with a specific pattern</span></span>  
  
-   <span data-ttu-id="505ce-108">Użyj `GetDirectories` metody, podając nazwę i ścieżkę do katalogu, który chcesz wyszukać.</span><span class="sxs-lookup"><span data-stu-id="505ce-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="505ce-109">Poniższy przykład zwraca wszystkie katalogi w strukturze katalogów, które zawierają słowo "Dzienniki" w nazwie i doda je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="505ce-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="505ce-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="505ce-110">Robust Programming</span></span>  
 <span data-ttu-id="505ce-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="505ce-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="505ce-112">Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="505ce-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="505ce-113">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="505ce-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="505ce-114">Co najmniej jeden określony symboli wieloznacznych jest `Nothing`, ciągiem pustym lub zawiera tylko spacje (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="505ce-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="505ce-115">`directory` nie istnieje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="505ce-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="505ce-116">`directory` wskazuje na istniejący plik (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="505ce-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="505ce-117">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="505ce-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="505ce-118">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="505ce-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="505ce-119">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="505ce-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="505ce-120">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="505ce-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="505ce-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="505ce-121">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="505ce-122">Instrukcje: Znajdowanie plików z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="505ce-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
