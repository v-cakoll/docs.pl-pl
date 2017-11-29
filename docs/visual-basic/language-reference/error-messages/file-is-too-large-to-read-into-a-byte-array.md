---
title: "Plik jest za duży, aby odczytać z tablicy bajtów"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bbdb5a4dcaa22ca84428ef28c8838a6d9a0ee1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="c0bda-102">Plik jest za duży, aby odczytać z tablicy bajtów</span><span class="sxs-lookup"><span data-stu-id="c0bda-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="c0bda-103">Rozmiar pliku, który próbujesz odczytu tablicy bajtów przekracza 4 GB.</span><span class="sxs-lookup"><span data-stu-id="c0bda-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="c0bda-104">`My.Computer.FileSystem.ReadAllBytes` — Metoda nie może odczytać pliku, który przekracza rozmiar.</span><span class="sxs-lookup"><span data-stu-id="c0bda-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c0bda-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c0bda-105">To correct this error</span></span>  
  
-   <span data-ttu-id="c0bda-106">Użyj <xref:System.IO.StreamReader> do odczytu pliku.</span><span class="sxs-lookup"><span data-stu-id="c0bda-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="c0bda-107">Aby uzyskać więcej informacji, zobacz [podstawowe informacje dotyczące programu .NET Framework We/Wy plików i systemu plików (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="c0bda-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0bda-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0bda-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [<span data-ttu-id="c0bda-109">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0bda-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [<span data-ttu-id="c0bda-110">Porady: Odczyt tekstu z plików za pomocą StreamReader</span><span class="sxs-lookup"><span data-stu-id="c0bda-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
