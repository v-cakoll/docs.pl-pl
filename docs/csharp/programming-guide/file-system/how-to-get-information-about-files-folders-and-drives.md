---
title: 'Porady: pobieranie informacji o plikach, folderach i dyskach (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: c4f29cd2ae65fb05a2636ae3674c7ffd1613b0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="656b2-102">Porady: pobieranie informacji o plikach, folderach i dyskach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="656b2-102">How to: Get Information About Files, Folders, and Drives  (C# Programming Guide)</span></span>
<span data-ttu-id="656b2-103">W programie .NET Framework aby dostęp do informacji o systemie plików przy użyciu następujących klas:</span><span class="sxs-lookup"><span data-stu-id="656b2-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="656b2-104"><xref:System.IO.FileInfo> i <xref:System.IO.DirectoryInfo> klasy reprezentują pliku lub katalogu i zawierają właściwości, które udostępniają wiele atrybutów plików, które są obsługiwane przez system plików NTFS.</span><span class="sxs-lookup"><span data-stu-id="656b2-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="656b2-105">Zawierają one również metody do otwierania, zamykania, przenoszenie i usuwanie plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="656b2-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="656b2-106">Można utworzyć wystąpieniami tych klas przez przekazanie ciąg reprezentujący nazwę pliku, folderu lub dysku w Konstruktorze:</span><span class="sxs-lookup"><span data-stu-id="656b2-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="656b2-107">Możesz również uzyskać nazwy plików, folderów lub stacji dysków przy użyciu wywołania <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, i <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="656b2-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="656b2-108"><xref:System.IO.Directory?displayProperty=nameWithType> i <xref:System.IO.File?displayProperty=nameWithType> klasy Podaj metody statyczne do pobierania informacji o katalogów i plików.</span><span class="sxs-lookup"><span data-stu-id="656b2-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="656b2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="656b2-109">Example</span></span>  
 <span data-ttu-id="656b2-110">Poniższy przykład przedstawia różne sposoby dostęp do informacji dotyczących plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="656b2-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="656b2-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="656b2-111">Robust Programming</span></span>  
 <span data-ttu-id="656b2-112">W przypadku przetwarzania ciągów ścieżka określona przez użytkownika również powinna obsługiwać wyjątki dla następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="656b2-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
-   <span data-ttu-id="656b2-113">Nazwa pliku jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="656b2-113">The file name is malformed.</span></span> <span data-ttu-id="656b2-114">Na przykład zawiera nieprawidłowe znaki lub białych znaków.</span><span class="sxs-lookup"><span data-stu-id="656b2-114">For example, it contains invalid characters or only white space.</span></span>  
  
-   <span data-ttu-id="656b2-115">Nazwa pliku ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="656b2-115">The file name is null.</span></span>  
  
-   <span data-ttu-id="656b2-116">Nazwa pliku jest dłuższa niż zdefiniowana w systemie długość maksymalna.</span><span class="sxs-lookup"><span data-stu-id="656b2-116">The file name is longer than the system-defined maximum length.</span></span>  
  
-   <span data-ttu-id="656b2-117">Nazwa pliku zawiera dwukropek (:).</span><span class="sxs-lookup"><span data-stu-id="656b2-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="656b2-118">Jeśli aplikacja nie ma wystarczających uprawnień do odczytu określonego pliku `Exists` metoda zwraca `false` niezależnie od tego, czy ścieżka istnieje; metoda zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="656b2-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="656b2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="656b2-119">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="656b2-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="656b2-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="656b2-121">System plików i rejestr (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="656b2-121">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
