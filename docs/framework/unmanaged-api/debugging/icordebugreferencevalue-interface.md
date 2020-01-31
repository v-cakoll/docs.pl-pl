---
title: ICorDebugReferenceValue, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: 2efba22b4ec372c5ddedd4982a29d66945d3511c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792134"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="b60d9-102">ICorDebugReferenceValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="b60d9-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="b60d9-103">Dostarcza metody, które zarządzają wartością, która jest odwołaniem do obiektu.</span><span class="sxs-lookup"><span data-stu-id="b60d9-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="b60d9-104">(Oznacza to, że ten interfejs zapewnia metody, które zarządzają wskaźnikiem). Ten interfejs implementuje "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="b60d9-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b60d9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b60d9-105">Methods</span></span>  
  
|<span data-ttu-id="b60d9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b60d9-106">Method</span></span>|<span data-ttu-id="b60d9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b60d9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b60d9-108">Dereference, metoda</span><span class="sxs-lookup"><span data-stu-id="b60d9-108">Dereference Method</span></span>](icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="b60d9-109">Pobiera obiekt, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="b60d9-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="b60d9-110">DereferenceStrong, metoda</span><span class="sxs-lookup"><span data-stu-id="b60d9-110">DereferenceStrong Method</span></span>](icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="b60d9-111">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="b60d9-111">Not implemented.</span></span> <span data-ttu-id="b60d9-112">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="b60d9-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="b60d9-113">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="b60d9-113">GetValue Method</span></span>](icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="b60d9-114">Pobiera bieżący adres pamięci obiektu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="b60d9-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="b60d9-115">IsNull, metoda</span><span class="sxs-lookup"><span data-stu-id="b60d9-115">IsNull Method</span></span>](icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="b60d9-116">Pobiera wartość wskazującą, czy ta `ICorDebugReferenceValue` jest wartością null, w której przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.</span><span class="sxs-lookup"><span data-stu-id="b60d9-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="b60d9-117">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="b60d9-117">SetValue Method</span></span>](icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="b60d9-118">Ustawia bieżący adres pamięci.</span><span class="sxs-lookup"><span data-stu-id="b60d9-118">Sets the current memory address.</span></span> <span data-ttu-id="b60d9-119">Oznacza to, że ta metoda ustawia tę `ICorDebugReferenceValue` tak, aby wskazywała na obiekt.</span><span class="sxs-lookup"><span data-stu-id="b60d9-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b60d9-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b60d9-120">Remarks</span></span>  
 <span data-ttu-id="b60d9-121">Środowisko uruchomieniowe języka wspólnego (CLR) może wykonywać odzyskiwanie pamięci na obiektach, gdy debugowany proces jest kontynuowany.</span><span class="sxs-lookup"><span data-stu-id="b60d9-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="b60d9-122">Wyrzucanie elementów bezużytecznych może przenosić obiekty w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b60d9-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="b60d9-123">`ICorDebugReferenceValue` będzie współpracować z wyrzucaniem elementów bezużytecznych, dzięki czemu informacje są aktualizowane po wyrzucaniu elementów bezużytecznych lub zostaną unieważnione niejawnie przed wyrzucaniem elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b60d9-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="b60d9-124">Obiekt `ICorDebugReferenceValue` może być niejawnie unieważniony po dalszym debugowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="b60d9-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="b60d9-125">Pochodny element "ICorDebugHandleValue" nie jest unieważniony, dopóki nie zostanie jawnie wystawiony lub ujawniony.</span><span class="sxs-lookup"><span data-stu-id="b60d9-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b60d9-126">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b60d9-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b60d9-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b60d9-127">Requirements</span></span>  
 <span data-ttu-id="b60d9-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b60d9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b60d9-129">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b60d9-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b60d9-130">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b60d9-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b60d9-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b60d9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b60d9-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b60d9-132">See also</span></span>

- [<span data-ttu-id="b60d9-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b60d9-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
