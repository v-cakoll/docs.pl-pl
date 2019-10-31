---
title: Metoda ICorDebugDataTarget2::EnumerateThreadIDs
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: b4510e6858045281a2a663095972b84c40df3a22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122162"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="1319d-102">Metoda ICorDebugDataTarget2::EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="1319d-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="1319d-103">Zwraca listę aktywnych identyfikatorów wątków.</span><span class="sxs-lookup"><span data-stu-id="1319d-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1319d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1319d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1319d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1319d-105">Parameters</span></span>  
 <span data-ttu-id="1319d-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="1319d-106">cThreadIDs</span></span>  
 <span data-ttu-id="1319d-107">podczas Maksymalna liczba wątków, których identyfikatory można zwrócić.</span><span class="sxs-lookup"><span data-stu-id="1319d-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="1319d-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="1319d-108">pcThreadIds</span></span>  
 <span data-ttu-id="1319d-109">określoną Wskaźnik do `ULONG32`, który wskazuje rzeczywistą liczbę identyfikatorów wątków zapisaną w tablicy `pThreadIds`.</span><span class="sxs-lookup"><span data-stu-id="1319d-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="1319d-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="1319d-110">pThreadIDs</span></span>  
 <span data-ttu-id="1319d-111">Tablica identyfikatorów wątków.</span><span class="sxs-lookup"><span data-stu-id="1319d-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1319d-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1319d-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1319d-113">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1319d-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1319d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1319d-114">Requirements</span></span>  
 <span data-ttu-id="1319d-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md). **Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1319d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1319d-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1319d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1319d-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1319d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1319d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1319d-118">See also</span></span>

- [<span data-ttu-id="1319d-119">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1319d-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="1319d-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1319d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
