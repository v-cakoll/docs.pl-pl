---
title: "ICorDebugComObjectValue — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugComObjectValue
helpviewer_keywords: ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d339d3146a8a9214c3518eac6c31ed5222f9b31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="2ef6f-102">ICorDebugComObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2ef6f-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="2ef6f-103">Udostępnia metody, aby pobrać informacje związane z wywoływana otoka środowiska uruchomieniowego (otoki RCW).</span><span class="sxs-lookup"><span data-stu-id="2ef6f-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2ef6f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2ef6f-104">Methods</span></span>  
  
|<span data-ttu-id="2ef6f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2ef6f-105">Method</span></span>|<span data-ttu-id="2ef6f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2ef6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ef6f-107">GetCachedInterfacePointers — metoda</span><span class="sxs-lookup"><span data-stu-id="2ef6f-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="2ef6f-108">Pobiera wskaźniki interfejsu pierwotnego w bieżącym otoki RCW pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2ef6f-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="2ef6f-109">GetCachedInterfaceTypes — metoda</span><span class="sxs-lookup"><span data-stu-id="2ef6f-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="2ef6f-110">Udostępnia moduł wyliczający dla typów interfejsu, czy bieżący obiekt został do wielkości liter lub używane jako.</span><span class="sxs-lookup"><span data-stu-id="2ef6f-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ef6f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ef6f-111">Remarks</span></span>  
 <span data-ttu-id="2ef6f-112">Aby sprawdzić, czy wystąpienie interfejsu "ICorDebugValue" reprezentuje otoki RCW, wywołuje debugera `QueryInterface` na "ICorDebugValue" z `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="2ef6f-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ef6f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ef6f-113">Requirements</span></span>  
 <span data-ttu-id="2ef6f-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ef6f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ef6f-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ef6f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ef6f-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ef6f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ef6f-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ef6f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ef6f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ef6f-118">See Also</span></span>  
 [<span data-ttu-id="2ef6f-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="2ef6f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2ef6f-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2ef6f-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
