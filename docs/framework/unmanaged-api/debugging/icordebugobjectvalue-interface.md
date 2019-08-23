---
title: ICorDebugObjectValue, interfejs
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4ca59aac075a42294026ad54c5d5dd4dbf7fda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943334"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="5e99e-102">ICorDebugObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e99e-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="5e99e-103">Podklasa elementu "ICorDebugValue" reprezentująca wartość, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="5e99e-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e99e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5e99e-104">Methods</span></span>  
  
|<span data-ttu-id="5e99e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5e99e-105">Method</span></span>|<span data-ttu-id="5e99e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5e99e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e99e-107">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="5e99e-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="5e99e-108">Pobiera wskaźnik interfejsu do środowiska uruchomieniowego języka wspólnego (CLR) <xref:System.Type> obiektu, do którego odwołuje się to `ICorDebugObjectValue` odwołanie.</span><span class="sxs-lookup"><span data-stu-id="5e99e-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="5e99e-109">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="5e99e-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="5e99e-110">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="5e99e-110">Not implemented.</span></span>|  
|[<span data-ttu-id="5e99e-111">GetFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="5e99e-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="5e99e-112">Pobiera wskaźnik interfejsu do elementu [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , który reprezentuje wartość określonego pola określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="5e99e-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="5e99e-113">GetManagedCopy, metoda</span><span class="sxs-lookup"><span data-stu-id="5e99e-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="5e99e-114">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="5e99e-114">Obsolete.</span></span> <span data-ttu-id="5e99e-115">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="5e99e-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="5e99e-116">GetVirtualMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="5e99e-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="5e99e-117">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="5e99e-117">Not implemented.</span></span>|  
|[<span data-ttu-id="5e99e-118">IsValueClass, metoda</span><span class="sxs-lookup"><span data-stu-id="5e99e-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="5e99e-119">Pobiera wartość wskazującą, czy obiekt, do którego odwołuje `ICorDebugObjectValue` się to typ wartości.</span><span class="sxs-lookup"><span data-stu-id="5e99e-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="5e99e-120">SetFromManagedCopy, metoda</span><span class="sxs-lookup"><span data-stu-id="5e99e-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="5e99e-121">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="5e99e-121">Obsolete.</span></span> <span data-ttu-id="5e99e-122">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="5e99e-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e99e-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e99e-123">Remarks</span></span>  
 <span data-ttu-id="5e99e-124">`ICorDebugObjectValue` Pozostanie on ważny do momentu, gdy debugowany proces jest kontynuowany.</span><span class="sxs-lookup"><span data-stu-id="5e99e-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e99e-125">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="5e99e-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e99e-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e99e-126">Requirements</span></span>  
 <span data-ttu-id="5e99e-127">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e99e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e99e-128">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e99e-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e99e-129">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e99e-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e99e-130">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e99e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e99e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e99e-131">See also</span></span>

- [<span data-ttu-id="5e99e-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5e99e-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
