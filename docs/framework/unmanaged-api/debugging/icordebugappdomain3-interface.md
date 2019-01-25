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
ms.openlocfilehash: ade4c88f4431dd6db636ea2581bdb936ac8d8e5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538014"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="eeac6-102">ICorDebugAppDomain3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="eeac6-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="eeac6-103">Dostarcza metody do pobierania informacji o zarządzanych reprezentacje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy załadowanych obecnie do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eeac6-103">Provides methods to retrieve information about the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in an application domain.</span></span> <span data-ttu-id="eeac6-104">Ten interfejs jest rozszerzeniem interfejsów ICorDebugAppDomain i ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="eeac6-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eeac6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="eeac6-105">Methods</span></span>  
  
|<span data-ttu-id="eeac6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="eeac6-106">Method</span></span>|<span data-ttu-id="eeac6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="eeac6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eeac6-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="eeac6-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="eeac6-109">Pobiera moduł wyliczający dla wszystkich buforowanych [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów.</span><span class="sxs-lookup"><span data-stu-id="eeac6-109">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>|  
|[<span data-ttu-id="eeac6-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="eeac6-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="eeac6-111">Pobiera moduł wyliczający dla pamięci podręcznej [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów w domenie aplikacji w oparciu o ich identyfikatory interfejsu.</span><span class="sxs-lookup"><span data-stu-id="eeac6-111">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eeac6-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eeac6-112">Remarks</span></span>  
 <span data-ttu-id="eeac6-113">Ten interfejs jest przeznaczona do użycia przez debuger w połączeniu z wywołaniem oceny funkcji `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="eeac6-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="eeac6-114">Gdy metoda pobiera identyfikatory interfejsu obsługiwane przez [!INCLUDE[wrt](../../../../includes/wrt-md.md)] obiektu serwera, debuger może używać metody zdefiniowane w tym interfejsie w celu zamapowania ich na zarządzane typy, które odnoszą się do tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="eeac6-114">When the method retrieves the interface identifiers supported by a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="eeac6-115">Uruchom, aby pobrać wystąpienie tego interfejsu `QueryInterface` w wystąpieniu ICorDebugAppDomain lub icordebugappdomain2 — interfejs.</span><span class="sxs-lookup"><span data-stu-id="eeac6-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eeac6-116">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="eeac6-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eeac6-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eeac6-117">Requirements</span></span>  
 <span data-ttu-id="eeac6-118">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeac6-118">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="eeac6-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eeac6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eeac6-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eeac6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eeac6-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeac6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeac6-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eeac6-122">See also</span></span>
- [<span data-ttu-id="eeac6-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="eeac6-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
