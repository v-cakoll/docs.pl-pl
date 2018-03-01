---
title: "ICorDebugGuidToTypeEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9993a5aaaef3d5b83d21e3641029af12119188da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="09669-102">ICorDebugGuidToTypeEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="09669-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="09669-103">Udostępnia moduł wyliczający, który definiuje mapowanie między zestaw identyfikatorów GUID i odpowiednie typy, które są reprezentowane przez ICorDebugType wystąpień.</span><span class="sxs-lookup"><span data-stu-id="09669-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="09669-104">Ten interfejs dziedziczy metody interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="09669-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09669-105">Metody</span><span class="sxs-lookup"><span data-stu-id="09669-105">Methods</span></span>  
  
|<span data-ttu-id="09669-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="09669-106">Method</span></span>|<span data-ttu-id="09669-107">Opis</span><span class="sxs-lookup"><span data-stu-id="09669-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09669-108">ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="09669-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="09669-109">Pobiera określoną liczbę [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) wystąpień, które mapują identyfikatory GUID do informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="09669-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09669-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09669-110">Remarks</span></span>  
 <span data-ttu-id="09669-111">`ICorDebugGuidToTypeEnum` Można pobrać obiektu interfejsu, wywołując [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="09669-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="09669-112">Debuger można wywołać tego interfejsu [dalej](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metoda pobierania [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) reprezentacje zarządzane obiekty, które reprezentują mapowania [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów ładowany w domeny aplikacji używane dla wywołania [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="09669-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09669-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09669-113">Requirements</span></span>  
 <span data-ttu-id="09669-114">**Platformy:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09669-114">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="09669-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09669-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09669-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09669-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09669-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09669-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09669-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09669-118">See Also</span></span>  
 [<span data-ttu-id="09669-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="09669-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
