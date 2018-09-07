---
title: 'Porady: wyliczanie katalogów i ciągów'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de83395df9e8c89a92e85b96ddd15e9f0be6ad5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067162"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="73292-102">Porady: wyliczanie katalogów i ciągów</span><span class="sxs-lookup"><span data-stu-id="73292-102">How to: Enumerate Directories and Files</span></span>
<span data-ttu-id="73292-103">Za pomocą metody, które zwracają wyliczalny zbiór ciągów ich nazw, można wyliczyć katalogów i plików.</span><span class="sxs-lookup"><span data-stu-id="73292-103">You can enumerate directories and files by using methods that return an enumerable collection of strings of their names.</span></span> <span data-ttu-id="73292-104">Można również użyć metod, które zwracają wyliczalny zbiór <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, lub <xref:System.IO.FileSystemInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="73292-104">You can also use methods that return an enumerable collection of <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span> <span data-ttu-id="73292-105">Przeliczalne kolekcje zapewniają lepszą wydajność niż tablic, podczas pracy z dużych kolekcjach katalogów i plików.</span><span class="sxs-lookup"><span data-stu-id="73292-105">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span>  
  
 <span data-ttu-id="73292-106">Umożliwia także przeliczalne kolekcje uzyskany z tych metod do dostarczania <xref:System.Collections.Generic.IEnumerable%601> parametr dla konstruktorów kolekcji klasy, takie jak <xref:System.Collections.Generic.List%601> klasy.</span><span class="sxs-lookup"><span data-stu-id="73292-106">You can also use enumerable collections obtained from these methods to supply the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes such as the <xref:System.Collections.Generic.List%601> class.</span></span>  
  
 <span data-ttu-id="73292-107">Jeśli chcesz pobrać tylko nazwy katalogów i plików, należy użyć metod wyliczenie <xref:System.IO.Directory> klasy.</span><span class="sxs-lookup"><span data-stu-id="73292-107">If you want to obtain only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="73292-108">Aby uzyskać inne właściwości katalogów i plików, należy użyć <xref:System.IO.DirectoryInfo> i <xref:System.IO.FileSystemInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="73292-108">If you want to obtain other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
 <span data-ttu-id="73292-109">W poniższej tabeli przedstawiono wskazówki do metod, które zwracają przeliczalne kolekcje.</span><span class="sxs-lookup"><span data-stu-id="73292-109">The following table provides a guide to the methods that return enumerable collections.</span></span>  
  
|<span data-ttu-id="73292-110">Aby wyliczyć</span><span class="sxs-lookup"><span data-stu-id="73292-110">To enumerate</span></span>|<span data-ttu-id="73292-111">Wyliczalne kolekcji do zwrócenia</span><span class="sxs-lookup"><span data-stu-id="73292-111">Enumerable collection to return</span></span>|<span data-ttu-id="73292-112">Metoda do użycia</span><span class="sxs-lookup"><span data-stu-id="73292-112">Method to use</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="73292-113">Katalogi</span><span class="sxs-lookup"><span data-stu-id="73292-113">Directories</span></span>|<span data-ttu-id="73292-114">Nazwy katalogów</span><span class="sxs-lookup"><span data-stu-id="73292-114">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="73292-115">Informacje o katalogu (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="73292-115">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="73292-116">Pliki</span><span class="sxs-lookup"><span data-stu-id="73292-116">Files</span></span>|<span data-ttu-id="73292-117">Nazwy plików</span><span class="sxs-lookup"><span data-stu-id="73292-117">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="73292-118">Informacje o pliku (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="73292-118">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="73292-119">Informacje o systemie plików</span><span class="sxs-lookup"><span data-stu-id="73292-119">File system information</span></span>|<span data-ttu-id="73292-120">We wpisach w plikach systemu</span><span class="sxs-lookup"><span data-stu-id="73292-120">File system entries</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="73292-121">Informacje o systemie plików (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="73292-121">File system information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="73292-122">Mimo że można od razu wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego za pomocą <xref:System.IO.SearchOption.AllDirectories> dostarczone przez opcję wyszukiwania <xref:System.IO.SearchOption> wyliczenie, wyjątki przed nieautoryzowanym dostępem (<xref:System.UnauthorizedAccessException>) może spowodować, że wyliczenie do być niekompletne.</span><span class="sxs-lookup"><span data-stu-id="73292-122">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> search option provided by the <xref:System.IO.SearchOption> enumeration, unauthorized access exceptions (<xref:System.UnauthorizedAccessException>) may cause the enumeration to be incomplete.</span></span> <span data-ttu-id="73292-123">Jeśli te wyjątki, można przechwytywać i Kontynuuj, najpierw wyliczanie katalogów i następnie Wyliczanie plików.</span><span class="sxs-lookup"><span data-stu-id="73292-123">If these exceptions are possible, you can catch them and continue by first enumerating directories and then enumerating files.</span></span>  
  
### <a name="to-enumerate-directory-names"></a><span data-ttu-id="73292-124">Aby wyliczyć nazwy katalogów</span><span class="sxs-lookup"><span data-stu-id="73292-124">To enumerate directory names</span></span>  
  
-   <span data-ttu-id="73292-125">Użyj <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodę, aby uzyskać listę nazw własny katalog najwyższego poziomu w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="73292-125">Use the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to obtain a list of the top-level directory names in a specified path.</span></span>  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a><span data-ttu-id="73292-126">Aby wyliczyć nazwy plików w katalogu i podkatalogach</span><span class="sxs-lookup"><span data-stu-id="73292-126">To enumerate file names in a directory and subdirectories</span></span>  
  
-   <span data-ttu-id="73292-127">Użyj <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metody do wyszukiwania i (opcjonalnie) jego podkatalogi katalogu, aby uzyskać listę nazw plików, które pasują do wzorca wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="73292-127">Use the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to search a directory and (optionally) its subdirectories, and to obtain a list of file names that match a specified search pattern.</span></span>  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a><span data-ttu-id="73292-128">Aby wyliczyć kolekcji obiektów DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="73292-128">To enumerate a collection of DirectoryInfo objects</span></span>  
  
-   <span data-ttu-id="73292-129">Użyj <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metodę, aby uzyskać kolekcję katalogów najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="73292-129">Use the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to obtain a collection of top-level directories.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a><span data-ttu-id="73292-130">Aby wyliczyć kolekcji obiektów FileInfo we wszystkich katalogach</span><span class="sxs-lookup"><span data-stu-id="73292-130">To enumerate a collection of FileInfo objects in all directories</span></span>  
  
-   <span data-ttu-id="73292-131">Użyj <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodę, aby uzyskać kolekcję plików, które pasują do wzorca wyszukiwania we wszystkich katalogach.</span><span class="sxs-lookup"><span data-stu-id="73292-131">Use the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to obtain a collection of files that match a specified search pattern in all directories.</span></span> <span data-ttu-id="73292-132">W tym przykładzie najpierw wylicza najwyższego poziomu katalogów przechwytują wyjątki możliwe nieautoryzowanemu dostępowi, a następnie wylicza pliki.</span><span class="sxs-lookup"><span data-stu-id="73292-132">This example first enumerates the top-level directories to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="73292-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73292-133">See also</span></span>

- [<span data-ttu-id="73292-134">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="73292-134">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
