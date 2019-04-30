---
title: System plików i rejestru — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 64c852e6fcc034cb56651ffc2d22fa5323bbb54f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680067"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="83843-102">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="83843-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="83843-103">Poniższe tematy przedstawiają, jak różne podstawowe operacje wykonywane na pliki, foldery i rejestru za pomocą języka C# i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83843-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83843-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="83843-104">In This Section</span></span>  
  
|<span data-ttu-id="83843-105">**Tytuł**</span><span class="sxs-lookup"><span data-stu-id="83843-105">**Title**</span></span>|<span data-ttu-id="83843-106">**Opis**</span><span class="sxs-lookup"><span data-stu-id="83843-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="83843-107">Instrukcje: Iterowanie drzewa katalogu</span><span class="sxs-lookup"><span data-stu-id="83843-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="83843-108">Pokazuje, jak ręcznie wykonać iterację drzewa katalogów.</span><span class="sxs-lookup"><span data-stu-id="83843-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="83843-109">Instrukcje: Pobierz informacje o plikach, folderach i dyskach</span><span class="sxs-lookup"><span data-stu-id="83843-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="83843-110">Pokazuje, jak pobrać informacje takie jak czasy tworzenia i rozmiar, o plikach, folderach i dyskach.</span><span class="sxs-lookup"><span data-stu-id="83843-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="83843-111">Instrukcje: Utworzenie pliku lub folderu</span><span class="sxs-lookup"><span data-stu-id="83843-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="83843-112">Przedstawia sposób tworzenia nowego pliku lub folderu.</span><span class="sxs-lookup"><span data-stu-id="83843-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="83843-113">Instrukcje: Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="83843-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="83843-114">Pokazuje, jak kopiowanie, usuwanie i przenoszenie plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="83843-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="83843-115">Instrukcje: Dostarczanie okna dialogowego postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="83843-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="83843-116">Pokazuje sposób wyświetlania standardowe okno dialogowe postępu Windows, dla niektórych operacji na plikach.</span><span class="sxs-lookup"><span data-stu-id="83843-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="83843-117">Instrukcje: Zapis do pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="83843-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="83843-118">Pokazuje, jak można zapisać do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="83843-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="83843-119">Instrukcje: Odczyt z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="83843-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="83843-120">Pokazuje, jak można odczytać z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="83843-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="83843-121">Instrukcje: Przeczytaj jeden wiersz pliku tekstowego w czasie</span><span class="sxs-lookup"><span data-stu-id="83843-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="83843-122">Pokazuje, jak pobieranie tekstu ze jeden wiersz pliku naraz.</span><span class="sxs-lookup"><span data-stu-id="83843-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="83843-123">Instrukcje: Utwórz klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="83843-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="83843-124">Pokazuje, jak zapisać klucza rejestru systemu.</span><span class="sxs-lookup"><span data-stu-id="83843-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="83843-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="83843-125">Related Sections</span></span>  
 [<span data-ttu-id="83843-126">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="83843-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="83843-127">Instrukcje: Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="83843-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="83843-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="83843-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="83843-129">Plikach, folderach i dyskach</span><span class="sxs-lookup"><span data-stu-id="83843-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
