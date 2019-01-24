---
title: Można&#39;t utworzyć niezbędnego pliku tymczasowego
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: c10444129f2a57bfef7f523a291e0f6d30e68d85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610373"
---
# <a name="can39t-create-necessary-temporary-file"></a><span data-ttu-id="0f3d3-102">Można&#39;t utworzyć niezbędnego pliku tymczasowego</span><span class="sxs-lookup"><span data-stu-id="0f3d3-102">Can&#39;t create necessary temporary file</span></span>
<span data-ttu-id="0f3d3-103">Albo dysk jest pełny, zawierający określony przez zmienną środowiskową TEMP katalog lub zmienna środowiskowa TEMP określa nieprawidłowy lub tylko do odczytu dysku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="0f3d3-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f3d3-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0f3d3-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="0f3d3-105">Usuń pliki z dysku, jeśli jest to pełna.</span><span class="sxs-lookup"><span data-stu-id="0f3d3-105">Delete files from the drive, if full.</span></span>  
  
2.  <span data-ttu-id="0f3d3-106">Określ inny dysk w zmienna środowiskowa TEMP.</span><span class="sxs-lookup"><span data-stu-id="0f3d3-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3.  <span data-ttu-id="0f3d3-107">Określ prawidłowy dysk zmienna środowiskowa TEMP.</span><span class="sxs-lookup"><span data-stu-id="0f3d3-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4.  <span data-ttu-id="0f3d3-108">Usuń ograniczenia tylko do odczytu z aktualnie określony dysk lub katalog.</span><span class="sxs-lookup"><span data-stu-id="0f3d3-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f3d3-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f3d3-109">See also</span></span>
- [<span data-ttu-id="0f3d3-110">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="0f3d3-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
