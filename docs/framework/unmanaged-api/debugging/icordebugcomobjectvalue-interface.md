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
ms.openlocfilehash: ed5b39ed4b2a14c071bf23fb04efbad6834e8a9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783970"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="0c68e-102">ICorDebugComObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0c68e-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="0c68e-103">Dostarcza metody do pobierania informacji skojarzonych z otoką w czasie wykonywania (otoka).</span><span class="sxs-lookup"><span data-stu-id="0c68e-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c68e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0c68e-104">Methods</span></span>  
  
|<span data-ttu-id="0c68e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0c68e-105">Method</span></span>|<span data-ttu-id="0c68e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0c68e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c68e-107">GetCachedInterfacePointers, metoda</span><span class="sxs-lookup"><span data-stu-id="0c68e-107">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="0c68e-108">Pobiera pierwotne wskaźniki interfejsu w pamięci podręcznej w bieżącej otoki RCW.</span><span class="sxs-lookup"><span data-stu-id="0c68e-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="0c68e-109">GetCachedInterfaceTypes, metoda</span><span class="sxs-lookup"><span data-stu-id="0c68e-109">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="0c68e-110">Dostarcza moduł wyliczający dla typów interfejsów, do których jest uwzględniany bieżący obiekt lub do których służy.</span><span class="sxs-lookup"><span data-stu-id="0c68e-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c68e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c68e-111">Remarks</span></span>  
 <span data-ttu-id="0c68e-112">Aby sprawdzić, czy wystąpienie interfejsu "ICorDebugValue" reprezentuje otokę RCW, debuger wywołuje `QueryInterface` w "ICorDebugValue" z `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="0c68e-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c68e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c68e-113">Requirements</span></span>  
 <span data-ttu-id="0c68e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c68e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c68e-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0c68e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c68e-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0c68e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c68e-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c68e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c68e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c68e-118">See also</span></span>

- [<span data-ttu-id="0c68e-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0c68e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0c68e-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0c68e-120">Debugging</span></span>](index.md)
