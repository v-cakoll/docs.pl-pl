---
title: Można&#39;t utworzyć niezbędnego pliku tymczasowego
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: fb3a6d02fbe4c6e9f699e503590a7a1825c3e2cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="can39t-create-necessary-temporary-file"></a><span data-ttu-id="d2c3e-102">Można&#39;t utworzyć niezbędnego pliku tymczasowego</span><span class="sxs-lookup"><span data-stu-id="d2c3e-102">Can&#39;t create necessary temporary file</span></span>
<span data-ttu-id="d2c3e-103">Albo dysk jest pełny, zawiera katalog określony przez zmienną środowiskową TEMP lub zmienna środowiskowa TEMP określa nieprawidłowy lub tylko do odczytu dysku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2c3e-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d2c3e-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="d2c3e-105">Usuń pliki z dysku, jeśli jest to pełny.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-105">Delete files from the drive, if full.</span></span>  
  
2.  <span data-ttu-id="d2c3e-106">Określ inny dysk zmienną środowiskową TEMP.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3.  <span data-ttu-id="d2c3e-107">Określ prawidłowy dysk dla zmienną środowiskową TEMP.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4.  <span data-ttu-id="d2c3e-108">Usuń ograniczenie tylko do odczytu z aktualnie określonego dysku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c3e-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2c3e-109">See Also</span></span>  
 [<span data-ttu-id="d2c3e-110">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="d2c3e-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
