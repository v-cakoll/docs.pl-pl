---
title: 'Jak: Wyliczanie katalogów i plików'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 6a26d0ef529b81976c4d2caafed34bb5f08d8d46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707748"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="411b3-102">Jak: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="411b3-102">How to: Enumerate directories and files</span></span>
<span data-ttu-id="411b3-103">Kolekcje wyliczalne zapewniają lepszą wydajność niż tablice podczas pracy z dużymi kolekcjami katalogów i plików.</span><span class="sxs-lookup"><span data-stu-id="411b3-103">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="411b3-104">Aby wyliczyć katalogi i pliki, należy użyć metod zwracających wyliczoną <xref:System.IO.DirectoryInfo> <xref:System.IO.FileInfo>kolekcję <xref:System.IO.FileSystemInfo> nazw katalogów lub plików lub ich , lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="411b3-104">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="411b3-105">Jeśli chcesz wyszukać i zwrócić tylko nazwy katalogów lub plików, użyj <xref:System.IO.Directory> metod wyliczenia klasy.</span><span class="sxs-lookup"><span data-stu-id="411b3-105">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="411b3-106">Jeśli chcesz wyszukać i zwrócić inne właściwości katalogów <xref:System.IO.DirectoryInfo> lub <xref:System.IO.FileSystemInfo> plików, należy użyć i klas.</span><span class="sxs-lookup"><span data-stu-id="411b3-106">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="411b3-107">Można użyć niezliczonych kolekcji z tych <xref:System.Collections.Generic.IEnumerable%601> metod jako parametru dla <xref:System.Collections.Generic.List%601>konstruktorów klas kolekcji, takich jak .</span><span class="sxs-lookup"><span data-stu-id="411b3-107">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="411b3-108">W poniższej tabeli podsumowano metody zwracające wyliczalne kolekcje plików i katalogów:</span><span class="sxs-lookup"><span data-stu-id="411b3-108">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="411b3-109">Aby wyszukać i powrócić</span><span class="sxs-lookup"><span data-stu-id="411b3-109">To search and return</span></span>|<span data-ttu-id="411b3-110">Użyj metody</span><span class="sxs-lookup"><span data-stu-id="411b3-110">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="411b3-111">Nazwy katalogów</span><span class="sxs-lookup"><span data-stu-id="411b3-111">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="411b3-112">Informacje katalogowe (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="411b3-112">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="411b3-113">Nazwy plików</span><span class="sxs-lookup"><span data-stu-id="411b3-113">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="411b3-114">Informacje o<xref:System.IO.FileInfo>pliku ( )</span><span class="sxs-lookup"><span data-stu-id="411b3-114">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="411b3-115">Nazwy wejściówek systemu plików</span><span class="sxs-lookup"><span data-stu-id="411b3-115">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="411b3-116">Informacje o wpisie systemu plików (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="411b3-116">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="411b3-117">Nazwy katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="411b3-117">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="411b3-118">Chociaż można natychmiast wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego przy użyciu <xref:System.IO.SearchOption.AllDirectories> opcji opcjonalnego <xref:System.IO.SearchOption> wyliczenia, błędy mogą sprawić, <xref:System.UnauthorizedAccessException> że wyliczenie będzie niekompletne.</span><span class="sxs-lookup"><span data-stu-id="411b3-118">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="411b3-119">Można przechwycić te wyjątki, najpierw wyliczając katalogi, a następnie wyliczając pliki.</span><span class="sxs-lookup"><span data-stu-id="411b3-119">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="411b3-120">Przykłady: Użyj klasy Directory</span><span class="sxs-lookup"><span data-stu-id="411b3-120">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="411b3-121">W poniższym <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> przykładzie użyto metody, aby uzyskać listę nazw katalogów najwyższego poziomu w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="411b3-121">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="411b3-122">W poniższym <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> przykładzie użyto metody do rekursyjnie wyliczyć wszystkie nazwy plików w katalogu i podkatalogów, które pasują do określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="411b3-122">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="411b3-123">Następnie odczytuje każdy wiersz każdego pliku i wyświetla wiersze zawierające określony ciąg, z ich nazwami plików i ścieżkami.</span><span class="sxs-lookup"><span data-stu-id="411b3-123">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="411b3-124">Przykłady: Użyj klasy DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="411b3-124">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="411b3-125">W poniższym <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> przykładzie użyto metody do listy kolekcji <xref:System.IO.FileSystemInfo.CreationTimeUtc> katalogów najwyższego <xref:System.DateTime> poziomu, których jest wcześniejsza niż określona wartość.</span><span class="sxs-lookup"><span data-stu-id="411b3-125">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="411b3-126">W poniższym <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> przykładzie użyto metody <xref:System.IO.FileInfo.Length> do listy wszystkich plików, których przekracza 10 MB.</span><span class="sxs-lookup"><span data-stu-id="411b3-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="411b3-127">W tym przykładzie najpierw wylicza katalogi najwyższego poziomu, aby przechwycić możliwe wyjątki nieautoryzowanego dostępu, a następnie wylicza pliki.</span><span class="sxs-lookup"><span data-stu-id="411b3-127">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="411b3-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="411b3-128">See also</span></span>

- [<span data-ttu-id="411b3-129">Plik i strumień we/wy</span><span class="sxs-lookup"><span data-stu-id="411b3-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
