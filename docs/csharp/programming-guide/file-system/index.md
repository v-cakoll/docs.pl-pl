---
title: System plików i rejestr (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 20e8b857759253736d11bc31988fadb4843fa87a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="d006e-102">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d006e-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="d006e-103">W następujących tematach opisano sposób użycia języka C# i .NET Framework do wykonywania podstawowych operacji różnych plików, folderów i rejestru.</span><span class="sxs-lookup"><span data-stu-id="d006e-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d006e-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d006e-104">In This Section</span></span>  
  
|<span data-ttu-id="d006e-105">**Tytuł**</span><span class="sxs-lookup"><span data-stu-id="d006e-105">**Title**</span></span>|<span data-ttu-id="d006e-106">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d006e-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="d006e-107">Instrukcje: iterowanie drzewa katalogów</span><span class="sxs-lookup"><span data-stu-id="d006e-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="d006e-108">Pokazano, jak ręcznie Iterowanie drzewa katalogów.</span><span class="sxs-lookup"><span data-stu-id="d006e-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="d006e-109">Porady: uzyskiwanie informacji o plikach, folderach i dyskach</span><span class="sxs-lookup"><span data-stu-id="d006e-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="d006e-110">Pokazuje, jak pobrać informacje takie jak czas tworzenia i rozmiar o plikach, folderach i dyskach.</span><span class="sxs-lookup"><span data-stu-id="d006e-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="d006e-111">Instrukcje: utworzenie pliku lub folderu</span><span class="sxs-lookup"><span data-stu-id="d006e-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="d006e-112">Przedstawia sposób tworzenia nowego pliku lub folderu.</span><span class="sxs-lookup"><span data-stu-id="d006e-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="d006e-113">Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="d006e-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="d006e-114">Pokazano, jak kopiowanie, usuwanie i przenoszenie plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="d006e-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="d006e-115">Instrukcje: dostarczanie okna dialogowego postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="d006e-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="d006e-116">Przedstawia sposób wyświetlania standardowe okno dialogowe postępu systemu Windows, dla niektórych operacji na plikach.</span><span class="sxs-lookup"><span data-stu-id="d006e-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="d006e-117">Instrukcje: zapisywanie do pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="d006e-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="d006e-118">Pokazuje, jak można zapisać do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="d006e-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="d006e-119">Instrukcje: odczytywanie z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="d006e-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="d006e-120">Pokazuje, jak można odczytać z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="d006e-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="d006e-121">Porady: Odczyt pliku tekstowego po jednym wierszu naraz</span><span class="sxs-lookup"><span data-stu-id="d006e-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="d006e-122">Pokazuje, jak pobrać tekstu z pliku jednego wiersza w czasie.</span><span class="sxs-lookup"><span data-stu-id="d006e-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="d006e-123">Porady: Tworzenie klucza w rejestrze</span><span class="sxs-lookup"><span data-stu-id="d006e-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="d006e-124">Pokazuje, jak zapisać klucza rejestru systemu.</span><span class="sxs-lookup"><span data-stu-id="d006e-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="d006e-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d006e-125">Related Sections</span></span>  
 [<span data-ttu-id="d006e-126">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="d006e-126">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
  
 [<span data-ttu-id="d006e-127">Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="d006e-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="d006e-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d006e-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="d006e-129">Pliki, foldery i dyski</span><span class="sxs-lookup"><span data-stu-id="d006e-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
