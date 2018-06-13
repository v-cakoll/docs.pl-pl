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
ms.openlocfilehash: e5c3185dc6d488223d5882f543f0c690d82261b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402447"
---
# <a name="closeenum-method"></a><span data-ttu-id="5458e-102">CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="5458e-102">CloseEnum Method</span></span>
<span data-ttu-id="5458e-103">Zamyka wskazanych wyliczenie i zwalnia skojarzonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="5458e-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5458e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5458e-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5458e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5458e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="5458e-106">Dojście do wyliczenia zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="5458e-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5458e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5458e-107">Return Value</span></span>  
 <span data-ttu-id="5458e-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5458e-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5458e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5458e-109">Requirements</span></span>  
 <span data-ttu-id="5458e-110">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="5458e-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5458e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5458e-111">See Also</span></span>  
 [<span data-ttu-id="5458e-112">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="5458e-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="5458e-113">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5458e-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="5458e-114">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="5458e-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
