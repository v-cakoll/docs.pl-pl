---
title: "ICorDebugValue3::GetSize64 — Metoda"
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
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4eb0c4691b82bdfaecb97c5969a942c113987c04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="c7c1d-102">ICorDebugValue3::GetSize64 — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7c1d-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="c7c1d-103">Pobiera rozmiar w bajtach to [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="c7c1d-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7c1d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7c1d-104">Syntax</span></span>  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7c1d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7c1d-105">Parameters</span></span>  
 <span data-ttu-id="c7c1d-106">pSize</span><span class="sxs-lookup"><span data-stu-id="c7c1d-106">pSize</span></span>  
 <span data-ttu-id="c7c1d-107">[out] Wskaźnik do rozmiar w bajtach tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c7c1d-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7c1d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7c1d-108">Remarks</span></span>  
 <span data-ttu-id="c7c1d-109">Jeśli ta wartość typ jest typem referencyjnym, ta metoda zwraca rozmiar wskaźnika niż rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="c7c1d-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="c7c1d-110">`ICorDebugValue3::GetSize` Metoda różni się od [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) metody w typie jej parametr wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="c7c1d-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="c7c1d-111">W [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), parametr wyjściowy jest `ULONG32`; na liście `ICorDebugValue3::GetSize`, jest `ULONG64`.</span><span class="sxs-lookup"><span data-stu-id="c7c1d-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="c7c1d-112">Dzięki temu [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interfejs do zgłaszania rozmiar tablic, które przekraczają 2 GB.</span><span class="sxs-lookup"><span data-stu-id="c7c1d-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7c1d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7c1d-113">Requirements</span></span>  
 <span data-ttu-id="c7c1d-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7c1d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7c1d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7c1d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7c1d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7c1d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7c1d-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7c1d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c1d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7c1d-118">See Also</span></span>  
 [<span data-ttu-id="c7c1d-119">ICorDebugValue3, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7c1d-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="c7c1d-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c7c1d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
