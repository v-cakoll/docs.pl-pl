---
title: File Access
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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348896"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="a62b1-102">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a62b1-102">File Access with Visual Basic</span></span>

<span data-ttu-id="a62b1-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span><span class="sxs-lookup"><span data-stu-id="a62b1-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="a62b1-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span><span class="sxs-lookup"><span data-stu-id="a62b1-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="a62b1-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span><span class="sxs-lookup"><span data-stu-id="a62b1-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a62b1-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a62b1-106">In This Section</span></span>  

 [<span data-ttu-id="a62b1-107">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="a62b1-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="a62b1-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span><span class="sxs-lookup"><span data-stu-id="a62b1-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="a62b1-109">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="a62b1-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="a62b1-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span><span class="sxs-lookup"><span data-stu-id="a62b1-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="a62b1-111">Tworzenie, usuwanie i przenoszenie plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="a62b1-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="a62b1-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span><span class="sxs-lookup"><span data-stu-id="a62b1-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="a62b1-113">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="a62b1-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="a62b1-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span><span class="sxs-lookup"><span data-stu-id="a62b1-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="a62b1-115">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="a62b1-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="a62b1-116">Describes file encodings and their use.</span><span class="sxs-lookup"><span data-stu-id="a62b1-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="a62b1-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a62b1-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="a62b1-118">Demonstrates how to create a utility that reports information about files and folders.</span><span class="sxs-lookup"><span data-stu-id="a62b1-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="a62b1-119">Rozwiązywanie problemów: odczytywanie z plików tekstowych oraz zapisywanie w nich</span><span class="sxs-lookup"><span data-stu-id="a62b1-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="a62b1-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span><span class="sxs-lookup"><span data-stu-id="a62b1-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
