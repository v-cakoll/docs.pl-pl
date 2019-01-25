---
title: Plik jest już otwarty
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: cda72e03eb5c2469b8106957a0c50fbfa5314549
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567038"
---
# <a name="file-already-open"></a><span data-ttu-id="86886-102">Plik jest już otwarty</span><span class="sxs-lookup"><span data-stu-id="86886-102">File already open</span></span>
<span data-ttu-id="86886-103">Czasami pliku muszą zostać zamknięte przed inny `FileOpen` lub może wystąpić inna operacja.</span><span class="sxs-lookup"><span data-stu-id="86886-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="86886-104">Wśród możliwe przyczyny tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="86886-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="86886-105">Tryb sekwencyjne dane wyjściowe `FileOpen` operacja została wykonana dla pliku, który jest już otwarty</span><span class="sxs-lookup"><span data-stu-id="86886-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="86886-106">Oświadczenie odnosi się do otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="86886-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="86886-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="86886-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="86886-108">Zamknij plik przed wykonaniem instrukcji.</span><span class="sxs-lookup"><span data-stu-id="86886-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86886-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86886-109">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
