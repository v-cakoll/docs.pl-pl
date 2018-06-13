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
ms.openlocfilehash: 91d653587d5b7c35a2a43c7eed7c4bf33e5401f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416754"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="461cf-102">ICorDebugGuidToTypeEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="461cf-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="461cf-103">Udostępnia moduł wyliczający, który definiuje mapowanie między zestaw identyfikatorów GUID i odpowiednie typy, które są reprezentowane przez ICorDebugType wystąpień.</span><span class="sxs-lookup"><span data-stu-id="461cf-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="461cf-104">Ten interfejs dziedziczy metody interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="461cf-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="461cf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="461cf-105">Methods</span></span>  
  
|<span data-ttu-id="461cf-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="461cf-106">Method</span></span>|<span data-ttu-id="461cf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="461cf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="461cf-108">ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="461cf-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="461cf-109">Pobiera określoną liczbę [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) wystąpień, które mapują identyfikatory GUID do informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="461cf-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="461cf-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="461cf-110">Remarks</span></span>  
 <span data-ttu-id="461cf-111">`ICorDebugGuidToTypeEnum` Można pobrać obiektu interfejsu, wywołując [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="461cf-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="461cf-112">Debuger można wywołać tego interfejsu [dalej](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metoda pobierania [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) reprezentacje zarządzane obiekty, które reprezentują mapowania [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów ładowany w domeny aplikacji używane dla wywołania [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="461cf-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="461cf-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="461cf-113">Requirements</span></span>  
 <span data-ttu-id="461cf-114">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="461cf-114">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="461cf-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="461cf-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="461cf-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="461cf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="461cf-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="461cf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="461cf-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="461cf-118">See Also</span></span>  
 [<span data-ttu-id="461cf-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="461cf-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
