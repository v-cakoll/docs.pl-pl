---
title: "ICorDebugClass2::GetParameterizedType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass2.GetParameterizedType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0df76f43ad037a4681f985e99401cb8c7f5a2ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="486dc-102">ICorDebugClass2::GetParameterizedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="486dc-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="486dc-103">Pobiera deklaracji typu dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="486dc-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="486dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="486dc-104">Syntax</span></span>  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="486dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="486dc-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="486dc-106">[in] Wartość wyliczenia CorElementType, która określa typ elementu dla tej klasy: Ustaw tę wartość na ELEMENT_TYPE_VALUETYPE, jeśli ta ICorDebugClass2 reprezentuje typ wartości.</span><span class="sxs-lookup"><span data-stu-id="486dc-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="486dc-107">Ustaw tę wartość po elemencie ELEMENT_TYPE_CLASS, jeśli `ICorDebugClass2` reprezentuje typ złożony.</span><span class="sxs-lookup"><span data-stu-id="486dc-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="486dc-108">[in] Liczba parametrów typu, jeśli typ jest rodzajowy.</span><span class="sxs-lookup"><span data-stu-id="486dc-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="486dc-109">Liczba parametrów typu (jeśli istnieją) muszą być zgodne numer wymagane przez klasę.</span><span class="sxs-lookup"><span data-stu-id="486dc-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="486dc-110">[in] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje parametr typu.</span><span class="sxs-lookup"><span data-stu-id="486dc-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="486dc-111">Jeśli klasa jest inny niż ogólny, ta wartość jest pusta.</span><span class="sxs-lookup"><span data-stu-id="486dc-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="486dc-112">[out] Wskaźnik do adresu `ICorDebugType` obiekt, który reprezentuje deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="486dc-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="486dc-113">Ten obiekt jest odpowiednikiem <xref:System.Type> obiektu w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="486dc-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="486dc-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="486dc-114">Remarks</span></span>  
 <span data-ttu-id="486dc-115">Jeśli klasa nie jest ogólna, oznacza to, jeśli go nie ma typu parametrów, `GetParameterizedType` po prostu pobiera obiekt typu środowiska uruchomieniowego odpowiadającą klasę.</span><span class="sxs-lookup"><span data-stu-id="486dc-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="486dc-116">`elementType` Parametr należy ustawić na typ elementu poprawne dla klasy: ELEMENT_TYPE_VALUETYPE, jeśli klasa jest typ wartości; w przeciwnym razie po elemencie ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="486dc-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="486dc-117">Jeśli klasa akceptuje parametrów typu (na przykład `ArrayList<T>`), można użyć `GetParameterizedType` do utworzenia obiektu typu dla typu, takich jak `ArrayList<int>`.</span><span class="sxs-lookup"><span data-stu-id="486dc-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="486dc-118">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="486dc-118">Background Information</span></span>  
 <span data-ttu-id="486dc-119">W wersji systemu .NET Framework 1.0 i 1.1 co typ w metadanych można bezpośrednio zmapowana do typu w uruchomionym procesem.</span><span class="sxs-lookup"><span data-stu-id="486dc-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="486dc-120">W związku z tym typem metadanych i typu środowiska uruchomieniowego miała pojedynczego reprezentacja w uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="486dc-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="486dc-121">Jednak jeden typ rodzajowy w metadanych mogą być mapowane na wiele różnych wystąpień typu uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="486dc-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="486dc-122">Na przykład typ metadanych `SortedList<K,V>` można mapować na `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="486dc-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="486dc-123">W związku z tym należy sposób obsługi podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="486dc-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="486dc-124">.NET Framework w wersji 2.0 wprowadzono `ICorDebugType` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="486dc-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="486dc-125">Dla typu ogólnego `ICorDebugClass` lub `ICorDebugClass2` obiekt reprezentuje typ bez wystąpień (`SortedList<K,V>`), a `ICorDebugType` obiektu przedstawia różne typy skonkretyzowanym.</span><span class="sxs-lookup"><span data-stu-id="486dc-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="486dc-126">Podane `ICorDebugClass` lub `ICorDebugClass2` obiektu, można utworzyć `ICorDebugType` obiekt do dowolnego wystąpienia przez wywołanie metody `ICorDebugClass2::GetParameterizedType` metody.</span><span class="sxs-lookup"><span data-stu-id="486dc-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="486dc-127">Można również utworzyć `ICorDebugType` obiektu typu prostego, takie jak Int32, lub dla typu nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="486dc-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="486dc-128">Wprowadzenie `ICorDebugType` obiekt do reprezentowania wykonawcze pojęcie typu ma wpływ w interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="486dc-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="486dc-129">Funkcje, które wcześniej miały `ICorDebugClass` lub `ICorDebugClass2` obiektu, a nawet `CorElementType` wartości zostały uogólnione podjęcie `ICorDebugType` obiektu.</span><span class="sxs-lookup"><span data-stu-id="486dc-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="486dc-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="486dc-130">Requirements</span></span>  
 <span data-ttu-id="486dc-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="486dc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="486dc-132">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="486dc-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="486dc-133">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="486dc-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="486dc-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="486dc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
