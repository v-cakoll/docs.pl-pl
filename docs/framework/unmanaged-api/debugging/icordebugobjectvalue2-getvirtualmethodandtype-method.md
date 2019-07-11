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
ms.openlocfilehash: bcbe9a701b91a063e19fec5aae9cc2687b1f279f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766134"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="01e99-102">ICorDebugObjectValue2::GetVirtualMethodAndType — Metoda</span><span class="sxs-lookup"><span data-stu-id="01e99-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>
<span data-ttu-id="01e99-103">Ta metoda nie została jeszcze zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="01e99-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e99-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01e99-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="01e99-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01e99-105">Remarks</span></span>  
 <span data-ttu-id="01e99-106">Pobiera interfejs wskaźniki do wystąpienia "ICorDebugFunction" i "ICorDebugType", które reprezentują najbardziej pochodnej metoda i typ dla odwołania do określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="01e99-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e99-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01e99-107">See also</span></span>
