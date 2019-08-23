---
title: Metoda ICorDebugDataTarget2::EnumerateThreadIDs
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1dc5f8b7fa308bdb0fb270c11e044244839a7b47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910289"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="0102e-102">Metoda ICorDebugDataTarget2::EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="0102e-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="0102e-103">Zwraca listę aktywnych identyfikatorów wątków.</span><span class="sxs-lookup"><span data-stu-id="0102e-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0102e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0102e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0102e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0102e-105">Parameters</span></span>  
 <span data-ttu-id="0102e-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="0102e-106">cThreadIDs</span></span>  
 <span data-ttu-id="0102e-107">podczas Maksymalna liczba wątków, których identyfikatory można zwrócić.</span><span class="sxs-lookup"><span data-stu-id="0102e-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="0102e-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="0102e-108">pcThreadIds</span></span>  
 <span data-ttu-id="0102e-109">określoną Wskaźnik `ULONG32` wskazujący rzeczywistą liczbę identyfikatorów wątków zapisaną `pThreadIds` w tablicy.</span><span class="sxs-lookup"><span data-stu-id="0102e-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="0102e-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="0102e-110">pThreadIDs</span></span>  
 <span data-ttu-id="0102e-111">Tablica identyfikatorów wątków.</span><span class="sxs-lookup"><span data-stu-id="0102e-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0102e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0102e-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0102e-113">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0102e-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0102e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0102e-114">Requirements</span></span>  
 <span data-ttu-id="0102e-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md). **Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0102e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0102e-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0102e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0102e-117">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0102e-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0102e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0102e-118">See also</span></span>

- [<span data-ttu-id="0102e-119">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0102e-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="0102e-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0102e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
