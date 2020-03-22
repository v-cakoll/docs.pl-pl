---
title: 'Porady: znajdowanie plików z określonym wzorcem'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 5faaa16615f52714db3de6853786990265716501
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348756"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="dc603-102">Porady: znajdowanie plików z określonym wzorcem w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc603-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="dc603-103">Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> zwraca kolekcję tylko do odczytu ciągów reprezentujących nazwy ścieżek dla plików.</span><span class="sxs-lookup"><span data-stu-id="dc603-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="dc603-104">Za pomocą `wildCards` parametru można określić określony wzorzec.</span><span class="sxs-lookup"><span data-stu-id="dc603-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="dc603-105">Jeśli chcesz dołączyć podkatalogi do wyszukiwania, `searchType` ustaw `SearchOption.SearchAllSubDirectories`parametr na .</span><span class="sxs-lookup"><span data-stu-id="dc603-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="dc603-106">Pusta kolekcja jest zwracana, jeśli nie zostaną znalezione żadne pliki pasujące do określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="dc603-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc603-107">Aby uzyskać informacje na temat zwracania listy `System.IO` plików przy <xref:System.IO.DirectoryInfo.GetFiles%2A>użyciu `DirectoryInfo` klasy obszaru nazw, zobacz .</span><span class="sxs-lookup"><span data-stu-id="dc603-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="dc603-108">Aby znaleźć pliki z określonym wzorem</span><span class="sxs-lookup"><span data-stu-id="dc603-108">To find files with a specified pattern</span></span>  
  
- <span data-ttu-id="dc603-109">Użyj `GetFiles` tej metody, podając nazwę i ścieżkę katalogu, który chcesz przeszukać, i określając wzorzec.</span><span class="sxs-lookup"><span data-stu-id="dc603-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="dc603-110">Poniższy przykład zwraca wszystkie `.dll` pliki z rozszerzeniem w `ListBox1`katalogu i dodaje je do .</span><span class="sxs-lookup"><span data-stu-id="dc603-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="dc603-111">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="dc603-111">.NET Framework Security</span></span>  

 <span data-ttu-id="dc603-112">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="dc603-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="dc603-113">Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="dc603-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="dc603-114">Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).</span><span class="sxs-lookup"><span data-stu-id="dc603-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="dc603-115">`directory`nie istnieje<xref:System.IO.DirectoryNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="dc603-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="dc603-116">`directory`wskazuje istniejący plik<xref:System.IO.IOException>( ).</span><span class="sxs-lookup"><span data-stu-id="dc603-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="dc603-117">Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).</span><span class="sxs-lookup"><span data-stu-id="dc603-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="dc603-118">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="dc603-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="dc603-119">Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).</span><span class="sxs-lookup"><span data-stu-id="dc603-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="dc603-120">Użytkownik nie ma niezbędnych<xref:System.UnauthorizedAccessException>uprawnień ( ).</span><span class="sxs-lookup"><span data-stu-id="dc603-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc603-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc603-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="dc603-122">Porady: znajdowanie podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="dc603-122">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="dc603-123">Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="dc603-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="dc603-124">Porady: pobieranie kolekcji plików z katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc603-124">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
