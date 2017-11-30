---
title: "CloseEnum — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CloseEnum
- IALink.CloseEnum
api_location: alink.dll
api_type: COM
f1_keywords: CloseEnum
helpviewer_keywords: CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6ade939969069fb35221d83f8c7e4e380e903a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="closeenum-method"></a><span data-ttu-id="796d4-102">CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="796d4-102">CloseEnum Method</span></span>
<span data-ttu-id="796d4-103">Zamyka wskazanych wyliczenie i zwalnia skojarzonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="796d4-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="796d4-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="796d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="796d4-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="796d4-106">Dojście do wyliczenia zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="796d4-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="796d4-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="796d4-107">Return Value</span></span>  
 <span data-ttu-id="796d4-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="796d4-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="796d4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="796d4-109">Requirements</span></span>  
 <span data-ttu-id="796d4-110">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="796d4-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796d4-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="796d4-111">See Also</span></span>  
 [<span data-ttu-id="796d4-112">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="796d4-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="796d4-113">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="796d4-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="796d4-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="796d4-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
