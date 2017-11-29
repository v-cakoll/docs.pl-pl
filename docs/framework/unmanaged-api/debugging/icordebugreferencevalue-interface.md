---
title: ICorDebugReferenceValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue
helpviewer_keywords: ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d11cb4cbd6baa1e0d381c9fb11d5a3343287cf55
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugreferencevalue-interface1"></a><span data-ttu-id="251c3-102">ICorDebugReferenceValue Interface1</span><span class="sxs-lookup"><span data-stu-id="251c3-102">ICorDebugReferenceValue Interface1</span></span>
<span data-ttu-id="251c3-103">Udostępnia metody zarządzające wartość, która jest odwołaniem do obiektu.</span><span class="sxs-lookup"><span data-stu-id="251c3-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="251c3-104">(To znaczy, że ten interfejs udostępnia metody zarządzające wskaźnik). Ten interfejs implementuje "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="251c3-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="251c3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="251c3-105">Methods</span></span>  
  
|<span data-ttu-id="251c3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="251c3-106">Method</span></span>|<span data-ttu-id="251c3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="251c3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="251c3-108">Dereference — metoda</span><span class="sxs-lookup"><span data-stu-id="251c3-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="251c3-109">Pobiera obiekt, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="251c3-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="251c3-110">DereferenceStrong — metoda</span><span class="sxs-lookup"><span data-stu-id="251c3-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="251c3-111">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="251c3-111">Not implemented.</span></span> <span data-ttu-id="251c3-112">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="251c3-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="251c3-113">GetValue — metoda</span><span class="sxs-lookup"><span data-stu-id="251c3-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="251c3-114">Pobiera bieżący adres pamięci odwołuje się do obiektu.</span><span class="sxs-lookup"><span data-stu-id="251c3-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="251c3-115">IsNull — metoda</span><span class="sxs-lookup"><span data-stu-id="251c3-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="251c3-116">Pobiera wartość wskazującą, czy to `ICorDebugReferenceValue` jest wartość null, w którym to przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.</span><span class="sxs-lookup"><span data-stu-id="251c3-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="251c3-117">SetValue — metoda</span><span class="sxs-lookup"><span data-stu-id="251c3-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="251c3-118">Ustawia bieżący adres pamięci.</span><span class="sxs-lookup"><span data-stu-id="251c3-118">Sets the current memory address.</span></span> <span data-ttu-id="251c3-119">Oznacza to, że ta metoda określa tę `ICorDebugReferenceValue` wskaż obiekt.</span><span class="sxs-lookup"><span data-stu-id="251c3-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="251c3-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="251c3-120">Remarks</span></span>  
 <span data-ttu-id="251c3-121">Środowisko uruchomieniowe języka wspólnego (CLR) może wykonać wyrzucania elementów bezużytecznych w obiektach, jeśli debugowany proces jest kontynuowany.</span><span class="sxs-lookup"><span data-stu-id="251c3-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="251c3-122">Wyrzucanie elementów bezużytecznych może poruszanie się obiekty w pamięci.</span><span class="sxs-lookup"><span data-stu-id="251c3-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="251c3-123">`ICorDebugReferenceValue` Albo współpracują z wyrzucanie elementów bezużytecznych tak, aby jego informacje są aktualizowane po wyrzucanie elementów bezużytecznych lub jego zostaną unieważnione niejawnie przed wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="251c3-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="251c3-124">`ICorDebugReferenceValue` Obiekt może być niejawnie nieważne po debugowanym procesie jest kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="251c3-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="251c3-125">Pochodne "ICorDebugHandleValue" nie zostało unieważnione, dopóki zostanie jawnie wydane lub udostępniane.</span><span class="sxs-lookup"><span data-stu-id="251c3-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="251c3-126">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="251c3-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="251c3-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="251c3-127">Requirements</span></span>  
 <span data-ttu-id="251c3-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="251c3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="251c3-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="251c3-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="251c3-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="251c3-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="251c3-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="251c3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251c3-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="251c3-132">See Also</span></span>  
    
    
 [<span data-ttu-id="251c3-133">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="251c3-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
