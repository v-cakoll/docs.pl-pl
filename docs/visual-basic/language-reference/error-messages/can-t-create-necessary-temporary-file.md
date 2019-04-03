---
title: Nie można utworzyć niezbędnego pliku tymczasowego
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: 7887c04d57291703b4e69d528b7b191376d1262a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819024"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="1380b-102">Nie można utworzyć niezbędnego pliku tymczasowego</span><span class="sxs-lookup"><span data-stu-id="1380b-102">Can't create necessary temporary file</span></span>
<span data-ttu-id="1380b-103">Albo dysk jest pełny, zawierający określony przez zmienną środowiskową TEMP katalog lub zmienna środowiskowa TEMP określa nieprawidłowy lub tylko do odczytu dysku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="1380b-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1380b-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1380b-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="1380b-105">Usuń pliki z dysku, jeśli jest to pełna.</span><span class="sxs-lookup"><span data-stu-id="1380b-105">Delete files from the drive, if full.</span></span>  
  
2.  <span data-ttu-id="1380b-106">Określ inny dysk w zmienna środowiskowa TEMP.</span><span class="sxs-lookup"><span data-stu-id="1380b-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3.  <span data-ttu-id="1380b-107">Określ prawidłowy dysk zmienna środowiskowa TEMP.</span><span class="sxs-lookup"><span data-stu-id="1380b-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4.  <span data-ttu-id="1380b-108">Usuń ograniczenia tylko do odczytu z aktualnie określony dysk lub katalog.</span><span class="sxs-lookup"><span data-stu-id="1380b-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1380b-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1380b-109">See also</span></span>

- [<span data-ttu-id="1380b-110">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="1380b-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
