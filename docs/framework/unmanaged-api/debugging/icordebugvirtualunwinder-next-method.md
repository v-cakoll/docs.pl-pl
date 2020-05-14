---
title: 'ICorDebugVirtualUnwinder:: Next — Metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 55f10a6148f0b11cf74492afe947d5921a1d1458
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396426"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="ffb22-102">ICorDebugVirtualUnwinder:: Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="ffb22-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="ffb22-103">Przechodzi do kontekstu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ffb22-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffb22-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffb22-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffb22-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffb22-105">Parameters</span></span>  
 <span data-ttu-id="ffb22-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="ffb22-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffb22-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ffb22-107">Return Value</span></span>  
 <span data-ttu-id="ffb22-108">`S_OK`Jeśli operacja unwind zakończyła się pomyślnie lub `CORDBG_S_AT_END_OF_STACK` nie można ukończyć operacji unwindy, ponieważ nie ma więcej ramek.</span><span class="sxs-lookup"><span data-stu-id="ffb22-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="ffb22-109">Jeśli zwracana jest niepowodzenie HRESULT, ICorDebug interfejsy API zostaną zwrócone `CORDBG_E_DATA_TARGET_ERROR` .</span><span class="sxs-lookup"><span data-stu-id="ffb22-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffb22-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffb22-110">Remarks</span></span>  
 <span data-ttu-id="ffb22-111">Analizator stosu powinien zapewnić, że postępuje postęp, tak że ostatecznie wywołanie `Next` zwróci błąd HRESULT lub `CORDBG_S_AT_END_OF_STACK` .</span><span class="sxs-lookup"><span data-stu-id="ffb22-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="ffb22-112">Zwracanie `S_OK` nieokreślonych wartości może spowodować nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="ffb22-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffb22-113">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ffb22-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffb22-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffb22-114">Requirements</span></span>  
 <span data-ttu-id="ffb22-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffb22-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffb22-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ffb22-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffb22-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ffb22-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffb22-118">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffb22-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffb22-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffb22-119">See also</span></span>

- [<span data-ttu-id="ffb22-120">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="ffb22-120">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="ffb22-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ffb22-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
