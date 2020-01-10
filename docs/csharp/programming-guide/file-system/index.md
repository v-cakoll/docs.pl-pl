---
title: System plików i przewodnik C# programowania w rejestrze
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 2540c816a102a7f11f1f103b993194cccf0f4688
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75704524"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="9adb4-102">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9adb4-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="9adb4-103">W poniższych tematach pokazano, jak C# używać programu i .NET Framework do wykonywania różnych podstawowych operacji dotyczących plików, folderów i rejestru.</span><span class="sxs-lookup"><span data-stu-id="9adb4-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9adb4-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9adb4-104">In This Section</span></span>  
  
|<span data-ttu-id="9adb4-105">**Tytuł**</span><span class="sxs-lookup"><span data-stu-id="9adb4-105">**Title**</span></span>|<span data-ttu-id="9adb4-106">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9adb4-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="9adb4-107">Jak wykonać iterację drzewa katalogów</span><span class="sxs-lookup"><span data-stu-id="9adb4-107">How to iterate through a directory tree</span></span>](./how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="9adb4-108">Pokazuje, jak ręcznie wykonać iterację w drzewie katalogów.</span><span class="sxs-lookup"><span data-stu-id="9adb4-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="9adb4-109">Jak uzyskać informacje o plikach, folderach i dyskach</span><span class="sxs-lookup"><span data-stu-id="9adb4-109">How to get information about files, folders, and drives</span></span>](./how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="9adb4-110">Pokazuje, jak pobierać informacje, takie jak czasy i rozmiary tworzenia, informacje o plikach, folderach i dyskach.</span><span class="sxs-lookup"><span data-stu-id="9adb4-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="9adb4-111">Jak utworzyć plik lub folder</span><span class="sxs-lookup"><span data-stu-id="9adb4-111">How to create a file or folder</span></span>](./how-to-create-a-file-or-folder.md)|<span data-ttu-id="9adb4-112">Pokazuje, jak utworzyć nowy plik lub folder.</span><span class="sxs-lookup"><span data-stu-id="9adb4-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="9adb4-113">Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="9adb4-113">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="9adb4-114">Pokazuje, jak kopiować, usuwać i przenosić pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="9adb4-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="9adb4-115">Jak zapewnić okno dialogowe postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="9adb4-115">How to provide a progress dialog box for file operations</span></span>](./how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="9adb4-116">Pokazuje sposób wyświetlania standardowego okna dialogowego postępu systemu Windows dla określonych operacji na plikach.</span><span class="sxs-lookup"><span data-stu-id="9adb4-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="9adb4-117">Jak zapisać w pliku tekstowym</span><span class="sxs-lookup"><span data-stu-id="9adb4-117">How to write to a text file</span></span>](./how-to-write-to-a-text-file.md)|<span data-ttu-id="9adb4-118">Pokazuje, jak zapisywać w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="9adb4-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="9adb4-119">Jak czytać z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="9adb4-119">How to read from a text file</span></span>](./how-to-read-from-a-text-file.md)|<span data-ttu-id="9adb4-120">Pokazuje, jak czytać z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="9adb4-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="9adb4-121">Jak czytać plik tekstowy po jednym wierszu</span><span class="sxs-lookup"><span data-stu-id="9adb4-121">How to read a text file one line at a time</span></span>](./how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="9adb4-122">Pokazuje, jak pobrać tekst z pliku po jednym wierszu naraz.</span><span class="sxs-lookup"><span data-stu-id="9adb4-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="9adb4-123">Jak utworzyć klucz w rejestrze</span><span class="sxs-lookup"><span data-stu-id="9adb4-123">How to create a key in the registry</span></span>](./how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="9adb4-124">Pokazuje, w jaki sposób napisać klucz do rejestru systemowego.</span><span class="sxs-lookup"><span data-stu-id="9adb4-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="9adb4-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9adb4-125">Related Sections</span></span>  
 [<span data-ttu-id="9adb4-126">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="9adb4-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="9adb4-127">Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="9adb4-127">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)
  
 [<span data-ttu-id="9adb4-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9adb4-128">C# Programming Guide</span></span>](../index.md)  
  
 [<span data-ttu-id="9adb4-129">Pliki, foldery i dyski</span><span class="sxs-lookup"><span data-stu-id="9adb4-129">Files, Folders and Drives</span></span>](./index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
