---
title: Metoda ICorDebugDataTarget2::EnumerateThreadIDs
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 848929901e91164bdccda5c1e77069364452a782
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750251"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="e3bd9-102">Metoda ICorDebugDataTarget2::EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="e3bd9-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="e3bd9-103">Zwraca listę aktywnych wątków identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="e3bd9-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3bd9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3bd9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3bd9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3bd9-105">Parameters</span></span>  
 <span data-ttu-id="e3bd9-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="e3bd9-106">cThreadIDs</span></span>  
 <span data-ttu-id="e3bd9-107">[in] Maksymalna liczba wątków, których identyfikatory, które mogą być zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e3bd9-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="e3bd9-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="e3bd9-108">pcThreadIds</span></span>  
 <span data-ttu-id="e3bd9-109">[out] Wskaźnik do `ULONG32` oznacza to, rzeczywista liczba wątków identyfikatory zapisywane do `pThreadIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e3bd9-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="e3bd9-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="e3bd9-110">pThreadIDs</span></span>  
 <span data-ttu-id="e3bd9-111">Tablica identyfikatorów wątku.</span><span class="sxs-lookup"><span data-stu-id="e3bd9-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3bd9-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3bd9-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3bd9-113">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e3bd9-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3bd9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3bd9-114">Requirements</span></span>  
 <span data-ttu-id="e3bd9-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md). **Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3bd9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3bd9-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3bd9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3bd9-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3bd9-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3bd9-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3bd9-118">See also</span></span>

- [<span data-ttu-id="e3bd9-119">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3bd9-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="e3bd9-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e3bd9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
