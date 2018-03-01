---
title: "ICorDebugThreadEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ac9ff468f85248631ffd7f3a39a8827b1aef45b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="dfca4-102">ICorDebugThreadEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="dfca4-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="dfca4-103">Pobiera liczbę wystąpień określonego ICorDebugThread z wyliczenia, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="dfca4-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfca4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfca4-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfca4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfca4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="dfca4-106">[in] Liczba `ICorDebugThread` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="dfca4-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="dfca4-107">[out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugThread` obiekt, który reprezentuje wątku.</span><span class="sxs-lookup"><span data-stu-id="dfca4-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="dfca4-108">[out] Wskaźnik do liczby `ICorDebugThread` wystąpienia faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="dfca4-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="dfca4-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="dfca4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfca4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfca4-110">Requirements</span></span>  
 <span data-ttu-id="dfca4-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfca4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfca4-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfca4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfca4-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfca4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfca4-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfca4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
