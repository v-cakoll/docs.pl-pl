---
title: 'Instrukcje: Wyliczanie katalogów i plików'
description: Informacje na temat wyliczania katalogów i plików przy użyciu wyliczalnych kolekcji, które mogą zapewnić lepszą wydajność niż tablice w programie .NET.
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 276668f4a3eee89610a81b1256820770d1f72dc3
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662579"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="a913e-103">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="a913e-103">How to: Enumerate directories and files</span></span>
<span data-ttu-id="a913e-104">Wyliczalne kolekcje zapewniają lepszą wydajność niż tablice podczas pracy z dużymi kolekcjami katalogów i plików.</span><span class="sxs-lookup"><span data-stu-id="a913e-104">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="a913e-105">Aby wyliczyć katalogi i pliki, należy użyć metod, które zwracają wyliczalną kolekcję nazw katalogów lub plików, lub ich <xref:System.IO.DirectoryInfo> , <xref:System.IO.FileInfo> lub <xref:System.IO.FileSystemInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a913e-105">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="a913e-106">Jeśli chcesz wyszukać i zwrócić tylko nazwy katalogów lub plików, użyj metod wyliczenia <xref:System.IO.Directory> klasy.</span><span class="sxs-lookup"><span data-stu-id="a913e-106">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="a913e-107">Jeśli chcesz wyszukać i zwrócić inne właściwości katalogów lub plików, użyj <xref:System.IO.DirectoryInfo> <xref:System.IO.FileSystemInfo> klas i.</span><span class="sxs-lookup"><span data-stu-id="a913e-107">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="a913e-108">Można użyć wyliczalnych kolekcji z tych metod jako <xref:System.Collections.Generic.IEnumerable%601> parametru dla konstruktorów klas kolekcji, takich jak <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="a913e-108">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="a913e-109">Poniższa tabela zawiera podsumowanie metod, które zwracają wyliczalne kolekcje plików i katalogów:</span><span class="sxs-lookup"><span data-stu-id="a913e-109">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="a913e-110">Aby wyszukać i zwrócić</span><span class="sxs-lookup"><span data-stu-id="a913e-110">To search and return</span></span>|<span data-ttu-id="a913e-111">Use, Metoda</span><span class="sxs-lookup"><span data-stu-id="a913e-111">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="a913e-112">Nazwy katalogów</span><span class="sxs-lookup"><span data-stu-id="a913e-112">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a913e-113">Informacje o katalogu ( <xref:System.IO.DirectoryInfo> )</span><span class="sxs-lookup"><span data-stu-id="a913e-113">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a913e-114">Nazwy plików</span><span class="sxs-lookup"><span data-stu-id="a913e-114">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a913e-115">Informacje o pliku ( <xref:System.IO.FileInfo> )</span><span class="sxs-lookup"><span data-stu-id="a913e-115">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a913e-116">Nazwy wpisów systemu plików</span><span class="sxs-lookup"><span data-stu-id="a913e-116">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a913e-117">Informacje o wpisie systemu plików ( <xref:System.IO.FileSystemInfo> )</span><span class="sxs-lookup"><span data-stu-id="a913e-117">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a913e-118">Nazwy katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="a913e-118">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="a913e-119">Chociaż można natychmiast wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego przy użyciu <xref:System.IO.SearchOption.AllDirectories> opcji opcjonalne <xref:System.IO.SearchOption> Wyliczenie, <xref:System.UnauthorizedAccessException> błędy mogą spowodować, że Wyliczenie nie jest kompletne.</span><span class="sxs-lookup"><span data-stu-id="a913e-119">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="a913e-120">Te wyjątki można przechwytywać, wprowadzając najpierw katalogi i wyliczając pliki.</span><span class="sxs-lookup"><span data-stu-id="a913e-120">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="a913e-121">Przykłady: Użyj klasy katalogu</span><span class="sxs-lookup"><span data-stu-id="a913e-121">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="a913e-122">Poniższy przykład używa metody, <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> Aby uzyskać listę nazw katalogów najwyższego poziomu w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="a913e-122">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="a913e-123">Poniższy przykład używa metody, <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> Aby rekursywnie wyliczyć wszystkie nazwy plików w katalogu i podkatalogach zgodnych z określonym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="a913e-123">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="a913e-124">Następnie odczytuje każdy wiersz każdego pliku i wyświetla wiersze zawierające określony ciąg wraz z ich nazwami i ścieżkami.</span><span class="sxs-lookup"><span data-stu-id="a913e-124">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="a913e-125">Przykłady: użycie klasy DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="a913e-125">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="a913e-126">W poniższym przykładzie zastosowano <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metodę, aby wyświetlić kolekcję katalogów najwyższego poziomu, których <xref:System.IO.FileSystemInfo.CreationTimeUtc> wartość jest wcześniejsza niż określona <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="a913e-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="a913e-127">Poniższy przykład używa metody, <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> Aby wyświetlić listę wszystkich plików, których <xref:System.IO.FileInfo.Length> rozmiar przekracza 10 MB.</span><span class="sxs-lookup"><span data-stu-id="a913e-127">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="a913e-128">Ten przykład najpierw wylicza katalogi najwyższego poziomu, aby przechwycić możliwe nieautoryzowane wyjątki dostępu, a następnie wylicza pliki.</span><span class="sxs-lookup"><span data-stu-id="a913e-128">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a913e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a913e-129">See also</span></span>

- [<span data-ttu-id="a913e-130">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="a913e-130">File and stream I/O</span></span>](index.md)
