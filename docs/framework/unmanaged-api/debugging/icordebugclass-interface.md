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
ms.openlocfilehash: 7e1ad830e728fbe764085a5808a48e4cacedc595
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133630"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="ad4d4-102">ICorDebugClass, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad4d4-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="ad4d4-103">Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="ad4d4-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="ad4d4-104">Jeśli typ ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad4d4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ad4d4-105">Methods</span></span>  
  
|<span data-ttu-id="ad4d4-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ad4d4-106">Method</span></span>|<span data-ttu-id="ad4d4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ad4d4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad4d4-108">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="ad4d4-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="ad4d4-109">Pobiera moduł, który definiuje tę klasę.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="ad4d4-110">GetStaticFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="ad4d4-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="ad4d4-111">Pobiera wartość określonego pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="ad4d4-112">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="ad4d4-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="ad4d4-113">Pobiera `TypeDef` token metadanych dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad4d4-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad4d4-114">Remarks</span></span>  
 <span data-ttu-id="ad4d4-115">`ICorDebugClass` Interfejs reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="ad4d4-116">Icordebugtype — interfejs reprezentuje typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="ad4d4-117">Na przykład `Hashtable<K, V>` jest przedstawiany przez `ICorDebugClass`, podczas gdy `Hashtable<Int32, String>` jest przedstawiany przez `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="ad4d4-118">Typy nieuniwersalne są reprezentowane przez oba `ICorDebugClass` i `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="ad4d4-119">Ostatnie interfejsu została wprowadzona w .NET Framework w wersji 2.0 radzenia sobie z podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad4d4-120">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad4d4-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad4d4-121">Requirements</span></span>  
 <span data-ttu-id="ad4d4-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad4d4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad4d4-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad4d4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad4d4-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad4d4-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ad4d4-125">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ad4d4-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad4d4-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad4d4-126">See also</span></span>

- [<span data-ttu-id="ad4d4-127">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ad4d4-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
