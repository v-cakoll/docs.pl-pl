---
title: Przetwarzanie dysków, katalogów i plików (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aad7ea3a24bf0f738999c58a7934d1ffcf92b967
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="3fbd5-102">Przetwarzanie dysków, katalogów i plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fbd5-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>
<span data-ttu-id="3fbd5-103">Visual Basic umożliwia przetwarzanie dysków, folderów i plików z `My.Computer.FileSystem` obiektu, który zapewnia lepszą wydajność i łatwiej używać od metod tradycyjnych, takich jak `FileOpen` i `Write` funkcje (chociaż są one nadal dostępna).</span><span class="sxs-lookup"><span data-stu-id="3fbd5-103">You can use Visual Basic to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="3fbd5-104">W poniższych sekcjach omówiono te metody szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="3fbd5-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3fbd5-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3fbd5-105">In This Section</span></span>  
 [<span data-ttu-id="3fbd5-106">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3fbd5-106">File Access with Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 <span data-ttu-id="3fbd5-107">W tym artykule omówiono sposób użycia `My.Computer.FileSystem` obiekt do pracy z plikami, dyski i foldery.</span><span class="sxs-lookup"><span data-stu-id="3fbd5-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="3fbd5-108">Podstawowe informacje o .NET Framework File I/O i systemie plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fbd5-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="3fbd5-109">Omówienie pojęć we/wy pliku w programie .NET Framework, w tym strumieni, izolowanego magazynu, zdarzenia pliku, atrybuty pliku i dostęp do plików.</span><span class="sxs-lookup"><span data-stu-id="3fbd5-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="3fbd5-110">Przewodnik: manipulowanie plikami za pomocą metod .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3fbd5-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="3fbd5-111">Pokazuje, jak używać [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] do manipulowania pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="3fbd5-111">Demonstrates how to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="3fbd5-112">Wskazówki: Manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3fbd5-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="3fbd5-113">Pokazuje, jak używać `My.Computer.FileSystem` obiekt do manipulowania pliki i foldery.</span><span class="sxs-lookup"><span data-stu-id="3fbd5-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3fbd5-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3fbd5-114">Related Sections</span></span>  
 [<span data-ttu-id="3fbd5-115">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="3fbd5-115">Program Structure and Code Conventions</span></span>](../../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="3fbd5-116">Wskazówki dla struktury fizyczne i wygląd programów.</span><span class="sxs-lookup"><span data-stu-id="3fbd5-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="3fbd5-117">Odwołanie dokumentacji `My.Computer.FileSystem` obiekt i jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="3fbd5-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
