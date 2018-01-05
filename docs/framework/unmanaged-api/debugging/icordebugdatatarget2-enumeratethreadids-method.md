---
title: Metoda ICorDebugDataTarget2::EnumerateThreadIDs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9030f7f8453de98f535cf8212e55c7daee94e8e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="cc710-102">Metoda ICorDebugDataTarget2::EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="cc710-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="cc710-103">Zwraca listę aktywnych wątku identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="cc710-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc710-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc710-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc710-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc710-105">Parameters</span></span>  
 <span data-ttu-id="cc710-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="cc710-106">cThreadIDs</span></span>  
 <span data-ttu-id="cc710-107">[in] Maksymalna liczba wątków, których identyfikatory może być zwracany.</span><span class="sxs-lookup"><span data-stu-id="cc710-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="cc710-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="cc710-108">pcThreadIds</span></span>  
 <span data-ttu-id="cc710-109">[out] Wskaźnik do `ULONG32` który wskazuje rzeczywistą liczbę wątków zapisane identyfikatory `pThreadIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="cc710-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="cc710-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="cc710-110">pThreadIDs</span></span>  
 <span data-ttu-id="cc710-111">Tablica identyfikatorów wątku.</span><span class="sxs-lookup"><span data-stu-id="cc710-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc710-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc710-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc710-113">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cc710-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc710-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc710-114">Requirements</span></span>  
 <span data-ttu-id="cc710-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md). **Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc710-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc710-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc710-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc710-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc710-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc710-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc710-118">See Also</span></span>  
 [<span data-ttu-id="cc710-119">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc710-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="cc710-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cc710-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
