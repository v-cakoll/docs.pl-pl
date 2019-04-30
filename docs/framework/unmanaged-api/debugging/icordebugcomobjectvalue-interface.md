---
title: ICorDebugComObjectValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3387985ebf6027b9cd9dee372190da65939dbae3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749700"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="4536d-102">ICorDebugComObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4536d-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="4536d-103">Udostępnia metody, aby pobrać informacje skojarzone z wywoływana otoka środowiska uruchomieniowego (RCW).</span><span class="sxs-lookup"><span data-stu-id="4536d-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4536d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4536d-104">Methods</span></span>  
  
|<span data-ttu-id="4536d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4536d-105">Method</span></span>|<span data-ttu-id="4536d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4536d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4536d-107">GetCachedInterfacePointers, metoda</span><span class="sxs-lookup"><span data-stu-id="4536d-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="4536d-108">Pobiera wskaźniki interfejsu raw, buforowane na bieżącym RCW.</span><span class="sxs-lookup"><span data-stu-id="4536d-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="4536d-109">GetCachedInterfaceTypes, metoda</span><span class="sxs-lookup"><span data-stu-id="4536d-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="4536d-110">Dostarcza moduł wyliczający dla typów interfejsu, czy bieżący obiekt został z uwzględnieniem wielkości liter do lub używany jako.</span><span class="sxs-lookup"><span data-stu-id="4536d-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4536d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4536d-111">Remarks</span></span>  
 <span data-ttu-id="4536d-112">Aby sprawdzić, czy wystąpienie interfejsu "ICorDebugValue" reprezentuje RCW, wywołuje debugera `QueryInterface` na "ICorDebugValue" za pomocą `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="4536d-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4536d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4536d-113">Requirements</span></span>  
 <span data-ttu-id="4536d-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4536d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4536d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4536d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4536d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4536d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4536d-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4536d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4536d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4536d-118">See also</span></span>

- [<span data-ttu-id="4536d-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4536d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4536d-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4536d-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
