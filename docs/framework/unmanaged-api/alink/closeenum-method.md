---
title: CloseEnum — Metoda
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b6c839cc664105149f26b0d21d7ba7fb91b3e29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742200"
---
# <a name="closeenum-method"></a><span data-ttu-id="99aed-102">CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="99aed-102">CloseEnum Method</span></span>
<span data-ttu-id="99aed-103">Zamyka wskazany wyliczenie i zwalnia skojarzonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="99aed-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99aed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99aed-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="99aed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99aed-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="99aed-106">Dojście do wyliczenia zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="99aed-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99aed-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="99aed-107">Return Value</span></span>  
 <span data-ttu-id="99aed-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="99aed-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99aed-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99aed-109">Requirements</span></span>  
 <span data-ttu-id="99aed-110">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="99aed-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99aed-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99aed-111">See also</span></span>

- [<span data-ttu-id="99aed-112">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="99aed-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="99aed-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="99aed-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="99aed-114">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="99aed-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
