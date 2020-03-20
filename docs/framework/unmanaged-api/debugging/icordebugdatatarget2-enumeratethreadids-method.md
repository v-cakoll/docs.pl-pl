---
title: Metoda ICorDebugDataTarget2::EnumerateThreadIDs
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 120a970aac33b1ab06ae47335a959d2791f893ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178979"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="deba2-102">Metoda ICorDebugDataTarget2::EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="deba2-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="deba2-103">Zwraca listę aktywnych identyfikatorów wątków.</span><span class="sxs-lookup"><span data-stu-id="deba2-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deba2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="deba2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="deba2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="deba2-105">Parameters</span></span>  
 <span data-ttu-id="deba2-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="deba2-106">cThreadIDs</span></span>  
 <span data-ttu-id="deba2-107">[w] Maksymalna liczba wątków, których identyfikatory mogą być zwracane.</span><span class="sxs-lookup"><span data-stu-id="deba2-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="deba2-108">pcThreadIds (Nieujmi.</span><span class="sxs-lookup"><span data-stu-id="deba2-108">pcThreadIds</span></span>  
 <span data-ttu-id="deba2-109">[na zewnątrz] Wskaźnik `ULONG32` do, który wskazuje rzeczywistą liczbę identyfikatorów wątku `pThreadIds` zapisane w tablicy.</span><span class="sxs-lookup"><span data-stu-id="deba2-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="deba2-110">pThreadIDs (Psż.</span><span class="sxs-lookup"><span data-stu-id="deba2-110">pThreadIDs</span></span>  
 <span data-ttu-id="deba2-111">Tablica identyfikatorów wątków.</span><span class="sxs-lookup"><span data-stu-id="deba2-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="deba2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="deba2-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="deba2-113">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="deba2-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deba2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="deba2-114">Requirements</span></span>  
 <span data-ttu-id="deba2-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md). **Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="deba2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="deba2-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="deba2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deba2-117">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deba2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deba2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="deba2-118">See also</span></span>

- [<span data-ttu-id="deba2-119">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="deba2-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="deba2-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="deba2-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
