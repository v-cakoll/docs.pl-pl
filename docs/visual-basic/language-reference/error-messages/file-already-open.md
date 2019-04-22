---
title: Plik jest już otwarty
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 401801c7c9072ce11f9eafdb84f2b377669ae545
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770363"
---
# <a name="file-already-open"></a><span data-ttu-id="609d8-102">Plik jest już otwarty</span><span class="sxs-lookup"><span data-stu-id="609d8-102">File already open</span></span>
<span data-ttu-id="609d8-103">Czasami pliku muszą zostać zamknięte przed inny `FileOpen` lub może wystąpić inna operacja.</span><span class="sxs-lookup"><span data-stu-id="609d8-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="609d8-104">Wśród możliwe przyczyny tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="609d8-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="609d8-105">Tryb sekwencyjne dane wyjściowe `FileOpen` operacja została wykonana dla pliku, który jest już otwarty</span><span class="sxs-lookup"><span data-stu-id="609d8-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="609d8-106">Oświadczenie odnosi się do otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="609d8-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="609d8-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="609d8-107">To correct this error</span></span>  
  
1. <span data-ttu-id="609d8-108">Zamknij plik przed wykonaniem instrukcji.</span><span class="sxs-lookup"><span data-stu-id="609d8-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609d8-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="609d8-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
