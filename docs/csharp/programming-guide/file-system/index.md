---
title: System plików i przewodnik C# programowania w rejestrze
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: ef6c1da09ea0435643caba0f5e2819c064f8db01
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589909"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="cb023-102">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="cb023-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="cb023-103">W poniższych tematach pokazano, jak C# używać programu i .NET Framework do wykonywania różnych podstawowych operacji dotyczących plików, folderów i rejestru.</span><span class="sxs-lookup"><span data-stu-id="cb023-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb023-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cb023-104">In This Section</span></span>  
  
|<span data-ttu-id="cb023-105">**Tytuł**</span><span class="sxs-lookup"><span data-stu-id="cb023-105">**Title**</span></span>|<span data-ttu-id="cb023-106">**Opis**</span><span class="sxs-lookup"><span data-stu-id="cb023-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="cb023-107">Instrukcje: Wykonaj iterację drzewa katalogów</span><span class="sxs-lookup"><span data-stu-id="cb023-107">How to: Iterate Through a Directory Tree</span></span>](./how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="cb023-108">Pokazuje, jak ręcznie wykonać iterację w drzewie katalogów.</span><span class="sxs-lookup"><span data-stu-id="cb023-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="cb023-109">Instrukcje: Pobieranie informacji o plikach, folderach i dyskach</span><span class="sxs-lookup"><span data-stu-id="cb023-109">How to: Get Information About Files, Folders, and Drives</span></span>](./how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="cb023-110">Pokazuje, jak pobierać informacje, takie jak czasy i rozmiary tworzenia, informacje o plikach, folderach i dyskach.</span><span class="sxs-lookup"><span data-stu-id="cb023-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="cb023-111">Instrukcje: Utwórz plik lub folder</span><span class="sxs-lookup"><span data-stu-id="cb023-111">How to: Create a File or Folder</span></span>](./how-to-create-a-file-or-folder.md)|<span data-ttu-id="cb023-112">Pokazuje, jak utworzyć nowy plik lub folder.</span><span class="sxs-lookup"><span data-stu-id="cb023-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="cb023-113">Instrukcje: Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="cb023-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="cb023-114">Pokazuje, jak kopiować, usuwać i przenosić pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="cb023-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="cb023-115">Instrukcje: Udostępnianie okna dialogowego postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="cb023-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](./how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="cb023-116">Pokazuje sposób wyświetlania standardowego okna dialogowego postępu systemu Windows dla określonych operacji na plikach.</span><span class="sxs-lookup"><span data-stu-id="cb023-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="cb023-117">Instrukcje: Zapisz w pliku tekstowym</span><span class="sxs-lookup"><span data-stu-id="cb023-117">How to: Write to a Text File</span></span>](./how-to-write-to-a-text-file.md)|<span data-ttu-id="cb023-118">Pokazuje, jak zapisywać w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="cb023-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="cb023-119">Instrukcje: Odczytaj z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="cb023-119">How to: Read From a Text File</span></span>](./how-to-read-from-a-text-file.md)|<span data-ttu-id="cb023-120">Pokazuje, jak czytać z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="cb023-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="cb023-121">Instrukcje: Odczytywanie pliku tekstowego po jednym wierszu</span><span class="sxs-lookup"><span data-stu-id="cb023-121">How to: Read a Text File One Line at a Time</span></span>](./how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="cb023-122">Pokazuje, jak pobrać tekst z pliku po jednym wierszu naraz.</span><span class="sxs-lookup"><span data-stu-id="cb023-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="cb023-123">Instrukcje: Tworzenie klucza w rejestrze</span><span class="sxs-lookup"><span data-stu-id="cb023-123">How to: Create a Key In the Registry</span></span>](./how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="cb023-124">Pokazuje, w jaki sposób napisać klucz do rejestru systemowego.</span><span class="sxs-lookup"><span data-stu-id="cb023-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="cb023-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="cb023-125">Related Sections</span></span>  
 [<span data-ttu-id="cb023-126">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="cb023-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="cb023-127">Instrukcje: Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="cb023-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="cb023-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cb023-128">C# Programming Guide</span></span>](../index.md)  
  
 [<span data-ttu-id="cb023-129">Pliki, foldery i dyski</span><span class="sxs-lookup"><span data-stu-id="cb023-129">Files, Folders and Drives</span></span>](./index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
