---
title: ICorDebugClass Interface1
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
ms.openlocfilehash: d12d952fe540b2ec36d058ae2100f0cf5c8e6bcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710230"
---
# <a name="icordebugclass-interface1"></a><span data-ttu-id="e6901-102">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="e6901-102">ICorDebugClass Interface1</span></span>
<span data-ttu-id="e6901-103">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="e6901-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="e6901-104">Jeśli typ ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e6901-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6901-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e6901-105">Methods</span></span>  
  
|<span data-ttu-id="e6901-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e6901-106">Method</span></span>|<span data-ttu-id="e6901-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e6901-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6901-108">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="e6901-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="e6901-109">Pobiera moduł, który definiuje tę klasę.</span><span class="sxs-lookup"><span data-stu-id="e6901-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="e6901-110">GetStaticFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="e6901-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="e6901-111">Pobiera wartość określonego pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="e6901-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="e6901-112">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="e6901-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="e6901-113">Pobiera `TypeDef` token metadanych dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="e6901-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6901-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6901-114">Remarks</span></span>  
 <span data-ttu-id="e6901-115">`ICorDebugClass` Interfejs reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e6901-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="e6901-116">Icordebugtype — interfejs reprezentuje typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="e6901-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="e6901-117">Na przykład `Hashtable<K, V>` jest przedstawiany przez `ICorDebugClass`, podczas gdy `Hashtable<Int32, String>` jest przedstawiany przez `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e6901-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="e6901-118">Typy nieuniwersalne są reprezentowane przez oba `ICorDebugClass` i `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e6901-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="e6901-119">Ostatnie interfejsu została wprowadzona w .NET Framework w wersji 2.0 radzenia sobie z podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="e6901-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6901-120">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="e6901-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6901-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e6901-121">Requirements</span></span>  
 <span data-ttu-id="e6901-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6901-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6901-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6901-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6901-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6901-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6901-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6901-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6901-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6901-126">See also</span></span>
- [<span data-ttu-id="e6901-127">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e6901-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
