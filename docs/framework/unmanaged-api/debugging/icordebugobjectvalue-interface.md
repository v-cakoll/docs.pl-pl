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
ms.openlocfilehash: 603ab20b57dc4ba736b0342797d0be649a5bebc4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207481"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="a2384-102">ICorDebugObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2384-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="a2384-103">Podklasa elementu "ICorDebugValue" reprezentująca wartość, która zawiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="a2384-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2384-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a2384-104">Methods</span></span>  
  
|<span data-ttu-id="a2384-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a2384-105">Method</span></span>|<span data-ttu-id="a2384-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a2384-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2384-107">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="a2384-107">GetClass Method</span></span>](icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="a2384-108">Pobiera wskaźnik interfejsu do środowiska uruchomieniowego języka wspólnego (CLR) <xref:System.Type> obiektu, do którego `ICorDebugObjectValue` odwołuje się to odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a2384-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="a2384-109">GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2384-109">GetContext Method</span></span>](icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="a2384-110">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="a2384-110">Not implemented.</span></span>|  
|[<span data-ttu-id="a2384-111">GetFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="a2384-111">GetFieldValue Method</span></span>](icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="a2384-112">Pobiera wskaźnik interfejsu do elementu [ICorDebugValue](icordebugvalue-interface.md) , który reprezentuje wartość określonego pola określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="a2384-112">Gets an interface pointer to an [ICorDebugValue](icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="a2384-113">GetManagedCopy, metoda</span><span class="sxs-lookup"><span data-stu-id="a2384-113">GetManagedCopy Method</span></span>](icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="a2384-114">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="a2384-114">Obsolete.</span></span> <span data-ttu-id="a2384-115">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="a2384-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="a2384-116">GetVirtualMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="a2384-116">GetVirtualMethod Method</span></span>](icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="a2384-117">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="a2384-117">Not implemented.</span></span>|  
|[<span data-ttu-id="a2384-118">IsValueClass, metoda</span><span class="sxs-lookup"><span data-stu-id="a2384-118">IsValueClass Method</span></span>](icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="a2384-119">Pobiera wartość wskazującą, czy obiekt, do którego odwołuje się to `ICorDebugObjectValue` Typ wartości.</span><span class="sxs-lookup"><span data-stu-id="a2384-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="a2384-120">SetFromManagedCopy, metoda</span><span class="sxs-lookup"><span data-stu-id="a2384-120">SetFromManagedCopy Method</span></span>](icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="a2384-121">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="a2384-121">Obsolete.</span></span> <span data-ttu-id="a2384-122">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="a2384-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2384-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2384-123">Remarks</span></span>  
 <span data-ttu-id="a2384-124">`ICorDebugObjectValue`Pozostanie on ważny do momentu, gdy debugowany proces jest kontynuowany.</span><span class="sxs-lookup"><span data-stu-id="a2384-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2384-125">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a2384-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2384-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2384-126">Requirements</span></span>  
 <span data-ttu-id="a2384-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2384-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2384-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a2384-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2384-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a2384-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2384-130">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2384-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2384-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2384-131">See also</span></span>

- [<span data-ttu-id="a2384-132">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a2384-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
