---
title: ICorDebugType — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e3d1173ac6fb14a380cdbc99882fd9baee6552a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966037"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="14912-102">ICorDebugType — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14912-102">ICorDebugType Interface</span></span>
<span data-ttu-id="14912-103">Reprezentuje typ podstawowy lub złożony (zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="14912-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="14912-104">Jeśli typ ogólny, `ICorDebugType` reprezentuje typ ogólny z wystąpieniami.</span><span class="sxs-lookup"><span data-stu-id="14912-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14912-105">Metody</span><span class="sxs-lookup"><span data-stu-id="14912-105">Methods</span></span>  
  
|<span data-ttu-id="14912-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="14912-106">Method</span></span>|<span data-ttu-id="14912-107">Opis</span><span class="sxs-lookup"><span data-stu-id="14912-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14912-108">EnumerateTypeParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="14912-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="14912-109">Pobiera wskaźnik interfejsu do icordebugtypeenum —, który odwołuje się do ogólnego <xref:System.Type> parametrów klasy przywoływane przez to `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="14912-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="14912-110">GetBase, metoda</span><span class="sxs-lookup"><span data-stu-id="14912-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="14912-111">Pobiera wskaźnik interfejsu do `ICorDebugType` odwołujący się klasę bazową klasy przywoływane przez to `ICorDebugType`, jeśli taka istnieje.</span><span class="sxs-lookup"><span data-stu-id="14912-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="14912-112">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="14912-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="14912-113">Pobiera wskaźnik interfejsu do ICorDebugClass, który odwołuje się do konstruktora wpisane `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="14912-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="14912-114">GetFirstTypeParameter, metoda</span><span class="sxs-lookup"><span data-stu-id="14912-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="14912-115">Pobiera wskaźnik interfejsu do `ICorDebugType` odwołujący się pierwszy ogólny <xref:System.Type> parametr dla konstruktora klasy przywoływane przez to `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="14912-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="14912-116">GetRank, metoda</span><span class="sxs-lookup"><span data-stu-id="14912-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="14912-117">Pobiera liczbę wymiarów typu tablicowego.</span><span class="sxs-lookup"><span data-stu-id="14912-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="14912-118">GetStaticFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="14912-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="14912-119">Pobiera token w ramce stosu określony wskaźnik interfejsu do ICorDebugValue, który zawiera wartość pola statycznego odwołuje się określone pole.</span><span class="sxs-lookup"><span data-stu-id="14912-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="14912-120">GetType, metoda</span><span class="sxs-lookup"><span data-stu-id="14912-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="14912-121">Pobiera wartość corelementtype —, która opisuje typ macierzysty środowiska uruchomieniowego języka wspólnego <xref:System.Type> przywoływane przez to `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="14912-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14912-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14912-122">Remarks</span></span>  
 <span data-ttu-id="14912-123">Jeśli typ ogólny, `ICorDebugClass` reprezentuje typ bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="14912-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="14912-124">`ICorDebugType` Interfejs reprezentuje typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="14912-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="14912-125">Na przykład tablica skrótów\<K, V > jest przedstawiany przez `ICorDebugClass`, podczas gdy tabela skrótów\<Int32, String > jest przedstawiany przez `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="14912-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="14912-126">Typy nieuniwersalne są reprezentowane przez oba `ICorDebugClass` i `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="14912-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="14912-127">Ostatnie interfejsu została wprowadzona w .NET Framework w wersji 2.0 radzenia sobie z podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="14912-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14912-128">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="14912-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14912-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14912-129">Requirements</span></span>  
 <span data-ttu-id="14912-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14912-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14912-131">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14912-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14912-132">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14912-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14912-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14912-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14912-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14912-134">See also</span></span>
- [<span data-ttu-id="14912-135">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="14912-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
