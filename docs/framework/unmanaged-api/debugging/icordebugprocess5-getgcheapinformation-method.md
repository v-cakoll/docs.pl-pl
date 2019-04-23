---
title: ICorDebugProcess5::GetGCHeapInformation — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50b682a7b3a4aadf7559120745265ef266cf2870
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140546"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="e2cbe-102">ICorDebugProcess5::GetGCHeapInformation — Metoda</span><span class="sxs-lookup"><span data-stu-id="e2cbe-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="e2cbe-103">Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym, czy jest ono aktualnie wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="e2cbe-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2cbe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2cbe-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2cbe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2cbe-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="e2cbe-106">[out] Wskaźnik do [cor_heapinfo —](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) wartość, która zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e2cbe-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2cbe-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2cbe-107">Remarks</span></span>  
 <span data-ttu-id="e2cbe-108">`ICorDebugProcess5::GetGCHeapInformation` Metoda musi zostać wywołana przed wyliczanie stosu lub sterty poszczególnych regionów, aby upewnić się, że wyrzucanie elementów bezużytecznych struktury w procesie jest ważny w chwili obecnej.</span><span class="sxs-lookup"><span data-stu-id="e2cbe-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="e2cbe-109">Nie może być dodawanym stercie wyrzucania elementów bezużytecznych, gdy kolekcja jest w toku.</span><span class="sxs-lookup"><span data-stu-id="e2cbe-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="e2cbe-110">W przeciwnym razie wyliczenia mogą przechwytywać struktury kolekcji wyrzucania elementów, które są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e2cbe-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2cbe-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2cbe-111">Requirements</span></span>  
 <span data-ttu-id="e2cbe-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2cbe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2cbe-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2cbe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2cbe-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2cbe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2cbe-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2cbe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2cbe-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2cbe-116">See also</span></span>

- [<span data-ttu-id="e2cbe-117">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2cbe-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="e2cbe-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e2cbe-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
