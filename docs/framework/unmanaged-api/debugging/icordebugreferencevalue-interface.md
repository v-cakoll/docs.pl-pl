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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6575acfb1f75cbc8e3d59ddca5fea0953274cf2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206463"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="c1318-102">ICorDebugReferenceValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1318-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="c1318-103">Udostępnia metody zarządzające wartość, która jest odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="c1318-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="c1318-104">(Czyli ten interfejs udostępnia metody zarządzające wskaźnik). Ten interfejs implementuje "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="c1318-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1318-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c1318-105">Methods</span></span>  
  
|<span data-ttu-id="c1318-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c1318-106">Method</span></span>|<span data-ttu-id="c1318-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c1318-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1318-108">Dereference, metoda</span><span class="sxs-lookup"><span data-stu-id="c1318-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="c1318-109">Pobiera obiekt, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="c1318-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="c1318-110">DereferenceStrong, metoda</span><span class="sxs-lookup"><span data-stu-id="c1318-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="c1318-111">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="c1318-111">Not implemented.</span></span> <span data-ttu-id="c1318-112">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="c1318-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="c1318-113">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="c1318-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="c1318-114">Pobiera bieżący adres pamięci przywoływanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c1318-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="c1318-115">IsNull, metoda</span><span class="sxs-lookup"><span data-stu-id="c1318-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="c1318-116">Pobiera wartość wskazującą, czy to `ICorDebugReferenceValue` jest wartość null, w którym to przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.</span><span class="sxs-lookup"><span data-stu-id="c1318-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="c1318-117">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="c1318-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="c1318-118">Ustawia bieżący adres pamięci.</span><span class="sxs-lookup"><span data-stu-id="c1318-118">Sets the current memory address.</span></span> <span data-ttu-id="c1318-119">Oznacza to, że ta metoda Określa `ICorDebugReferenceValue` wskaż obiektu.</span><span class="sxs-lookup"><span data-stu-id="c1318-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1318-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1318-120">Remarks</span></span>  
 <span data-ttu-id="c1318-121">Środowisko uruchomieniowe języka wspólnego (CLR) może wykonać wyrzucania elementów bezużytecznych na obiektach, gdy debugowany proces jest kontynuowany.</span><span class="sxs-lookup"><span data-stu-id="c1318-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="c1318-122">Wyrzucanie elementów bezużytecznych może poruszanie się obiekty w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c1318-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="c1318-123">`ICorDebugReferenceValue` Albo współpracują z wyrzucania elementów bezużytecznych tak, aby pobierał informacje o jest aktualizowany po wyrzucania elementów bezużytecznych lub go zostaną unieważnione niejawnie przed wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c1318-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="c1318-124">`ICorDebugReferenceValue` Obiekt może być niejawnie unieważniony po ciąg dalszy debugowanego procesu.</span><span class="sxs-lookup"><span data-stu-id="c1318-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="c1318-125">Pochodne icordebughandlevalue "—" nie zostaje unieważniony, dopóki zostanie jawnie wydane lub ujawnione.</span><span class="sxs-lookup"><span data-stu-id="c1318-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1318-126">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="c1318-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1318-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1318-127">Requirements</span></span>  
 <span data-ttu-id="c1318-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1318-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1318-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1318-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1318-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1318-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1318-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1318-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1318-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1318-132">See also</span></span>

- [<span data-ttu-id="c1318-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c1318-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
