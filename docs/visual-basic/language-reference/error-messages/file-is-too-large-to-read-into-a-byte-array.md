---
title: Plik jest za duży, aby odczytać z tablicy bajtów
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 1b04d47cab77269a0ce84ef77c162a4401d99d9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585928"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="03777-102">Plik jest za duży, aby odczytać z tablicy bajtów</span><span class="sxs-lookup"><span data-stu-id="03777-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="03777-103">Rozmiar pliku, który próbujesz odczytu tablicy bajtów przekracza 4 GB.</span><span class="sxs-lookup"><span data-stu-id="03777-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="03777-104">`My.Computer.FileSystem.ReadAllBytes` — Metoda nie może odczytać pliku, który przekracza rozmiar.</span><span class="sxs-lookup"><span data-stu-id="03777-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="03777-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="03777-105">To correct this error</span></span>  
  
-   <span data-ttu-id="03777-106">Użyj <xref:System.IO.StreamReader> do odczytu pliku.</span><span class="sxs-lookup"><span data-stu-id="03777-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="03777-107">Aby uzyskać więcej informacji, zobacz [podstawowe informacje dotyczące programu .NET Framework We/Wy plików i systemu plików (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="03777-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03777-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03777-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [<span data-ttu-id="03777-109">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03777-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [<span data-ttu-id="03777-110">Instrukcje: odczyt tekstu z plików za pomocą StreamReader</span><span class="sxs-lookup"><span data-stu-id="03777-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
