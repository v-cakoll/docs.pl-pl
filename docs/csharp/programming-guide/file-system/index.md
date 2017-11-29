---
title: "System plików i rejestr (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d1b4e3fa9b6c6da89abd242be855e9fb7c16dd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="3bb8c-102">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3bb8c-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="3bb8c-103">W następujących tematach opisano sposób użycia języka C# i .NET Framework do wykonywania podstawowych operacji różnych plików, folderów i rejestru.</span><span class="sxs-lookup"><span data-stu-id="3bb8c-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bb8c-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3bb8c-104">In This Section</span></span>  
  
|<span data-ttu-id="3bb8c-105">**Tytuł**</span><span class="sxs-lookup"><span data-stu-id="3bb8c-105">**Title**</span></span>|<span data-ttu-id="3bb8c-106">**Opis**</span><span class="sxs-lookup"><span data-stu-id="3bb8c-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="3bb8c-107">Porady: iterowanie drzewa katalogów</span><span class="sxs-lookup"><span data-stu-id="3bb8c-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="3bb8c-108">Pokazano, jak ręcznie Iterowanie drzewa katalogów.</span><span class="sxs-lookup"><span data-stu-id="3bb8c-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="3bb8c-109">Porady: uzyskiwanie informacji o plikach, folderach i dyskach</span><span class="sxs-lookup"><span data-stu-id="3bb8c-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="3bb8c-110">Pokazuje, jak pobrać informacje takie jak czas tworzenia i rozmiar o plikach, folderach i dyskach.</span><span class="sxs-lookup"><span data-stu-id="3bb8c-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="3bb8c-111">Porady: Tworzenie pliku lub folderu</span><span class="sxs-lookup"><span data-stu-id="3bb8c-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="3bb8c-112">Przedstawia sposób tworzenia nowego pliku lub folderu.</span><span class="sxs-lookup"><span data-stu-id="3bb8c-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="3bb8c-113">Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="3bb8c-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="3bb8c-114">Pokazano, jak kopiowanie, usuwanie i przenoszenie plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="3bb8c-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="3bb8c-115">Porady: dostarczanie okna dialogowego postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="3bb8c-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="3bb8c-116">Przedstawia sposób wyświetlania standardowe okno dialogowe postępu systemu Windows, dla niektórych operacji na plikach.</span><span class="sxs-lookup"><span data-stu-id="3bb8c-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="3bb8c-117">Porady: zapis do pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="3bb8c-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="3bb8c-118">Pokazuje, jak można zapisać do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="3bb8c-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="3bb8c-119">Porady: Odczyt z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="3bb8c-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="3bb8c-120">Pokazuje, jak można odczytać z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="3bb8c-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="3bb8c-121">Porady: Odczyt pliku tekstowego po jednym wierszu naraz</span><span class="sxs-lookup"><span data-stu-id="3bb8c-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="3bb8c-122">Pokazuje, jak pobrać tekstu z pliku jednego wiersza w czasie.</span><span class="sxs-lookup"><span data-stu-id="3bb8c-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="3bb8c-123">Porady: Tworzenie klucza w rejestrze</span><span class="sxs-lookup"><span data-stu-id="3bb8c-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="3bb8c-124">Pokazuje, jak zapisać klucza rejestru systemu.</span><span class="sxs-lookup"><span data-stu-id="3bb8c-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="3bb8c-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3bb8c-125">Related Sections</span></span>  
 [<span data-ttu-id="3bb8c-126">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="3bb8c-126">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
  
 [<span data-ttu-id="3bb8c-127">Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="3bb8c-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="3bb8c-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3bb8c-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="3bb8c-129">Pliki, foldery i dyski</span><span class="sxs-lookup"><span data-stu-id="3bb8c-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
