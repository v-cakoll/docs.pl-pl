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
ms.openlocfilehash: 17cb3440c5b33d461b1624608ce115e1942d6beb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129719"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="1b2eb-102">ICorDebugObjectValue2::GetVirtualMethodAndType — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b2eb-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>
<span data-ttu-id="1b2eb-103">Ta metoda nie została jeszcze zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="1b2eb-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b2eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b2eb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="1b2eb-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b2eb-105">Remarks</span></span>  
 <span data-ttu-id="1b2eb-106">Pobiera wskaźniki interfejsu do wystąpień "ICorDebugFunction" i "ICorDebugType", które reprezentują najbardziej pochodną metodę i typ dla określonego odwołania do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1b2eb-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b2eb-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b2eb-107">See also</span></span>
