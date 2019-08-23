---
title: ICorDebugClass, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5099af23a2b706694bfcb655d295607c97ea8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969280"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="0997e-102">ICorDebugClass, interfejs</span><span class="sxs-lookup"><span data-stu-id="0997e-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="0997e-103">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="0997e-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="0997e-104">Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0997e-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0997e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0997e-105">Methods</span></span>  
  
|<span data-ttu-id="0997e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0997e-106">Method</span></span>|<span data-ttu-id="0997e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0997e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0997e-108">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="0997e-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="0997e-109">Pobiera moduł, który definiuje tę klasę.</span><span class="sxs-lookup"><span data-stu-id="0997e-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="0997e-110">GetStaticFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="0997e-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="0997e-111">Pobiera wartość określonego pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="0997e-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="0997e-112">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="0997e-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="0997e-113">Pobiera token `TypeDef` metadanych dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="0997e-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0997e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0997e-114">Remarks</span></span>  
 <span data-ttu-id="0997e-115">`ICorDebugClass` Interfejs reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0997e-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="0997e-116">Interfejs ICorDebugType reprezentuje typ ogólny skonkretyzowany.</span><span class="sxs-lookup"><span data-stu-id="0997e-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="0997e-117">Na przykład `Hashtable<K, V>` byłyby reprezentowane przez `ICorDebugClass`, a `Hashtable<Int32, String>` byłyby reprezentowane przez `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="0997e-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="0997e-118">Typy inne niż ogólne są reprezentowane przez `ICorDebugClass` i. `ICorDebugType`</span><span class="sxs-lookup"><span data-stu-id="0997e-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="0997e-119">Ten ostatni interfejs został wprowadzony w .NET Framework w wersji 2,0, aby można było zająć się tworzeniem wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="0997e-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0997e-120">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="0997e-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0997e-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0997e-121">Requirements</span></span>  
 <span data-ttu-id="0997e-122">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0997e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0997e-123">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0997e-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0997e-124">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0997e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0997e-125">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0997e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0997e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0997e-126">See also</span></span>

- [<span data-ttu-id="0997e-127">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0997e-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
