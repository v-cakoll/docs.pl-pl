---
title: ICorDebugObjectValue2::GetVirtualMethodAndType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue2.GetVirtualMethodAndType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9a6978f35b5ea9fb71f8e933dbc7a08b1c390ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="79fa3-102">ICorDebugObjectValue2::GetVirtualMethodAndType — Metoda</span><span class="sxs-lookup"><span data-stu-id="79fa3-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>
<span data-ttu-id="79fa3-103">Ta metoda nie została jeszcze zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="79fa3-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79fa3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="79fa3-104">Syntax</span></span>  
  
```  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="79fa3-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79fa3-105">Remarks</span></span>  
 <span data-ttu-id="79fa3-106">Pobiera interfejs wskaźników do wystąpień "ICorDebugFunction" i "ICorDebugType", które reprezentują najbardziej pochodnej metody i typu dla odwołania do określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="79fa3-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79fa3-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79fa3-107">See Also</span></span>  
    
 
