---
title: 'ICorDebugVirtualUnwinder:: Next — Metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 06d5377ef123cc3f9c91fbfbcf0b0f17a14eb629
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790819"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="96c82-102">ICorDebugVirtualUnwinder:: Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="96c82-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="96c82-103">Przechodzi do kontekstu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="96c82-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c82-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="96c82-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="96c82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96c82-105">Parameters</span></span>  
 <span data-ttu-id="96c82-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="96c82-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96c82-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="96c82-107">Return Value</span></span>  
 <span data-ttu-id="96c82-108">`S_OK`, jeśli wystąpiło pomyślne przewinięcie lub `CORDBG_S_AT_END_OF_STACK`, jeśli nie można ukończyć operacji unwindy, ponieważ nie ma więcej ramek.</span><span class="sxs-lookup"><span data-stu-id="96c82-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="96c82-109">Jeśli zwracana jest niepowodzenie HRESULT, interfejsy API ICorDebug będą zwracać `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="96c82-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96c82-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96c82-110">Remarks</span></span>  
 <span data-ttu-id="96c82-111">Analizator stosu powinien zapewnić, że postępuje postęp, aby ostatecznie wywołanie `Next` zwróci błąd HRESULT lub `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="96c82-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="96c82-112">Zwracanie `S_OK` nieskończoność może spowodować nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="96c82-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96c82-113">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="96c82-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96c82-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96c82-114">Requirements</span></span>  
 <span data-ttu-id="96c82-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96c82-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96c82-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96c82-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96c82-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="96c82-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96c82-118">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96c82-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c82-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96c82-119">See also</span></span>

- [<span data-ttu-id="96c82-120">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="96c82-120">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="96c82-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="96c82-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
