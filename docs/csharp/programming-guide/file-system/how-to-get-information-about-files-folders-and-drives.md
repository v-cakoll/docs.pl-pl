---
title: Jak uzyskać informacje o plikach, folderach i dyskach — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 6024b1be4ce826900c6f9b367323fb19ac55d2c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705213"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="4b30c-102">Jak uzyskać informacje o plikach, folderach i dyskach (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="4b30c-102">How to get information about files, folders, and drives  (C# Programming Guide)</span></span>
<span data-ttu-id="4b30c-103">W .NET Framework można uzyskać dostęp do informacji o systemie plików przy użyciu następujących klas:</span><span class="sxs-lookup"><span data-stu-id="4b30c-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="4b30c-104">Klasy <xref:System.IO.FileInfo> i <xref:System.IO.DirectoryInfo> reprezentują plik lub katalog i zawierają właściwości, które uwidaczniają wiele atrybutów plików obsługiwanych przez system plików NTFS.</span><span class="sxs-lookup"><span data-stu-id="4b30c-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="4b30c-105">Zawierają również metody otwierania, zamykania, przechodzenia i usuwania plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="4b30c-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="4b30c-106">Wystąpienia tych klas można utworzyć, przekazując ciąg, który reprezentuje nazwę pliku, folderu lub dysku w konstruktorze:</span><span class="sxs-lookup"><span data-stu-id="4b30c-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="4b30c-107">Możesz również uzyskać nazwy plików, folderów lub dysków, korzystając z wywołań do <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>i <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b30c-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="4b30c-108">Klasy <xref:System.IO.Directory?displayProperty=nameWithType> i <xref:System.IO.File?displayProperty=nameWithType> zapewniają metody statyczne do pobierania informacji o katalogach i plikach.</span><span class="sxs-lookup"><span data-stu-id="4b30c-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b30c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b30c-109">Example</span></span>  
 <span data-ttu-id="4b30c-110">W poniższym przykładzie przedstawiono różne sposoby uzyskiwania dostępu do informacji o plikach i folderach.</span><span class="sxs-lookup"><span data-stu-id="4b30c-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4b30c-111">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="4b30c-111">Robust Programming</span></span>  
 <span data-ttu-id="4b30c-112">Podczas przetwarzania ciągów ścieżki określonych przez użytkownika należy również obsługiwać wyjątki dla następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="4b30c-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
- <span data-ttu-id="4b30c-113">Nazwa pliku jest źle sformułowana.</span><span class="sxs-lookup"><span data-stu-id="4b30c-113">The file name is malformed.</span></span> <span data-ttu-id="4b30c-114">Na przykład zawiera nieprawidłowe znaki lub tylko odstęp.</span><span class="sxs-lookup"><span data-stu-id="4b30c-114">For example, it contains invalid characters or only white space.</span></span>  
  
- <span data-ttu-id="4b30c-115">Nazwa pliku ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="4b30c-115">The file name is null.</span></span>  
  
- <span data-ttu-id="4b30c-116">Nazwa pliku jest dłuższa niż zdefiniowana w systemie długość maksymalna.</span><span class="sxs-lookup"><span data-stu-id="4b30c-116">The file name is longer than the system-defined maximum length.</span></span>  
  
- <span data-ttu-id="4b30c-117">Nazwa pliku zawiera dwukropek (:).</span><span class="sxs-lookup"><span data-stu-id="4b30c-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="4b30c-118">Jeśli aplikacja nie ma wystarczających uprawnień do odczytu określonego pliku, Metoda `Exists` zwraca `false` niezależnie od tego, czy ścieżka istnieje; Metoda nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4b30c-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b30c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b30c-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="4b30c-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4b30c-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4b30c-121">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="4b30c-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
