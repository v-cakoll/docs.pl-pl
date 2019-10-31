---
title: ICorDebugObjectValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: b782207503a2c3f739a30f68d509e6b481d2b6a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129752"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="59ee5-102">ICorDebugObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="59ee5-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="59ee5-103">Podklasa elementu "ICorDebugValue" reprezentująca wartość, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="59ee5-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59ee5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="59ee5-104">Methods</span></span>  
  
|<span data-ttu-id="59ee5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="59ee5-105">Method</span></span>|<span data-ttu-id="59ee5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="59ee5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59ee5-107">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="59ee5-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="59ee5-108">Pobiera wskaźnik interfejsu do <xref:System.Type> środowiska uruchomieniowego języka wspólnego (CLR) obiektu, do którego odwołuje się ta `ICorDebugObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="59ee5-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="59ee5-109">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="59ee5-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="59ee5-110">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="59ee5-110">Not implemented.</span></span>|  
|[<span data-ttu-id="59ee5-111">GetFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="59ee5-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="59ee5-112">Pobiera wskaźnik interfejsu do elementu [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , który reprezentuje wartość określonego pola określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="59ee5-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="59ee5-113">GetManagedCopy, metoda</span><span class="sxs-lookup"><span data-stu-id="59ee5-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="59ee5-114">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="59ee5-114">Obsolete.</span></span> <span data-ttu-id="59ee5-115">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="59ee5-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="59ee5-116">GetVirtualMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="59ee5-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="59ee5-117">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="59ee5-117">Not implemented.</span></span>|  
|[<span data-ttu-id="59ee5-118">IsValueClass, metoda</span><span class="sxs-lookup"><span data-stu-id="59ee5-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="59ee5-119">Pobiera wartość wskazującą, czy obiekt, do którego odwołuje się ten `ICorDebugObjectValue`, jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="59ee5-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="59ee5-120">SetFromManagedCopy, metoda</span><span class="sxs-lookup"><span data-stu-id="59ee5-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="59ee5-121">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="59ee5-121">Obsolete.</span></span> <span data-ttu-id="59ee5-122">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="59ee5-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ee5-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59ee5-123">Remarks</span></span>  
 <span data-ttu-id="59ee5-124">`ICorDebugObjectValue` pozostaje ważna do momentu kontynuowania debugowanego procesu.</span><span class="sxs-lookup"><span data-stu-id="59ee5-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59ee5-125">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="59ee5-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ee5-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59ee5-126">Requirements</span></span>  
 <span data-ttu-id="59ee5-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59ee5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ee5-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="59ee5-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59ee5-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="59ee5-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59ee5-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59ee5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ee5-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59ee5-131">See also</span></span>

- [<span data-ttu-id="59ee5-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="59ee5-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
