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
ms.openlocfilehash: d0ac91681313b60ebfcaf725dcc2e0d6547e3c1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987821"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="ab696-102">ICorDebugObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab696-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="ab696-103">Podklasa klasy "ICorDebugValue", która reprezentuje wartość, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="ab696-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab696-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ab696-104">Methods</span></span>  
  
|<span data-ttu-id="ab696-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab696-105">Method</span></span>|<span data-ttu-id="ab696-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ab696-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab696-107">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="ab696-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="ab696-108">Pobiera wskaźnik interfejsu do środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.Type> obiektu że `ICorDebugObjectValue` odwołania.</span><span class="sxs-lookup"><span data-stu-id="ab696-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="ab696-109">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="ab696-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="ab696-110">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="ab696-110">Not implemented.</span></span>|  
|[<span data-ttu-id="ab696-111">GetFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="ab696-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="ab696-112">Pobiera wskaźnik interfejsu do [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) reprezentująca wartość określonego pola określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="ab696-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="ab696-113">GetManagedCopy, metoda</span><span class="sxs-lookup"><span data-stu-id="ab696-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="ab696-114">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="ab696-114">Obsolete.</span></span> <span data-ttu-id="ab696-115">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="ab696-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="ab696-116">GetVirtualMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="ab696-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="ab696-117">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="ab696-117">Not implemented.</span></span>|  
|[<span data-ttu-id="ab696-118">IsValueClass, metoda</span><span class="sxs-lookup"><span data-stu-id="ab696-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="ab696-119">Pobiera wartość wskazującą, czy obiekt odwołuje się ten `ICorDebugObjectValue` jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="ab696-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="ab696-120">SetFromManagedCopy, metoda</span><span class="sxs-lookup"><span data-stu-id="ab696-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="ab696-121">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="ab696-121">Obsolete.</span></span> <span data-ttu-id="ab696-122">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="ab696-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab696-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab696-123">Remarks</span></span>  
 <span data-ttu-id="ab696-124">`ICorDebugObjectValue` Pozostaje ważny, dopóki debugowany proces jest kontynuowany.</span><span class="sxs-lookup"><span data-stu-id="ab696-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab696-125">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="ab696-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab696-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab696-126">Requirements</span></span>  
 <span data-ttu-id="ab696-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab696-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab696-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab696-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab696-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab696-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab696-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab696-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab696-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab696-131">See also</span></span>

- [<span data-ttu-id="ab696-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ab696-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
