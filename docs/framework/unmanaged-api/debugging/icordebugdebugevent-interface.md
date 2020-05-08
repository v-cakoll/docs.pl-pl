---
title: Interfejs ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: a66012651d4b307d06a5a3bff675a248cc0ee376
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976359"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="85f0b-102">Interfejs ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="85f0b-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="85f0b-103">Definiuje interfejs podstawowy, z którego pochodzą `ICorDebug` wszystkie zdarzenia debugowania.</span><span class="sxs-lookup"><span data-stu-id="85f0b-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85f0b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="85f0b-104">Methods</span></span>  
  
|<span data-ttu-id="85f0b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="85f0b-105">Method</span></span>|<span data-ttu-id="85f0b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="85f0b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85f0b-107">GetEventKind, metoda</span><span class="sxs-lookup"><span data-stu-id="85f0b-107">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="85f0b-108">Wskazuje, jaki rodzaj zdarzenia reprezentuje `ICorDebugDebugEvent` ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="85f0b-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="85f0b-109">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="85f0b-109">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="85f0b-110">Pobiera wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="85f0b-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85f0b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85f0b-111">Remarks</span></span>  
 <span data-ttu-id="85f0b-112">Następujące interfejsy pochodzą od `ICorDebugDebugEvent` interfejsu:</span><span class="sxs-lookup"><span data-stu-id="85f0b-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="85f0b-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="85f0b-113">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="85f0b-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="85f0b-114">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="85f0b-115">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="85f0b-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="85f0b-116">Próba wywołania metody `QueryInterface` pobierającej wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="85f0b-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f0b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85f0b-117">Requirements</span></span>  
 <span data-ttu-id="85f0b-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85f0b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85f0b-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85f0b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85f0b-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85f0b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85f0b-121">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85f0b-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f0b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85f0b-122">See also</span></span>

- [<span data-ttu-id="85f0b-123">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="85f0b-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="85f0b-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="85f0b-124">Debugging</span></span>](index.md)
