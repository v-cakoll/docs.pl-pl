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
ms.openlocfilehash: 4ff5c0d470e6eb84eb8b526f5e8f74e5e1a8118a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125486"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="38cb8-102">ICorDebugComObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="38cb8-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="38cb8-103">Dostarcza metody do pobierania informacji skojarzonych z otoką w czasie wykonywania (otoka).</span><span class="sxs-lookup"><span data-stu-id="38cb8-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38cb8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="38cb8-104">Methods</span></span>  
  
|<span data-ttu-id="38cb8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="38cb8-105">Method</span></span>|<span data-ttu-id="38cb8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="38cb8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38cb8-107">GetCachedInterfacePointers, metoda</span><span class="sxs-lookup"><span data-stu-id="38cb8-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="38cb8-108">Pobiera pierwotne wskaźniki interfejsu w pamięci podręcznej w bieżącej otoki RCW.</span><span class="sxs-lookup"><span data-stu-id="38cb8-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="38cb8-109">GetCachedInterfaceTypes, metoda</span><span class="sxs-lookup"><span data-stu-id="38cb8-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="38cb8-110">Dostarcza moduł wyliczający dla typów interfejsów, do których jest uwzględniany bieżący obiekt lub do których służy.</span><span class="sxs-lookup"><span data-stu-id="38cb8-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38cb8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38cb8-111">Remarks</span></span>  
 <span data-ttu-id="38cb8-112">Aby sprawdzić, czy wystąpienie interfejsu "ICorDebugValue" reprezentuje otokę RCW, debuger wywołuje `QueryInterface` w "ICorDebugValue" z `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="38cb8-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38cb8-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38cb8-113">Requirements</span></span>  
 <span data-ttu-id="38cb8-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38cb8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38cb8-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="38cb8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38cb8-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="38cb8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38cb8-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38cb8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38cb8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38cb8-118">See also</span></span>

- [<span data-ttu-id="38cb8-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="38cb8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="38cb8-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="38cb8-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
