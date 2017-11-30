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
ms.openlocfilehash: c20b7dd1bcbc27edb9be11419b7919250301d488
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="2f505-102">Metoda ICorDebugDataTarget2::EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="2f505-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="2f505-103">Zwraca listę aktywnych wątku identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="2f505-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f505-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f505-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f505-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f505-105">Parameters</span></span>  
 <span data-ttu-id="2f505-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="2f505-106">cThreadIDs</span></span>  
 <span data-ttu-id="2f505-107">[in] Maksymalna liczba wątków, których identyfikatory może być zwracany.</span><span class="sxs-lookup"><span data-stu-id="2f505-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="2f505-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="2f505-108">pcThreadIds</span></span>  
 <span data-ttu-id="2f505-109">[out] Wskaźnik do `ULONG32` który wskazuje rzeczywistą liczbę wątków zapisane identyfikatory `pThreadIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="2f505-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="2f505-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="2f505-110">pThreadIDs</span></span>  
 <span data-ttu-id="2f505-111">Tablica identyfikatorów wątku.</span><span class="sxs-lookup"><span data-stu-id="2f505-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f505-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f505-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f505-113">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2f505-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f505-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f505-114">Requirements</span></span>  
 <span data-ttu-id="2f505-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md). **Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f505-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f505-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f505-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f505-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f505-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f505-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f505-118">See Also</span></span>  
 [<span data-ttu-id="2f505-119">Interfejs ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="2f505-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="2f505-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="2f505-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
