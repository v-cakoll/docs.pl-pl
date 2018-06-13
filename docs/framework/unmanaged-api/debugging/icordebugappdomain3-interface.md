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
ms.openlocfilehash: 7c130b92fd5114d067730da3b7cd138d98cf0577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407408"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="91eb9-102">ICorDebugAppDomain3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="91eb9-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="91eb9-103">Udostępnia metody do pobierania informacji o zarządzanych reprezentacje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy załadowanych obecnie do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91eb9-103">Provides methods to retrieve information about the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in an application domain.</span></span> <span data-ttu-id="91eb9-104">Ten interfejs jest rozszerzeniem ICorDebugAppDomain i ICorDebugAppDomain2 interfejsów.</span><span class="sxs-lookup"><span data-stu-id="91eb9-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91eb9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="91eb9-105">Methods</span></span>  
  
|<span data-ttu-id="91eb9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="91eb9-106">Method</span></span>|<span data-ttu-id="91eb9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="91eb9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91eb9-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="91eb9-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="91eb9-109">Pobiera moduł wyliczający wszystkie buforowane [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów.</span><span class="sxs-lookup"><span data-stu-id="91eb9-109">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>|  
|[<span data-ttu-id="91eb9-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="91eb9-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="91eb9-111">Pobiera moduł wyliczający dla pamięci podręcznej [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów w domenie aplikacji w oparciu o ich identyfikatorów interfejsu.</span><span class="sxs-lookup"><span data-stu-id="91eb9-111">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91eb9-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91eb9-112">Remarks</span></span>  
 <span data-ttu-id="91eb9-113">Ten interfejs jest przeznaczona do użycia przez debuger w połączeniu z wywołanie oceny funkcji `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="91eb9-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="91eb9-114">Gdy metoda pobiera identyfikatory interfejsów obsługiwane przez [!INCLUDE[wrt](../../../../includes/wrt-md.md)] obiektu serwera, debuger może używać metody zdefiniowane w tym interfejsie w celu zamapowania ich typy zarządzane, które odpowiadają te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="91eb9-114">When the method retrieves the interface identifiers supported by a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="91eb9-115">Aby pobrać wystąpienia tego interfejsu, uruchom `QueryInterface` w wystąpieniu interfejsu ICorDebugAppDomain lub ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="91eb9-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91eb9-116">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="91eb9-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91eb9-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91eb9-117">Requirements</span></span>  
 <span data-ttu-id="91eb9-118">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91eb9-118">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="91eb9-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91eb9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91eb9-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91eb9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91eb9-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91eb9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91eb9-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91eb9-122">See Also</span></span>  
 [<span data-ttu-id="91eb9-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="91eb9-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
