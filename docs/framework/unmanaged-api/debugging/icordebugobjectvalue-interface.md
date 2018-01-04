---
title: ICorDebugObjectValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue
helpviewer_keywords: ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6dfde9f212936b1a0d0f5a6e76eafd4a2e62356c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvalue-interface1"></a><span data-ttu-id="12293-102">ICorDebugObjectValue Interface1</span><span class="sxs-lookup"><span data-stu-id="12293-102">ICorDebugObjectValue Interface1</span></span>
<span data-ttu-id="12293-103">Podklasa "ICorDebugValue", który reprezentuje wartość, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="12293-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12293-104">Metody</span><span class="sxs-lookup"><span data-stu-id="12293-104">Methods</span></span>  
  
|<span data-ttu-id="12293-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="12293-105">Method</span></span>|<span data-ttu-id="12293-106">Opis</span><span class="sxs-lookup"><span data-stu-id="12293-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12293-107">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="12293-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="12293-108">Pobiera wskaźnika interfejsu, aby środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.Type> obiektu tego `ICorDebugObjectValue` odwołania.</span><span class="sxs-lookup"><span data-stu-id="12293-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="12293-109">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="12293-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="12293-110">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="12293-110">Not implemented.</span></span>|  
|[<span data-ttu-id="12293-111">GetFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="12293-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="12293-112">Pobiera wskaźnika interfejsu do [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) reprezentujący wartość określonego pola określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="12293-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="12293-113">GetManagedCopy, metoda</span><span class="sxs-lookup"><span data-stu-id="12293-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="12293-114">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12293-114">Obsolete.</span></span> <span data-ttu-id="12293-115">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="12293-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="12293-116">GetVirtualMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="12293-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="12293-117">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="12293-117">Not implemented.</span></span>|  
|[<span data-ttu-id="12293-118">IsValueClass, metoda</span><span class="sxs-lookup"><span data-stu-id="12293-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="12293-119">Pobiera wartość wskazującą, czy obiekt odwołuje się ten `ICorDebugObjectValue` jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="12293-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="12293-120">SetFromManagedCopy, metoda</span><span class="sxs-lookup"><span data-stu-id="12293-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="12293-121">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12293-121">Obsolete.</span></span> <span data-ttu-id="12293-122">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="12293-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12293-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12293-123">Remarks</span></span>  
 <span data-ttu-id="12293-124">`ICorDebugObjectValue` Pozostaje ważny aż debugowany proces jest kontynuowany.</span><span class="sxs-lookup"><span data-stu-id="12293-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12293-125">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="12293-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12293-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12293-126">Requirements</span></span>  
 <span data-ttu-id="12293-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12293-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12293-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12293-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12293-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12293-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12293-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12293-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12293-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12293-131">See Also</span></span>  
 [<span data-ttu-id="12293-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="12293-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
