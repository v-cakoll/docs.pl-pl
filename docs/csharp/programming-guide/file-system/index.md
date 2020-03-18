---
title: System plików i rejestr - Przewodnik po programowaniu C#
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: f160df456f1a3437e11de2d3660d158ae4d4bb67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75900565"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="fb6b7-102">System plików i rejestr (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="fb6b7-102">File system and the registry (C# Programming Guide)</span></span>

<span data-ttu-id="fb6b7-103">W poniższych artykułach przedstawiono sposób wykonywania różnych podstawowych operacji na plikach, folderach i rejestrze za pomocą c# i .NET.</span><span class="sxs-lookup"><span data-stu-id="fb6b7-103">The following articles show how to use C# and .NET to perform various basic operations on files, folders, and the registry.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fb6b7-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fb6b7-104">In this section</span></span>

|<span data-ttu-id="fb6b7-105">**Tytuł**</span><span class="sxs-lookup"><span data-stu-id="fb6b7-105">**Title**</span></span>|<span data-ttu-id="fb6b7-106">**Opis**</span><span class="sxs-lookup"><span data-stu-id="fb6b7-106">**Description**</span></span>|
|---------------|---------------------|
|[<span data-ttu-id="fb6b7-107">Iterowanie drzewa katalogów</span><span class="sxs-lookup"><span data-stu-id="fb6b7-107">How to iterate through a directory tree</span></span>](how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="fb6b7-108">Pokazuje, jak ręcznie iterate przez drzewo katalogów.</span><span class="sxs-lookup"><span data-stu-id="fb6b7-108">Shows how to manually iterate through a directory tree.</span></span>|
|[<span data-ttu-id="fb6b7-109">Pobieranie informacji o plikach, folderach i dyskach</span><span class="sxs-lookup"><span data-stu-id="fb6b7-109">How to get information about files, folders, and drives</span></span>](how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="fb6b7-110">Pokazuje, jak pobierać informacje, takie jak czas i rozmiar tworzenia, o plikach, folderach i dyskach.</span><span class="sxs-lookup"><span data-stu-id="fb6b7-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|
|[<span data-ttu-id="fb6b7-111">Tworzenie pliku lub folderu</span><span class="sxs-lookup"><span data-stu-id="fb6b7-111">How to create a file or folder</span></span>](how-to-create-a-file-or-folder.md)|<span data-ttu-id="fb6b7-112">Pokazuje, jak utworzyć nowy plik lub folder.</span><span class="sxs-lookup"><span data-stu-id="fb6b7-112">Shows how to create a new file or folder.</span></span>|
|[<span data-ttu-id="fb6b7-113">Jak kopiować, usuwać i przenosić pliki i foldery (Przewodnik po programowaniu języka C#)</span><span class="sxs-lookup"><span data-stu-id="fb6b7-113">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="fb6b7-114">Pokazuje, jak kopiować, usuwać i przenosić pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="fb6b7-114">Shows how to copy, delete and move files and folders.</span></span>|
|[<span data-ttu-id="fb6b7-115">Dostarczanie okna dialogowego postępu dla operacji na plikach</span><span class="sxs-lookup"><span data-stu-id="fb6b7-115">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="fb6b7-116">Pokazuje, jak wyświetlić standardowe okno dialogowe postępu systemu Windows dla niektórych operacji na plikach.</span><span class="sxs-lookup"><span data-stu-id="fb6b7-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|
|[<span data-ttu-id="fb6b7-117">Zapisywanie do pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="fb6b7-117">How to write to a text file</span></span>](how-to-write-to-a-text-file.md)|<span data-ttu-id="fb6b7-118">Pokazuje, jak zapisywać do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="fb6b7-118">Shows how to write to a text file.</span></span>|
|[<span data-ttu-id="fb6b7-119">Jak czytać z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="fb6b7-119">How to read from a text file</span></span>](how-to-read-from-a-text-file.md)|<span data-ttu-id="fb6b7-120">Pokazuje, jak czytać z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="fb6b7-120">Shows how to read from a text file.</span></span>|
|[<span data-ttu-id="fb6b7-121">Odczytywanie pliku tekstowego po jednym wierszu</span><span class="sxs-lookup"><span data-stu-id="fb6b7-121">How to read a text file one line at a time</span></span>](how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="fb6b7-122">Pokazuje, jak pobierać tekst z pliku po jednym wierszu naraz.</span><span class="sxs-lookup"><span data-stu-id="fb6b7-122">Shows how to retrieve text from a file one line at a time.</span></span>|
|[<span data-ttu-id="fb6b7-123">Tworzenie klucza w rejestrze</span><span class="sxs-lookup"><span data-stu-id="fb6b7-123">How to create a key in the registry</span></span>](how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="fb6b7-124">Pokazuje, jak napisać klucz do rejestru systemowego.</span><span class="sxs-lookup"><span data-stu-id="fb6b7-124">Shows how to write a key to the system registry.</span></span>|

## <a name="related-sections"></a><span data-ttu-id="fb6b7-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fb6b7-125">Related sections</span></span>

- [<span data-ttu-id="fb6b7-126">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="fb6b7-126">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="fb6b7-127">Jak kopiować, usuwać i przenosić pliki i foldery (Przewodnik po programowaniu języka C#)</span><span class="sxs-lookup"><span data-stu-id="fb6b7-127">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)
- [<span data-ttu-id="fb6b7-128">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="fb6b7-128">C# Programming Guide</span></span>](../index.md)
- <xref:System.IO?displayProperty=nameWithType>
