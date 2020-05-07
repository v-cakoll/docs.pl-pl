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
ms.openlocfilehash: 528db447df4d71d67441b05ad29e6a900c59afbb
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892820"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="99fb1-102">ICorDebugComObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="99fb1-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="99fb1-103">Dostarcza metody do pobierania informacji skojarzonych z otoką w czasie wykonywania (otoka).</span><span class="sxs-lookup"><span data-stu-id="99fb1-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99fb1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="99fb1-104">Methods</span></span>  
  
|<span data-ttu-id="99fb1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="99fb1-105">Method</span></span>|<span data-ttu-id="99fb1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="99fb1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99fb1-107">GetCachedInterfacePointers, metoda</span><span class="sxs-lookup"><span data-stu-id="99fb1-107">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="99fb1-108">Pobiera pierwotne wskaźniki interfejsu w pamięci podręcznej w bieżącej otoki RCW.</span><span class="sxs-lookup"><span data-stu-id="99fb1-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="99fb1-109">GetCachedInterfaceTypes, metoda</span><span class="sxs-lookup"><span data-stu-id="99fb1-109">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="99fb1-110">Dostarcza moduł wyliczający dla typów interfejsów, do których jest uwzględniany bieżący obiekt lub do których służy.</span><span class="sxs-lookup"><span data-stu-id="99fb1-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99fb1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99fb1-111">Remarks</span></span>  
 <span data-ttu-id="99fb1-112">Aby sprawdzić, czy wystąpienie interfejsu "ICorDebugValue" reprezentuje otokę RCW, debuger wywołuje `QueryInterface` polecenie "ICorDebugValue" z. `IID_ICorDebugComObjectValue`</span><span class="sxs-lookup"><span data-stu-id="99fb1-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99fb1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99fb1-113">Requirements</span></span>  
 <span data-ttu-id="99fb1-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99fb1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99fb1-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="99fb1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99fb1-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="99fb1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99fb1-117">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99fb1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fb1-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99fb1-118">See also</span></span>

- [<span data-ttu-id="99fb1-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="99fb1-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="99fb1-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="99fb1-120">Debugging</span></span>](index.md)
