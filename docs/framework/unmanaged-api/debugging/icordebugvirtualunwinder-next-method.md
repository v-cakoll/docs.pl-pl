---
title: 'ICorDebugVirtualUnwinder:: Next — Metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a3d4bac42731bc94ecef7a0756392c8c0882fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967920"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="eb112-102">ICorDebugVirtualUnwinder:: Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb112-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="eb112-103">Przechodzi do kontekstu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="eb112-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb112-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb112-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb112-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb112-105">Parameters</span></span>  
 <span data-ttu-id="eb112-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="eb112-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb112-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eb112-107">Return Value</span></span>  
 <span data-ttu-id="eb112-108">`S_OK`Jeśli operacja unwind zakończyła `CORDBG_S_AT_END_OF_STACK` się pomyślnie lub nie można ukończyć operacji unwindy, ponieważ nie ma więcej ramek.</span><span class="sxs-lookup"><span data-stu-id="eb112-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="eb112-109">Jeśli zwracana jest niepowodzenie HRESULT, ICorDebug interfejsy API zostaną zwrócone `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="eb112-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb112-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb112-110">Remarks</span></span>  
 <span data-ttu-id="eb112-111">Analizator stosu powinien zapewnić, że postępuje postęp, tak że ostatecznie wywołanie `Next` zwróci błąd HRESULT lub. `CORDBG_S_AT_END_OF_STACK`</span><span class="sxs-lookup"><span data-stu-id="eb112-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="eb112-112">Zwracanie `S_OK` nieokreślonych wartości może spowodować nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="eb112-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb112-113">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="eb112-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb112-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb112-114">Requirements</span></span>  
 <span data-ttu-id="eb112-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb112-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb112-116">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb112-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb112-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb112-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb112-118">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb112-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb112-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb112-119">See also</span></span>

- [<span data-ttu-id="eb112-120">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb112-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="eb112-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="eb112-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
