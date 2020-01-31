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
ms.openlocfilehash: 7ac588591222a1abbc7b99ec7e973284c055f95e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784170"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="b68ca-102">ICorDebugClass, interfejs</span><span class="sxs-lookup"><span data-stu-id="b68ca-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="b68ca-103">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="b68ca-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="b68ca-104">Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="b68ca-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b68ca-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b68ca-105">Methods</span></span>  
  
|<span data-ttu-id="b68ca-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b68ca-106">Method</span></span>|<span data-ttu-id="b68ca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b68ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b68ca-108">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="b68ca-108">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="b68ca-109">Pobiera moduł, który definiuje tę klasę.</span><span class="sxs-lookup"><span data-stu-id="b68ca-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="b68ca-110">GetStaticFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="b68ca-110">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="b68ca-111">Pobiera wartość określonego pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="b68ca-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="b68ca-112">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="b68ca-112">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="b68ca-113">Pobiera `TypeDef` token metadanych dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="b68ca-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b68ca-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b68ca-114">Remarks</span></span>  
 <span data-ttu-id="b68ca-115">Interfejs `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="b68ca-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="b68ca-116">Interfejs ICorDebugType reprezentuje typ ogólny skonkretyzowany.</span><span class="sxs-lookup"><span data-stu-id="b68ca-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="b68ca-117">Na przykład `Hashtable<K, V>` byłaby reprezentowana przez `ICorDebugClass`, a `Hashtable<Int32, String>` będzie reprezentowane przez `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="b68ca-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="b68ca-118">Typy inne niż ogólne są reprezentowane przez `ICorDebugClass` i `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="b68ca-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="b68ca-119">Ten ostatni interfejs został wprowadzony w .NET Framework w wersji 2,0, aby można było zająć się tworzeniem wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="b68ca-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b68ca-120">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b68ca-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b68ca-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b68ca-121">Requirements</span></span>  
 <span data-ttu-id="b68ca-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b68ca-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b68ca-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b68ca-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b68ca-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b68ca-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b68ca-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b68ca-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68ca-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b68ca-126">See also</span></span>

- [<span data-ttu-id="b68ca-127">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b68ca-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
