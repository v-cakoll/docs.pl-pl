---
title: Metoda ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 0900ac2ae5bcf2141e720dad6efdf68d4fafaccc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793532"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="a7b2d-102">Metoda ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="a7b2d-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="a7b2d-103">Pobiera wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b2d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7b2d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7b2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7b2d-105">Parameters</span></span>  
 <span data-ttu-id="a7b2d-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="a7b2d-106">ppThread</span></span>  
 <span data-ttu-id="a7b2d-107">określoną Wskaźnik do adresu obiektu ICorDebugThread, który reprezentuje wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7b2d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7b2d-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7b2d-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a7b2d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b2d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7b2d-110">Requirements</span></span>  
 <span data-ttu-id="a7b2d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7b2d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7b2d-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a7b2d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7b2d-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a7b2d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7b2d-114">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7b2d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b2d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7b2d-115">See also</span></span>

- [<span data-ttu-id="a7b2d-116">ICorDebugDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7b2d-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="a7b2d-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a7b2d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
