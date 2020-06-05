---
title: Dostęp do plików
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
ms.openlocfilehash: 3b2042862ae81a52d62374e35a456766ed47edc9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401735"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="dee69-102">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dee69-102">File Access with Visual Basic</span></span>

<span data-ttu-id="dee69-103">`My.Computer.FileSystem`Obiekt zawiera narzędzia do pracy z plikami i folderami.</span><span class="sxs-lookup"><span data-stu-id="dee69-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="dee69-104">Jego właściwości, metody i zdarzenia umożliwiają tworzenie, kopiowanie, przenoszenie, badanie i usuwanie plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="dee69-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="dee69-105">`My.Computer.FileSystem`zapewnia lepszą wydajność niż starsze funkcje ( `FileOpen` ,,,, `FileClose` `Input` `InputString` `LineInput` itp.) zapewniane przez Visual Basic w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="dee69-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dee69-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dee69-106">In This Section</span></span>  

 [<span data-ttu-id="dee69-107">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="dee69-107">Reading from Files</span></span>](reading-from-files.md)  
 <span data-ttu-id="dee69-108">Wyświetla listę tematów dotyczących używania `My.Computer.FileSystem` obiektu do odczytu z plików</span><span class="sxs-lookup"><span data-stu-id="dee69-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="dee69-109">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="dee69-109">Writing to Files</span></span>](writing-to-files.md)  
 <span data-ttu-id="dee69-110">Wyświetla listę tematów dotyczących używania `My.Computer.FileSystem` obiektu do zapisywania w plikach</span><span class="sxs-lookup"><span data-stu-id="dee69-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="dee69-111">Tworzenie, usuwanie i przenoszenie plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="dee69-111">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="dee69-112">Wyświetla listę tematów dotyczących używania `My.Computer.FileSystem` obiektu do tworzenia, kopiowania, usuwania i przemieszczania plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="dee69-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="dee69-113">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="dee69-113">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="dee69-114">W tym artykule omówiono sposób użycia programu `TextFieldReader` do analizowania plików tekstowych, takich jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="dee69-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="dee69-115">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="dee69-115">File Encodings</span></span>](file-encodings.md)  
 <span data-ttu-id="dee69-116">Opisuje Kodowanie plików i ich użycie.</span><span class="sxs-lookup"><span data-stu-id="dee69-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="dee69-117">Wskazówki: manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dee69-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="dee69-118">Pokazuje, jak utworzyć narzędzie, które raportuje informacje o plikach i folderach.</span><span class="sxs-lookup"><span data-stu-id="dee69-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="dee69-119">Rozwiązywanie problemów: Odczytywanie z plików tekstowych oraz zapisywanie w nich</span><span class="sxs-lookup"><span data-stu-id="dee69-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="dee69-120">Wyświetla listę typowych problemów występujących podczas odczytywania i zapisywania w plikach tekstowych oraz sugeruje metody zaradcze dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="dee69-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
