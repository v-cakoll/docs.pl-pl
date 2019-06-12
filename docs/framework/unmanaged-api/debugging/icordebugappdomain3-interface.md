---
title: ICorDebugAppDomain3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256fd900fa73948b4ca42ac6b6f21f145effc461
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025895"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="9d609-102">ICorDebugAppDomain3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9d609-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="9d609-103">Dostarcza metody do pobierania informacji o zarządzanych reprezentacja typów środowiska wykonawczego Windows, które obecnie załadowane w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d609-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="9d609-104">Ten interfejs jest rozszerzeniem interfejsów ICorDebugAppDomain i ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="9d609-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d609-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9d609-105">Methods</span></span>  
  
|<span data-ttu-id="9d609-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9d609-106">Method</span></span>|<span data-ttu-id="9d609-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9d609-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d609-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="9d609-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="9d609-109">Pobiera moduł wyliczający dla wszystkich typów środowiska wykonawczego Windows pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9d609-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="9d609-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="9d609-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="9d609-111">Pobiera moduł wyliczający dla pamięci podręcznej typów środowiska wykonawczego Windows w domenie aplikacji, w oparciu o ich identyfikatory interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9d609-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d609-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d609-112">Remarks</span></span>  
 <span data-ttu-id="9d609-113">Ten interfejs jest przeznaczona do użycia przez debuger w połączeniu z wywołaniem oceny funkcji `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="9d609-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="9d609-114">Jeśli metoda pobiera identyfikatory interfejsu obsługiwane przez obiekt serwera Windows Runtime, debuger może używać metody zdefiniowane w tym interfejsie mapować je na zarządzane typy, które odnoszą się do tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="9d609-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="9d609-115">Uruchom, aby pobrać wystąpienie tego interfejsu `QueryInterface` w wystąpieniu ICorDebugAppDomain lub icordebugappdomain2 — interfejs.</span><span class="sxs-lookup"><span data-stu-id="9d609-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d609-116">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="9d609-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d609-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d609-117">Requirements</span></span>  
 <span data-ttu-id="9d609-118">**Platformy:** Środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9d609-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="9d609-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d609-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d609-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d609-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d609-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d609-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d609-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d609-122">See also</span></span>

- [<span data-ttu-id="9d609-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9d609-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
