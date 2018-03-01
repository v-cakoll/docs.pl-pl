---
title: "Może & #39; t utworzyć niezbędnego pliku tymczasowego"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbb1c65318f954249da097b026583b09ad340e20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="can39t-create-necessary-temporary-file"></a><span data-ttu-id="96f45-102">Może & #39; t utworzyć niezbędnego pliku tymczasowego</span><span class="sxs-lookup"><span data-stu-id="96f45-102">Can&#39;t create necessary temporary file</span></span>
<span data-ttu-id="96f45-103">Albo dysk jest pełny, zawiera katalog określony przez zmienną środowiskową TEMP lub zmienna środowiskowa TEMP określa nieprawidłowy lub tylko do odczytu dysku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="96f45-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="96f45-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="96f45-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="96f45-105">Usuń pliki z dysku, jeśli jest to pełny.</span><span class="sxs-lookup"><span data-stu-id="96f45-105">Delete files from the drive, if full.</span></span>  
  
2.  <span data-ttu-id="96f45-106">Określ inny dysk zmienną środowiskową TEMP.</span><span class="sxs-lookup"><span data-stu-id="96f45-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3.  <span data-ttu-id="96f45-107">Określ prawidłowy dysk dla zmienną środowiskową TEMP.</span><span class="sxs-lookup"><span data-stu-id="96f45-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4.  <span data-ttu-id="96f45-108">Usuń ograniczenie tylko do odczytu z aktualnie określonego dysku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="96f45-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f45-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96f45-109">See Also</span></span>  
 [<span data-ttu-id="96f45-110">Error — typy</span><span class="sxs-lookup"><span data-stu-id="96f45-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
