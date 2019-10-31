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
ms.openlocfilehash: da921644c4d967efb0d88060ada0332c5eb63965
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138532"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="bc6ef-102">ICorDebugGuidToTypeEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bc6ef-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="bc6ef-103">Dostarcza moduł wyliczający, który definiuje mapowanie między zestawem identyfikatorów GUID i odpowiadającymi im typami, które są reprezentowane przez wystąpienia ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="bc6ef-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="bc6ef-104">Ten interfejs dziedziczy metody z interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="bc6ef-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc6ef-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bc6ef-105">Methods</span></span>  
  
|<span data-ttu-id="bc6ef-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="bc6ef-106">Method</span></span>|<span data-ttu-id="bc6ef-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bc6ef-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc6ef-108">ICorDebugGuidToTypeEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="bc6ef-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="bc6ef-109">Pobiera określoną liczbę wystąpień [CorDebugGuidToTypeMapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , które MAPUJĄ identyfikatory GUID na informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="bc6ef-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc6ef-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc6ef-110">Remarks</span></span>  
 <span data-ttu-id="bc6ef-111">Obiekt interfejsu `ICorDebugGuidToTypeEnum` można pobrać, wywołując metodę [ICorDebugAppDomain3:: GetCachedWinRTTypes —](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bc6ef-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="bc6ef-112">Debuger może wywołać [kolejną](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metodę tego interfejsu, aby pobrać obiekty [CorDebugGuidToTypeMapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) reprezentujące mapowania zarządzanych reprezentacji typów środowisko wykonawcze systemu Windows załadowanych w domenie aplikacji używanej do wywołania [ ICorDebugAppDomain3:: GetCachedWinRTTypes —](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) , metoda.</span><span class="sxs-lookup"><span data-stu-id="bc6ef-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc6ef-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc6ef-113">Requirements</span></span>  
 <span data-ttu-id="bc6ef-114">**Platformy:** środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bc6ef-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="bc6ef-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc6ef-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc6ef-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bc6ef-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc6ef-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc6ef-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6ef-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc6ef-118">See also</span></span>

- [<span data-ttu-id="bc6ef-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bc6ef-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
