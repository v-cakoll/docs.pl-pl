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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098627"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="3bfea-102">ICorDebugComObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3bfea-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="3bfea-103">Udostępnia metody, aby pobrać informacje skojarzone z wywoływana otoka środowiska uruchomieniowego (RCW).</span><span class="sxs-lookup"><span data-stu-id="3bfea-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3bfea-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3bfea-104">Methods</span></span>  
  
|<span data-ttu-id="3bfea-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3bfea-105">Method</span></span>|<span data-ttu-id="3bfea-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3bfea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3bfea-107">GetCachedInterfacePointers, metoda</span><span class="sxs-lookup"><span data-stu-id="3bfea-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="3bfea-108">Pobiera wskaźniki interfejsu raw, buforowane na bieżącym RCW.</span><span class="sxs-lookup"><span data-stu-id="3bfea-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="3bfea-109">GetCachedInterfaceTypes, metoda</span><span class="sxs-lookup"><span data-stu-id="3bfea-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="3bfea-110">Dostarcza moduł wyliczający dla typów interfejsu, czy bieżący obiekt został z uwzględnieniem wielkości liter do lub używany jako.</span><span class="sxs-lookup"><span data-stu-id="3bfea-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bfea-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3bfea-111">Remarks</span></span>  
 <span data-ttu-id="3bfea-112">Aby sprawdzić, czy wystąpienie interfejsu "ICorDebugValue" reprezentuje RCW, wywołuje debugera `QueryInterface` na "ICorDebugValue" za pomocą `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="3bfea-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bfea-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bfea-113">Requirements</span></span>  
 <span data-ttu-id="3bfea-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bfea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bfea-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bfea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bfea-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bfea-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3bfea-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3bfea-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3bfea-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bfea-118">See also</span></span>

- [<span data-ttu-id="3bfea-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3bfea-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3bfea-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3bfea-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
