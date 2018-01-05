---
title: ICorDebugType Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType
helpviewer_keywords: ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 503d0debef2ec1bebd674234051db8101dcb0de2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtype-interface1"></a><span data-ttu-id="23c43-102">ICorDebugType Interface1</span><span class="sxs-lookup"><span data-stu-id="23c43-102">ICorDebugType Interface1</span></span>
<span data-ttu-id="23c43-103">Reprezentuje typ, podstawowe lub złożonych (który jest zdefiniowane przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="23c43-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="23c43-104">Jeśli typ jest rodzajowy, `ICorDebugType` reprezentuje wystąpień typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="23c43-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23c43-105">Metody</span><span class="sxs-lookup"><span data-stu-id="23c43-105">Methods</span></span>  
  
|<span data-ttu-id="23c43-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="23c43-106">Method</span></span>|<span data-ttu-id="23c43-107">Opis</span><span class="sxs-lookup"><span data-stu-id="23c43-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23c43-108">EnumerateTypeParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="23c43-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="23c43-109">Pobiera wskaźnika interfejsu do ICorDebugTypeEnum, który odwołuje się do ogólnego <xref:System.Type> parametrów klasy odwołuje się to `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="23c43-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="23c43-110">GetBase, metoda</span><span class="sxs-lookup"><span data-stu-id="23c43-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="23c43-111">Pobiera wskaźnika interfejsu do `ICorDebugType` , która odwołuje się klasę podstawową klasy odwołuje się to `ICorDebugType`, jeśli taka istnieje.</span><span class="sxs-lookup"><span data-stu-id="23c43-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="23c43-112">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="23c43-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="23c43-113">Pobiera wskaźnika interfejsu do ICorDebugClass, który odwołuje się do konstruktora typu `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="23c43-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="23c43-114">GetFirstTypeParameter, metoda</span><span class="sxs-lookup"><span data-stu-id="23c43-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="23c43-115">Pobiera wskaźnika interfejsu do `ICorDebugType` , która odwołuje się pierwszy ogólny <xref:System.Type> parametr dla konstruktora klasy odwołuje się to `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="23c43-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="23c43-116">GetRank, metoda</span><span class="sxs-lookup"><span data-stu-id="23c43-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="23c43-117">Pobiera liczbę wymiarów w typie tablicy.</span><span class="sxs-lookup"><span data-stu-id="23c43-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="23c43-118">GetStaticFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="23c43-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="23c43-119">Pobiera token w ramce stosu określonego wskaźnika interfejsu do ICorDebugValue zawierający wartość pola statycznego odwołuje się określonego pola.</span><span class="sxs-lookup"><span data-stu-id="23c43-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="23c43-120">GetType, metoda</span><span class="sxs-lookup"><span data-stu-id="23c43-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="23c43-121">Pobiera wartość CorElementType, która opisuje typ macierzysty środowisko uruchomieniowe języka wspólnego <xref:System.Type> odwołuje się to `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="23c43-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23c43-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23c43-122">Remarks</span></span>  
 <span data-ttu-id="23c43-123">Jeśli typ jest rodzajowy, `ICorDebugClass` reprezentuje typ bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="23c43-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="23c43-124">`ICorDebugType` Interfejsu reprezentuje typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="23c43-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="23c43-125">Na przykład Hashtable\<K, V > może być reprezentowany przez `ICorDebugClass`, podczas gdy Hashtable\<Int32, String > może być reprezentowany przez `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="23c43-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="23c43-126">Typy ogólne nie są reprezentowane przez oba `ICorDebugClass` i `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="23c43-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="23c43-127">Drugim interfejs został wprowadzony w programie .NET Framework w wersji 2.0 na wypadek wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="23c43-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23c43-128">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="23c43-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23c43-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23c43-129">Requirements</span></span>  
 <span data-ttu-id="23c43-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23c43-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23c43-131">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23c43-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23c43-132">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23c43-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23c43-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23c43-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c43-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23c43-134">See Also</span></span>  
 [<span data-ttu-id="23c43-135">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="23c43-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
