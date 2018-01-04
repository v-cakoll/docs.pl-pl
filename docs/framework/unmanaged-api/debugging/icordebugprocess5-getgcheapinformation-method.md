---
title: "ICorDebugProcess5::GetGCHeapInformation — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetGCHeapInformation
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70e9e3ab6c7332e492b7146e52e0265653803bf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="d9a0f-102">ICorDebugProcess5::GetGCHeapInformation — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9a0f-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="d9a0f-103">Ogólne informacje dotyczące pamięci sterty kolekcji, w tym, czy jest ono aktualnie wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="d9a0f-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9a0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9a0f-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9a0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9a0f-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="d9a0f-106">[out] Wskaźnik do [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) wartość, która zawiera ogólne informacje dotyczące odzyskiwania pamięci sterty kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d9a0f-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9a0f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9a0f-107">Remarks</span></span>  
 <span data-ttu-id="d9a0f-108">`ICorDebugProcess5::GetGCHeapInformation` Metoda musi zostać wywołana przed wyliczania sterty lub sterty poszczególnych regionów, aby upewnić się, że wyrzucanie elementów bezużytecznych struktury w procesie nie jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d9a0f-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="d9a0f-109">Nie może być udał pamięci sterty kolekcji, gdy kolekcja jest w toku.</span><span class="sxs-lookup"><span data-stu-id="d9a0f-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="d9a0f-110">W przeciwnym razie wartość wyliczenia może przechwycić struktury kolekcji pamięci, które nie są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="d9a0f-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9a0f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9a0f-111">Requirements</span></span>  
 <span data-ttu-id="d9a0f-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9a0f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9a0f-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9a0f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9a0f-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9a0f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9a0f-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9a0f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9a0f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9a0f-116">See Also</span></span>  
 [<span data-ttu-id="d9a0f-117">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9a0f-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="d9a0f-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d9a0f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
