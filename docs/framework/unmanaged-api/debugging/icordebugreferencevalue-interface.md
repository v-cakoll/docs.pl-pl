---
title: ICorDebugReferenceValue — Interfejs
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4709d1b8126436d4400c788891960100915cd1bc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971440"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="585cd-102">ICorDebugReferenceValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="585cd-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="585cd-103">Udostępnia metody zarządzające wartość, która jest odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="585cd-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="585cd-104">(Czyli ten interfejs udostępnia metody zarządzające wskaźnik). Ten interfejs implementuje "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="585cd-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="585cd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="585cd-105">Methods</span></span>  
  
|<span data-ttu-id="585cd-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="585cd-106">Method</span></span>|<span data-ttu-id="585cd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="585cd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="585cd-108">Dereference, metoda</span><span class="sxs-lookup"><span data-stu-id="585cd-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="585cd-109">Pobiera obiekt, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="585cd-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="585cd-110">DereferenceStrong, metoda</span><span class="sxs-lookup"><span data-stu-id="585cd-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="585cd-111">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="585cd-111">Not implemented.</span></span> <span data-ttu-id="585cd-112">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="585cd-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="585cd-113">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="585cd-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="585cd-114">Pobiera bieżący adres pamięci przywoływanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="585cd-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="585cd-115">IsNull, metoda</span><span class="sxs-lookup"><span data-stu-id="585cd-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="585cd-116">Pobiera wartość wskazującą, czy to `ICorDebugReferenceValue` jest wartość null, w którym to przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.</span><span class="sxs-lookup"><span data-stu-id="585cd-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="585cd-117">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="585cd-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="585cd-118">Ustawia bieżący adres pamięci.</span><span class="sxs-lookup"><span data-stu-id="585cd-118">Sets the current memory address.</span></span> <span data-ttu-id="585cd-119">Oznacza to, że ta metoda Określa `ICorDebugReferenceValue` wskaż obiektu.</span><span class="sxs-lookup"><span data-stu-id="585cd-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="585cd-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="585cd-120">Remarks</span></span>  
 <span data-ttu-id="585cd-121">Środowisko uruchomieniowe języka wspólnego (CLR) może wykonać wyrzucania elementów bezużytecznych na obiektach, gdy debugowany proces jest kontynuowany.</span><span class="sxs-lookup"><span data-stu-id="585cd-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="585cd-122">Wyrzucanie elementów bezużytecznych może poruszanie się obiekty w pamięci.</span><span class="sxs-lookup"><span data-stu-id="585cd-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="585cd-123">`ICorDebugReferenceValue` Albo współpracują z wyrzucania elementów bezużytecznych tak, aby pobierał informacje o jest aktualizowany po wyrzucania elementów bezużytecznych lub go zostaną unieważnione niejawnie przed wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="585cd-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="585cd-124">`ICorDebugReferenceValue` Obiekt może być niejawnie unieważniony po ciąg dalszy debugowanego procesu.</span><span class="sxs-lookup"><span data-stu-id="585cd-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="585cd-125">Pochodne icordebughandlevalue "—" nie zostaje unieważniony, dopóki zostanie jawnie wydane lub ujawnione.</span><span class="sxs-lookup"><span data-stu-id="585cd-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="585cd-126">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="585cd-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="585cd-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="585cd-127">Requirements</span></span>  
 <span data-ttu-id="585cd-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="585cd-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="585cd-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="585cd-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="585cd-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="585cd-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="585cd-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="585cd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="585cd-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="585cd-132">See also</span></span>


- [<span data-ttu-id="585cd-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="585cd-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
