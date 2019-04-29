---
title: Nie można utworzyć niezbędnego pliku tymczasowego
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: 658c2ab1dc210bf472646bce529ae5ffd7f67bc5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649988"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="93a85-102">Nie można utworzyć niezbędnego pliku tymczasowego</span><span class="sxs-lookup"><span data-stu-id="93a85-102">Can't create necessary temporary file</span></span>
<span data-ttu-id="93a85-103">Albo dysk jest pełny, zawierający określony przez zmienną środowiskową TEMP katalog lub zmienna środowiskowa TEMP określa nieprawidłowy lub tylko do odczytu dysku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="93a85-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="93a85-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="93a85-104">To correct this error</span></span>  
  
1. <span data-ttu-id="93a85-105">Usuń pliki z dysku, jeśli jest to pełna.</span><span class="sxs-lookup"><span data-stu-id="93a85-105">Delete files from the drive, if full.</span></span>  
  
2. <span data-ttu-id="93a85-106">Określ inny dysk w zmienna środowiskowa TEMP.</span><span class="sxs-lookup"><span data-stu-id="93a85-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3. <span data-ttu-id="93a85-107">Określ prawidłowy dysk zmienna środowiskowa TEMP.</span><span class="sxs-lookup"><span data-stu-id="93a85-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4. <span data-ttu-id="93a85-108">Usuń ograniczenia tylko do odczytu z aktualnie określony dysk lub katalog.</span><span class="sxs-lookup"><span data-stu-id="93a85-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a85-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93a85-109">See also</span></span>

- [<span data-ttu-id="93a85-110">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="93a85-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
