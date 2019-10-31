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
ms.openlocfilehash: 4f3f553ed5dc93433610365e0dae5bee54863de5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129629"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="60c3f-102">ICorDebugType — Interfejs</span><span class="sxs-lookup"><span data-stu-id="60c3f-102">ICorDebugType Interface</span></span>
<span data-ttu-id="60c3f-103">Reprezentuje typ, podstawowy lub złożony (to jest zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="60c3f-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="60c3f-104">Jeśli typ jest ogólny, `ICorDebugType` reprezentuje typ ogólny wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="60c3f-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60c3f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="60c3f-105">Methods</span></span>  
  
|<span data-ttu-id="60c3f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="60c3f-106">Method</span></span>|<span data-ttu-id="60c3f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="60c3f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60c3f-108">EnumerateTypeParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="60c3f-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="60c3f-109">Pobiera wskaźnik interfejsu do ICorDebugTypeEnum, który odwołuje się do generycznych parametrów <xref:System.Type> klasy, do których odwołuje się ten `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="60c3f-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="60c3f-110">GetBase, metoda</span><span class="sxs-lookup"><span data-stu-id="60c3f-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="60c3f-111">Pobiera wskaźnik interfejsu do `ICorDebugType`, który odwołuje się do klasy bazowej klasy, do której odwołuje się ten `ICorDebugType`(jeśli taki istnieje).</span><span class="sxs-lookup"><span data-stu-id="60c3f-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="60c3f-112">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="60c3f-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="60c3f-113">Pobiera wskaźnik interfejsu do elementu ICorDebugClass, który odwołuje się do określonego konstruktora tego `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="60c3f-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="60c3f-114">GetFirstTypeParameter, metoda</span><span class="sxs-lookup"><span data-stu-id="60c3f-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="60c3f-115">Pobiera wskaźnik interfejsu do `ICorDebugType`, który odwołuje się do pierwszego generycznego parametru <xref:System.Type> dla konstruktora klasy, do której odwołuje się ten `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="60c3f-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="60c3f-116">GetRank, metoda</span><span class="sxs-lookup"><span data-stu-id="60c3f-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="60c3f-117">Pobiera liczbę wymiarów w typie tablicy.</span><span class="sxs-lookup"><span data-stu-id="60c3f-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="60c3f-118">GetStaticFieldValue, metoda</span><span class="sxs-lookup"><span data-stu-id="60c3f-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="60c3f-119">Pobiera wskaźnik interfejsu do ICorDebugValue, który zawiera wartość pola statycznego, do którego odwołuje się określony token pola w określonej ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="60c3f-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="60c3f-120">GetType, metoda</span><span class="sxs-lookup"><span data-stu-id="60c3f-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="60c3f-121">Pobiera wartość CorElementType —, która opisuje natywny typ środowiska <xref:System.Type> uruchomieniowego języka wspólnego, do którego odwołuje się ten `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="60c3f-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60c3f-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60c3f-122">Remarks</span></span>  
 <span data-ttu-id="60c3f-123">Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ nieskonkretyzowany.</span><span class="sxs-lookup"><span data-stu-id="60c3f-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="60c3f-124">Interfejs `ICorDebugType` reprezentuje typ ogólny skonkretyzowany.</span><span class="sxs-lookup"><span data-stu-id="60c3f-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="60c3f-125">Na przykład, Hashtable\<K, V > byłaby reprezentowana przez `ICorDebugClass`, natomiast obiekt Hashtable\<Int32, ciąg > będzie reprezentowany przez `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="60c3f-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="60c3f-126">Typy inne niż ogólne są reprezentowane przez `ICorDebugClass` i `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="60c3f-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="60c3f-127">Ten ostatni interfejs został wprowadzony w .NET Framework w wersji 2,0, aby można było zająć się tworzeniem wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="60c3f-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60c3f-128">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="60c3f-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60c3f-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60c3f-129">Requirements</span></span>  
 <span data-ttu-id="60c3f-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60c3f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60c3f-131">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="60c3f-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60c3f-132">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="60c3f-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60c3f-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60c3f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c3f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60c3f-134">See also</span></span>

- [<span data-ttu-id="60c3f-135">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="60c3f-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
