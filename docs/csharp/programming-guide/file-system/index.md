---
title: System plików i przewodnik C# programowania w rejestrze
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: f160df456f1a3437e11de2d3660d158ae4d4bb67
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900565"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="a5f24-102">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="a5f24-102">File system and the registry (C# Programming Guide)</span></span>

<span data-ttu-id="a5f24-103">W poniższych artykułach pokazano, jak C# używać programu i .NET do wykonywania różnych podstawowych operacji dotyczących plików, folderów i rejestru.</span><span class="sxs-lookup"><span data-stu-id="a5f24-103">The following articles show how to use C# and .NET to perform various basic operations on files, folders, and the registry.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a5f24-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a5f24-104">In this section</span></span>

|<span data-ttu-id="a5f24-105">**Tytuł**</span><span class="sxs-lookup"><span data-stu-id="a5f24-105">**Title**</span></span>|<span data-ttu-id="a5f24-106">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a5f24-106">**Description**</span></span>|
|---------------|---------------------|
|[<span data-ttu-id="a5f24-107">Jak wykonać iterację drzewa katalogów</span><span class="sxs-lookup"><span data-stu-id="a5f24-107">How to iterate through a directory tree</span></span>](how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="a5f24-108">Pokazuje, jak ręcznie wykonać iterację w drzewie katalogów.</span><span class="sxs-lookup"><span data-stu-id="a5f24-108">Shows how to manually iterate through a directory tree.</span></span>|
|[<span data-ttu-id="a5f24-109">Jak uzyskać informacje o plikach, folderach i dyskach</span><span class="sxs-lookup"><span data-stu-id="a5f24-109">How to get information about files, folders, and drives</span></span>](how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="a5f24-110">Pokazuje, jak pobierać informacje, takie jak czasy i rozmiary tworzenia, informacje o plikach, folderach i dyskach.</span><span class="sxs-lookup"><span data-stu-id="a5f24-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|
|[<span data-ttu-id="a5f24-111">Jak utworzyć plik lub folder</span><span class="sxs-lookup"><span data-stu-id="a5f24-111">How to create a file or folder</span></span>](how-to-create-a-file-or-folder.md)|<span data-ttu-id="a5f24-112">Pokazuje, jak utworzyć nowy plik lub folder.</span><span class="sxs-lookup"><span data-stu-id="a5f24-112">Shows how to create a new file or folder.</span></span>|
|[<span data-ttu-id="a5f24-113">Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="a5f24-113">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="a5f24-114">Pokazuje, jak kopiować, usuwać i przenosić pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="a5f24-114">Shows how to copy, delete and move files and folders.</span></span>|
|[<span data-ttu-id="a5f24-115">Jak zapewnić okno dialogowe postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="a5f24-115">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="a5f24-116">Pokazuje sposób wyświetlania standardowego okna dialogowego postępu systemu Windows dla określonych operacji na plikach.</span><span class="sxs-lookup"><span data-stu-id="a5f24-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|
|[<span data-ttu-id="a5f24-117">Jak zapisać w pliku tekstowym</span><span class="sxs-lookup"><span data-stu-id="a5f24-117">How to write to a text file</span></span>](how-to-write-to-a-text-file.md)|<span data-ttu-id="a5f24-118">Pokazuje, jak zapisywać w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="a5f24-118">Shows how to write to a text file.</span></span>|
|[<span data-ttu-id="a5f24-119">Jak czytać z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="a5f24-119">How to read from a text file</span></span>](how-to-read-from-a-text-file.md)|<span data-ttu-id="a5f24-120">Pokazuje, jak czytać z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="a5f24-120">Shows how to read from a text file.</span></span>|
|[<span data-ttu-id="a5f24-121">Jak czytać plik tekstowy po jednym wierszu</span><span class="sxs-lookup"><span data-stu-id="a5f24-121">How to read a text file one line at a time</span></span>](how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="a5f24-122">Pokazuje, jak pobrać tekst z pliku po jednym wierszu naraz.</span><span class="sxs-lookup"><span data-stu-id="a5f24-122">Shows how to retrieve text from a file one line at a time.</span></span>|
|[<span data-ttu-id="a5f24-123">Jak utworzyć klucz w rejestrze</span><span class="sxs-lookup"><span data-stu-id="a5f24-123">How to create a key in the registry</span></span>](how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="a5f24-124">Pokazuje, w jaki sposób napisać klucz do rejestru systemowego.</span><span class="sxs-lookup"><span data-stu-id="a5f24-124">Shows how to write a key to the system registry.</span></span>|

## <a name="related-sections"></a><span data-ttu-id="a5f24-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a5f24-125">Related sections</span></span>

- [<span data-ttu-id="a5f24-126">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="a5f24-126">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="a5f24-127">Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="a5f24-127">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)
- [<span data-ttu-id="a5f24-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a5f24-128">C# Programming Guide</span></span>](../index.md)
- <xref:System.IO?displayProperty=nameWithType>
