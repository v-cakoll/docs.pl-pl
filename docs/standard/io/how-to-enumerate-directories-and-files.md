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
ms.openlocfilehash: bcb10426175c1f2cabeec6d8d4f8d2ed74e5e3b4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291880"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="092b2-102">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="092b2-102">How to: Enumerate directories and files</span></span>
<span data-ttu-id="092b2-103">Wyliczalne kolekcje zapewniają lepszą wydajność niż tablice podczas pracy z dużymi kolekcjami katalogów i plików.</span><span class="sxs-lookup"><span data-stu-id="092b2-103">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="092b2-104">Aby wyliczyć katalogi i pliki, należy użyć metod, które zwracają wyliczalną kolekcję nazw katalogów lub plików, lub ich <xref:System.IO.DirectoryInfo> , <xref:System.IO.FileInfo> lub <xref:System.IO.FileSystemInfo> obiektów.</span><span class="sxs-lookup"><span data-stu-id="092b2-104">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="092b2-105">Jeśli chcesz wyszukać i zwrócić tylko nazwy katalogów lub plików, użyj metod wyliczenia <xref:System.IO.Directory> klasy.</span><span class="sxs-lookup"><span data-stu-id="092b2-105">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="092b2-106">Jeśli chcesz wyszukać i zwrócić inne właściwości katalogów lub plików, użyj <xref:System.IO.DirectoryInfo> <xref:System.IO.FileSystemInfo> klas i.</span><span class="sxs-lookup"><span data-stu-id="092b2-106">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="092b2-107">Można użyć wyliczalnych kolekcji z tych metod jako <xref:System.Collections.Generic.IEnumerable%601> parametru dla konstruktorów klas kolekcji, takich jak <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="092b2-107">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="092b2-108">Poniższa tabela zawiera podsumowanie metod, które zwracają wyliczalne kolekcje plików i katalogów:</span><span class="sxs-lookup"><span data-stu-id="092b2-108">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="092b2-109">Aby wyszukać i zwrócić</span><span class="sxs-lookup"><span data-stu-id="092b2-109">To search and return</span></span>|<span data-ttu-id="092b2-110">Use, Metoda</span><span class="sxs-lookup"><span data-stu-id="092b2-110">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="092b2-111">Nazwy katalogów</span><span class="sxs-lookup"><span data-stu-id="092b2-111">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="092b2-112">Informacje o katalogu ( <xref:System.IO.DirectoryInfo> )</span><span class="sxs-lookup"><span data-stu-id="092b2-112">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="092b2-113">Nazwy plików</span><span class="sxs-lookup"><span data-stu-id="092b2-113">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="092b2-114">Informacje o pliku ( <xref:System.IO.FileInfo> )</span><span class="sxs-lookup"><span data-stu-id="092b2-114">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="092b2-115">Nazwy wpisów systemu plików</span><span class="sxs-lookup"><span data-stu-id="092b2-115">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="092b2-116">Informacje o wpisie systemu plików ( <xref:System.IO.FileSystemInfo> )</span><span class="sxs-lookup"><span data-stu-id="092b2-116">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="092b2-117">Nazwy katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="092b2-117">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="092b2-118">Chociaż można natychmiast wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego przy użyciu <xref:System.IO.SearchOption.AllDirectories> opcji opcjonalne <xref:System.IO.SearchOption> Wyliczenie, <xref:System.UnauthorizedAccessException> błędy mogą spowodować, że Wyliczenie nie jest kompletne.</span><span class="sxs-lookup"><span data-stu-id="092b2-118">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="092b2-119">Te wyjątki można przechwytywać, wprowadzając najpierw katalogi i wyliczając pliki.</span><span class="sxs-lookup"><span data-stu-id="092b2-119">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="092b2-120">Przykłady: Użyj klasy katalogu</span><span class="sxs-lookup"><span data-stu-id="092b2-120">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="092b2-121">Poniższy przykład używa metody, <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> Aby uzyskać listę nazw katalogów najwyższego poziomu w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="092b2-121">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="092b2-122">Poniższy przykład używa metody, <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> Aby rekursywnie wyliczyć wszystkie nazwy plików w katalogu i podkatalogach zgodnych z określonym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="092b2-122">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="092b2-123">Następnie odczytuje każdy wiersz każdego pliku i wyświetla wiersze zawierające określony ciąg wraz z ich nazwami i ścieżkami.</span><span class="sxs-lookup"><span data-stu-id="092b2-123">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="092b2-124">Przykłady: użycie klasy DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="092b2-124">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="092b2-125">W poniższym przykładzie zastosowano <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metodę, aby wyświetlić kolekcję katalogów najwyższego poziomu, których <xref:System.IO.FileSystemInfo.CreationTimeUtc> wartość jest wcześniejsza niż określona <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="092b2-125">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="092b2-126">Poniższy przykład używa metody, <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> Aby wyświetlić listę wszystkich plików, których <xref:System.IO.FileInfo.Length> rozmiar przekracza 10 MB.</span><span class="sxs-lookup"><span data-stu-id="092b2-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="092b2-127">Ten przykład najpierw wylicza katalogi najwyższego poziomu, aby przechwycić możliwe nieautoryzowane wyjątki dostępu, a następnie wylicza pliki.</span><span class="sxs-lookup"><span data-stu-id="092b2-127">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="092b2-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="092b2-128">See also</span></span>

- [<span data-ttu-id="092b2-129">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="092b2-129">File and stream I/O</span></span>](index.md)
