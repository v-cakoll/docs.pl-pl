---
title: "Dostęp do plików za pomocą Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9929061feeccee31028056bc93f0f0a2f119eb4e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="a2650-102">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2650-102">File Access with Visual Basic</span></span>
<span data-ttu-id="a2650-103">`My.Computer.FileSystem` Obiektu zawiera narzędzia do pracy z plikami i folderami.</span><span class="sxs-lookup"><span data-stu-id="a2650-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="a2650-104">Jego właściwości, metod i zdarzeń umożliwiają tworzenie, skopiować, przenieść, badanie i usuwać pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="a2650-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="a2650-105">`My.Computer.FileSystem`zapewnia lepszą wydajność niż funkcje starszej wersji (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, itd.) są dostarczane przez [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="a2650-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2650-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a2650-106">In This Section</span></span>  
 [<span data-ttu-id="a2650-107">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="a2650-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="a2650-108">Lista tematów dotyczących przy użyciu `My.Computer.FileSystem` obiektu odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="a2650-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="a2650-109">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="a2650-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="a2650-110">Lista tematów dotyczących przy użyciu `My.Computer.FileSystem` obiektu do zapisania plików</span><span class="sxs-lookup"><span data-stu-id="a2650-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="a2650-111">Tworzenie, usuwanie i przenoszenie plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="a2650-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="a2650-112">Lista tematów dotyczących przy użyciu `My.Computer.FileSystem` obiekt do tworzenia, kopiowanie, usuwanie i przenoszenie plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="a2650-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="a2650-113">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="a2650-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="a2650-114">W tym artykule omówiono sposób użycia `TextFieldReader` do analizowania plików tekstowych, takich jak dzienniki.</span><span class="sxs-lookup"><span data-stu-id="a2650-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="a2650-115">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="a2650-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="a2650-116">Opisuje kodowanie pliku oraz ich używania.</span><span class="sxs-lookup"><span data-stu-id="a2650-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="a2650-117">Wskazówki: Manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2650-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="a2650-118">Przedstawia sposób tworzenia narzędzia, która raportuje informacje o plikach i folderach.</span><span class="sxs-lookup"><span data-stu-id="a2650-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="a2650-119">Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="a2650-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="a2650-120">Wymieniono typowe problemy występujące podczas odczytywania i zapisywania plików, a także sugeruje środki zaradcze dla każdego.</span><span class="sxs-lookup"><span data-stu-id="a2650-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
