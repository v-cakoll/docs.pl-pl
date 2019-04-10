---
title: Metoda ICorDebugDataTarget2::EnumerateThreadIDs
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70b3b57b51faed51aa7d5a70a3b785e0f719321b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215849"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="f6c53-102">Metoda ICorDebugDataTarget2::EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="f6c53-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="f6c53-103">Zwraca listę aktywnych wątków identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="f6c53-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c53-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6c53-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6c53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6c53-105">Parameters</span></span>  
 <span data-ttu-id="f6c53-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="f6c53-106">cThreadIDs</span></span>  
 <span data-ttu-id="f6c53-107">[in] Maksymalna liczba wątków, których identyfikatory, które mogą być zwrócone.</span><span class="sxs-lookup"><span data-stu-id="f6c53-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="f6c53-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="f6c53-108">pcThreadIds</span></span>  
 <span data-ttu-id="f6c53-109">[out] Wskaźnik do `ULONG32` oznacza to, rzeczywista liczba wątków identyfikatory zapisywane do `pThreadIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f6c53-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="f6c53-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="f6c53-110">pThreadIDs</span></span>  
 <span data-ttu-id="f6c53-111">Tablica identyfikatorów wątku.</span><span class="sxs-lookup"><span data-stu-id="f6c53-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6c53-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6c53-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6c53-113">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f6c53-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6c53-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6c53-114">Requirements</span></span>  
 <span data-ttu-id="f6c53-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md). **Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6c53-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6c53-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6c53-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f6c53-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f6c53-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6c53-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6c53-118">See also</span></span>

- [<span data-ttu-id="f6c53-119">Interfejs ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="f6c53-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="f6c53-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f6c53-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
