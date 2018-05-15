---
title: Dostęp do plików za pomocą Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- file access
- files [Visual Basic], input and output
- file access, Visual Basic
- files [Visual Basic], I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files [Visual Basic], accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
ms.openlocfilehash: f9cbb255dea8c6915951b5099f40bfd0ba66c8aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="25836-102">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25836-102">File Access with Visual Basic</span></span>
<span data-ttu-id="25836-103">`My.Computer.FileSystem` Obiektu zawiera narzędzia do pracy z plikami i folderami.</span><span class="sxs-lookup"><span data-stu-id="25836-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="25836-104">Jego właściwości, metod i zdarzeń umożliwiają tworzenie, skopiować, przenieść, badanie i usuwać pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="25836-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="25836-105">`My.Computer.FileSystem` zapewnia lepszą wydajność niż funkcje starszej wersji (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, itd.) są dostarczane przez program Visual Basic dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="25836-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25836-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="25836-106">In This Section</span></span>  
 [<span data-ttu-id="25836-107">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="25836-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="25836-108">Lista tematów dotyczących przy użyciu `My.Computer.FileSystem` obiektu odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="25836-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="25836-109">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="25836-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="25836-110">Lista tematów dotyczących przy użyciu `My.Computer.FileSystem` obiektu do zapisania plików</span><span class="sxs-lookup"><span data-stu-id="25836-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="25836-111">Tworzenie, usuwanie i przenoszenie plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="25836-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="25836-112">Lista tematów dotyczących przy użyciu `My.Computer.FileSystem` obiekt do tworzenia, kopiowanie, usuwanie i przenoszenie plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="25836-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="25836-113">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="25836-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="25836-114">W tym artykule omówiono sposób użycia `TextFieldReader` do analizowania plików tekstowych, takich jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="25836-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="25836-115">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="25836-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="25836-116">Opisuje kodowanie pliku oraz ich używania.</span><span class="sxs-lookup"><span data-stu-id="25836-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="25836-117">Wskazówki: Manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25836-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="25836-118">Przedstawia sposób tworzenia narzędzia, która raportuje informacje o plikach i folderach.</span><span class="sxs-lookup"><span data-stu-id="25836-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="25836-119">Rozwiązywanie problemów: odczytywanie z plików tekstowych oraz zapisywanie w nich</span><span class="sxs-lookup"><span data-stu-id="25836-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="25836-120">Wymieniono typowe problemy występujące podczas odczytywania i zapisywania plików, a także sugeruje środki zaradcze dla każdego.</span><span class="sxs-lookup"><span data-stu-id="25836-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
