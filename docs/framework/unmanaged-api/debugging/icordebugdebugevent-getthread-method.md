---
title: Metoda ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: acce18517c105739417fc734b49ff004ca9546dc
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976385"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="090cb-102">Metoda ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="090cb-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="090cb-103">Pobiera wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="090cb-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="090cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="090cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="090cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="090cb-105">Parameters</span></span>  
 <span data-ttu-id="090cb-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="090cb-106">ppThread</span></span>  
 <span data-ttu-id="090cb-107">określoną Wskaźnik do adresu obiektu ICorDebugThread, który reprezentuje wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="090cb-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="090cb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="090cb-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="090cb-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="090cb-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="090cb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="090cb-110">Requirements</span></span>  
 <span data-ttu-id="090cb-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="090cb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="090cb-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="090cb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="090cb-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="090cb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="090cb-114">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="090cb-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="090cb-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="090cb-115">See also</span></span>

- [<span data-ttu-id="090cb-116">Interfejs ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="090cb-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="090cb-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="090cb-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
