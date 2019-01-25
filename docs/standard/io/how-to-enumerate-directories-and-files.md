---
title: 'Instrukcje: Wyliczanie katalogów i plików'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463c751ab03875b6af89c325981c65b7bc69d0ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580463"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="31d81-102">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="31d81-102">How to: Enumerate directories and files</span></span>
<span data-ttu-id="31d81-103">Przeliczalne kolekcje zapewniają lepszą wydajność niż tablic, podczas pracy z dużych kolekcjach katalogów i plików.</span><span class="sxs-lookup"><span data-stu-id="31d81-103">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="31d81-104">Aby wyliczanie katalogów i plików, należy użyć metody, które zwracają wyliczalny zbiór nazwy pliku lub katalogu, lub ich <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, lub <xref:System.IO.FileSystemInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="31d81-104">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="31d81-105">Jeśli chcesz wyszukać i zwrócić tylko nazwy katalogów i plików, należy użyć metod wyliczenie <xref:System.IO.Directory> klasy.</span><span class="sxs-lookup"><span data-stu-id="31d81-105">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="31d81-106">Jeśli chcesz wyszukać i zwrócić inne właściwości katalogów i plików, użyj <xref:System.IO.DirectoryInfo> i <xref:System.IO.FileSystemInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="31d81-106">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="31d81-107">Możesz użyć przeliczalne kolekcje z tych metod jako <xref:System.Collections.Generic.IEnumerable%601> parametr konstruktory klas kolekcji, takie jak <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="31d81-107">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="31d81-108">W poniższej tabeli przedstawiono metody, które zwracają przeliczalne kolekcje plików i katalogów:</span><span class="sxs-lookup"><span data-stu-id="31d81-108">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="31d81-109">Aby wyszukać i zwrócić</span><span class="sxs-lookup"><span data-stu-id="31d81-109">To search and return</span></span>|<span data-ttu-id="31d81-110">Użyj metody</span><span class="sxs-lookup"><span data-stu-id="31d81-110">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="31d81-111">Nazwy katalogów</span><span class="sxs-lookup"><span data-stu-id="31d81-111">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31d81-112">Informacje o katalogu (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="31d81-112">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31d81-113">Nazwy plików</span><span class="sxs-lookup"><span data-stu-id="31d81-113">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31d81-114">Informacje o pliku (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="31d81-114">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31d81-115">Nazwy wpisów systemu plików</span><span class="sxs-lookup"><span data-stu-id="31d81-115">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31d81-116">Plik informacji o systemie wejścia (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="31d81-116">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31d81-117">Nazwy katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="31d81-117">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="31d81-118">Mimo że można od razu wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego za pomocą <xref:System.IO.SearchOption.AllDirectories> możliwości opcjonalny <xref:System.IO.SearchOption> wyliczenia, <xref:System.UnauthorizedAccessException> błędy pomijana wyliczenia niekompletne.</span><span class="sxs-lookup"><span data-stu-id="31d81-118">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="31d81-119">Najpierw wyliczanie katalogów, a następnie Wyliczanie plików może przechwytywać te wyjątki.</span><span class="sxs-lookup"><span data-stu-id="31d81-119">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="31d81-120">Przykłady: Korzystanie z klasy katalogu</span><span class="sxs-lookup"><span data-stu-id="31d81-120">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="31d81-121">W poniższym przykładzie użyto <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodę, aby uzyskać listę nazw własny katalog najwyższego poziomu w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="31d81-121">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="31d81-122">W poniższym przykładzie użyto <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metody rekursywnie wyliczyć wszystkie nazwy plików w katalogu i podkatalogów, które pasują do określonych wzorca.</span><span class="sxs-lookup"><span data-stu-id="31d81-122">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="31d81-123">Następnie odczytuje każdej linii każdego pliku i wyświetla wiersze zawierające określony ciąg, wraz z ich nazw plików i ścieżek.</span><span class="sxs-lookup"><span data-stu-id="31d81-123">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="31d81-124">Przykłady: Korzystanie z klasy DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="31d81-124">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="31d81-125">W poniższym przykładzie użyto <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metody, aby wyświetlić listę kolekcji katalogów najwyższego poziomu którego <xref:System.IO.FileSystemInfo.CreationTimeUtc> jest starsza niż określony <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="31d81-125">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="31d81-126">W poniższym przykładzie użyto <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodę, aby wyświetlić listę wszystkich plików, których <xref:System.IO.FileInfo.Length> przekracza 10 MB.</span><span class="sxs-lookup"><span data-stu-id="31d81-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="31d81-127">W tym przykładzie najpierw wylicza najwyższego poziomu katalogów przechwytują wyjątki możliwe nieautoryzowanym dostępem i następnie wylicza pliki.</span><span class="sxs-lookup"><span data-stu-id="31d81-127">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="31d81-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31d81-128">See also</span></span>

[<span data-ttu-id="31d81-129">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="31d81-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
