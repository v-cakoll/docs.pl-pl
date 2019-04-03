---
title: Plik jest za duży, aby odczytać z tablicy bajtów
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 0c7d35e08eeb42e35c4c40e47434a64393d829b1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831517"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="d9c24-102">Plik jest za duży, aby odczytać z tablicy bajtów</span><span class="sxs-lookup"><span data-stu-id="d9c24-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="d9c24-103">Rozmiar pliku, który chcesz odczytać do tablicy typu byte przekracza 4 GB.</span><span class="sxs-lookup"><span data-stu-id="d9c24-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="d9c24-104">`My.Computer.FileSystem.ReadAllBytes` Metody nie można odczytać pliku, który przekroczy rozmiar.</span><span class="sxs-lookup"><span data-stu-id="d9c24-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d9c24-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d9c24-105">To correct this error</span></span>  
  
-   <span data-ttu-id="d9c24-106">Użyj <xref:System.IO.StreamReader> można odczytać pliku.</span><span class="sxs-lookup"><span data-stu-id="d9c24-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="d9c24-107">Aby uzyskać więcej informacji, zobacz [podstawowe informacje dotyczące programu .NET Framework We/Wy i System plików (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="d9c24-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c24-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9c24-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="d9c24-109">Dostęp do plików za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9c24-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="d9c24-110">Instrukcje: Odczytywanie tekstu z plików za pomocą StreamReader</span><span class="sxs-lookup"><span data-stu-id="d9c24-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
