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
ms.openlocfilehash: 0b238a953fa5cd57c8b7af9a0643bfc36ee1032e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088853"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="a4479-102">ICorDebugAppDomain3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a4479-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="a4479-103">Zapewnia metody do pobierania informacji o zarządzanych reprezentacjach typów środowisko wykonawcze systemu Windows aktualnie załadowanych w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4479-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="a4479-104">Ten interfejs jest rozszerzeniem interfejsów ICorDebugAppDomain i ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="a4479-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4479-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a4479-105">Methods</span></span>  
  
|<span data-ttu-id="a4479-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a4479-106">Method</span></span>|<span data-ttu-id="a4479-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a4479-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4479-108">ICorDebugAppDomain3:: GetCachedWinRTTypes —</span><span class="sxs-lookup"><span data-stu-id="a4479-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="a4479-109">Pobiera moduł wyliczający dla wszystkich typów środowisko wykonawcze systemu Windows w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a4479-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="a4479-110">ICorDebugAppDomain3:: GetCachedWinRTTypesForIIDs —</span><span class="sxs-lookup"><span data-stu-id="a4479-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="a4479-111">Pobiera moduł wyliczający dla buforowanych środowisko wykonawcze systemu Windows typów w domenie aplikacji w oparciu o ich identyfikatory interfejsów.</span><span class="sxs-lookup"><span data-stu-id="a4479-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4479-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4479-112">Remarks</span></span>  
 <span data-ttu-id="a4479-113">Ten interfejs jest przeznaczony do użycia przez debuger w połączeniu z wywołaniem oceny funkcji do `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="a4479-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="a4479-114">Gdy metoda pobiera identyfikatory interfejsów obsługiwane przez obiekt serwera środowisko wykonawcze systemu Windows, debuger może użyć metod zdefiniowanych w tym interfejsie do mapowania ich na typy zarządzane, które odpowiadają tym interfejsom.</span><span class="sxs-lookup"><span data-stu-id="a4479-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="a4479-115">Aby pobrać wystąpienie tego interfejsu, uruchom `QueryInterface` na wystąpieniu interfejsu ICorDebugAppDomain lub ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="a4479-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4479-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a4479-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4479-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4479-117">Requirements</span></span>  
 <span data-ttu-id="a4479-118">**Platformy:** środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a4479-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="a4479-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a4479-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4479-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a4479-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4479-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4479-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4479-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4479-122">See also</span></span>

- [<span data-ttu-id="a4479-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a4479-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
