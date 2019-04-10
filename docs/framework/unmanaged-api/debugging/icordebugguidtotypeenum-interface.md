---
title: ICorDebugGuidToTypeEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2ea67c6e4d860d41cfe67aaab73babb51f3ce45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210662"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="68dba-102">ICorDebugGuidToTypeEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="68dba-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="68dba-103">Dostarcza moduł wyliczający, który definiuje mapowanie między zbiór identyfikatorów GUID i odpowiednie typy, które są reprezentowane przez ICorDebugType wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="68dba-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="68dba-104">Ten interfejs dziedziczy metody icordebugenum — interfejs.</span><span class="sxs-lookup"><span data-stu-id="68dba-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68dba-105">Metody</span><span class="sxs-lookup"><span data-stu-id="68dba-105">Methods</span></span>  
  
|<span data-ttu-id="68dba-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="68dba-106">Method</span></span>|<span data-ttu-id="68dba-107">Opis</span><span class="sxs-lookup"><span data-stu-id="68dba-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68dba-108">ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="68dba-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="68dba-109">Pobiera określoną liczbę [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) wystąpień, które mapują identyfikatory GUID do informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="68dba-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68dba-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68dba-110">Remarks</span></span>  
 <span data-ttu-id="68dba-111">`ICorDebugGuidToTypeEnum` Obiektu interfejsu może być pobierany przez wywołanie [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="68dba-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="68dba-112">Debuger może wywołać ten interfejs [dalej](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metodę, która pobierze [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) obiekty reprezentujące mapowania zarządzane reprezentacje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów są ładowane w Domena aplikacji używana do wywołań [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="68dba-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68dba-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68dba-113">Requirements</span></span>  
 **<span data-ttu-id="68dba-114">Platformy:</span><span class="sxs-lookup"><span data-stu-id="68dba-114">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="68dba-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68dba-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68dba-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68dba-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="68dba-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="68dba-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68dba-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68dba-118">See also</span></span>

- [<span data-ttu-id="68dba-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="68dba-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
