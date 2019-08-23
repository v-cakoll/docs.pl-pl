---
title: Metoda ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f85dccd5b59610c52adcf685828984c9344fd49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911283"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="33480-102">Metoda ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="33480-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="33480-103">Pobiera wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="33480-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33480-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33480-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33480-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33480-105">Parameters</span></span>  
 <span data-ttu-id="33480-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="33480-106">ppThread</span></span>  
 <span data-ttu-id="33480-107">określoną Wskaźnik do adresu obiektu ICorDebugThread, który reprezentuje wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="33480-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33480-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33480-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33480-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="33480-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33480-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33480-110">Requirements</span></span>  
 <span data-ttu-id="33480-111">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33480-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33480-112">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33480-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33480-113">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33480-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33480-114">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33480-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33480-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33480-115">See also</span></span>

- [<span data-ttu-id="33480-116">ICorDebugDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="33480-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="33480-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="33480-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
