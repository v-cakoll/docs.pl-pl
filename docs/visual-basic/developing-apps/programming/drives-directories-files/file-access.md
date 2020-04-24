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
ms.openlocfilehash: 22bcd0f1f3acb0c0ad899b83ad2d879ead948f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348896"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="86a2b-102">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86a2b-102">File Access with Visual Basic</span></span>

<span data-ttu-id="86a2b-103">`My.Computer.FileSystem` Obiekt zawiera narzędzia do pracy z plikami i folderami.</span><span class="sxs-lookup"><span data-stu-id="86a2b-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="86a2b-104">Jego właściwości, metody i zdarzenia umożliwiają tworzenie, kopiowanie, przenoszenie, badanie i usuwanie plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="86a2b-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="86a2b-105">`My.Computer.FileSystem`zapewnia lepszą wydajność niż starsze`FileOpen`funkcje (, `FileClose`, `Input` `InputString` `LineInput`,, itp.) zapewniane przez Visual Basic w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="86a2b-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86a2b-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="86a2b-106">In This Section</span></span>  

 [<span data-ttu-id="86a2b-107">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="86a2b-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="86a2b-108">Wyświetla listę tematów dotyczących używania `My.Computer.FileSystem` obiektu do odczytu z plików</span><span class="sxs-lookup"><span data-stu-id="86a2b-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="86a2b-109">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="86a2b-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="86a2b-110">Wyświetla listę tematów dotyczących używania `My.Computer.FileSystem` obiektu do zapisywania w plikach</span><span class="sxs-lookup"><span data-stu-id="86a2b-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="86a2b-111">Tworzenie, usuwanie i przenoszenie plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="86a2b-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="86a2b-112">Wyświetla listę tematów dotyczących używania `My.Computer.FileSystem` obiektu do tworzenia, kopiowania, usuwania i przemieszczania plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="86a2b-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="86a2b-113">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="86a2b-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="86a2b-114">W tym artykule omówiono sposób `TextFieldReader` użycia programu do analizowania plików tekstowych, takich jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="86a2b-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="86a2b-115">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="86a2b-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="86a2b-116">Opisuje Kodowanie plików i ich użycie.</span><span class="sxs-lookup"><span data-stu-id="86a2b-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="86a2b-117">Wskazówki: manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86a2b-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="86a2b-118">Pokazuje, jak utworzyć narzędzie, które raportuje informacje o plikach i folderach.</span><span class="sxs-lookup"><span data-stu-id="86a2b-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="86a2b-119">Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="86a2b-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="86a2b-120">Wyświetla listę typowych problemów występujących podczas odczytywania i zapisywania w plikach tekstowych oraz sugeruje metody zaradcze dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="86a2b-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
