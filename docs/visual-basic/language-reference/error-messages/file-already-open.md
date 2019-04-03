---
title: Plik jest już otwarty
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: e565dbd6352a8f76290f3f58d62e2e14a18ef45f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823509"
---
# <a name="file-already-open"></a><span data-ttu-id="b9e10-102">Plik jest już otwarty</span><span class="sxs-lookup"><span data-stu-id="b9e10-102">File already open</span></span>
<span data-ttu-id="b9e10-103">Czasami pliku muszą zostać zamknięte przed inny `FileOpen` lub może wystąpić inna operacja.</span><span class="sxs-lookup"><span data-stu-id="b9e10-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="b9e10-104">Wśród możliwe przyczyny tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="b9e10-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="b9e10-105">Tryb sekwencyjne dane wyjściowe `FileOpen` operacja została wykonana dla pliku, który jest już otwarty</span><span class="sxs-lookup"><span data-stu-id="b9e10-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="b9e10-106">Oświadczenie odnosi się do otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9e10-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b9e10-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b9e10-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="b9e10-108">Zamknij plik przed wykonaniem instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b9e10-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e10-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9e10-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
