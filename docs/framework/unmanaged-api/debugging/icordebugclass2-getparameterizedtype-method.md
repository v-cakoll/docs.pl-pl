---
title: ICorDebugClass2::GetParameterizedType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e1734ca91fd48cc15b8dbf25f11518ed0455b6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475644"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="1f138-102">ICorDebugClass2::GetParameterizedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f138-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="1f138-103">Pobiera deklaracji typu dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="1f138-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f138-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f138-104">Syntax</span></span>  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f138-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f138-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="1f138-106">[in] Wartość corelementtype — wyliczenie, który określa typ elementu dla tej klasy: Ta wartość ELEMENT_TYPE_VALUETYPE Jeśli ta icordebugclass2 — reprezentuje typ wartości.</span><span class="sxs-lookup"><span data-stu-id="1f138-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="1f138-107">Ustaw tę wartość na ELEMENT_TYPE_CLASS, jeśli `ICorDebugClass2` reprezentuje typ złożony.</span><span class="sxs-lookup"><span data-stu-id="1f138-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="1f138-108">[in] Liczba parametrów typu, w przypadku typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="1f138-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="1f138-109">Liczba parametrów typu (jeśli istnieje) musi być zgodna liczbę wymaganych przez klasę.</span><span class="sxs-lookup"><span data-stu-id="1f138-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="1f138-110">[in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugType, który reprezentuje parametr typu.</span><span class="sxs-lookup"><span data-stu-id="1f138-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="1f138-111">Jeśli klasa jest nieogólnego, ta wartość ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="1f138-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="1f138-112">[out] Wskaźnik na adres `ICorDebugType` obiekt, który reprezentuje deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="1f138-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="1f138-113">Ten obiekt jest odpowiednikiem <xref:System.Type> obiektu w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="1f138-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f138-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f138-114">Remarks</span></span>  
 <span data-ttu-id="1f138-115">Jeśli klasa nieogólnego, oznacza to, jeśli go nie ma parametrów typu, `GetParameterizedType` po prostu pobiera obiekt typu środowiska uruchomieniowego, odpowiadający tej klasy.</span><span class="sxs-lookup"><span data-stu-id="1f138-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="1f138-116">`elementType` Parametr powinien być ustawiony na typ elementu poprawne dla klasy: ELEMENT_TYPE_VALUETYPE, jeśli klasa jest typem wartości w przeciwnym razie ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="1f138-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="1f138-117">Jeśli klasa akceptuje parametry typu (na przykład `ArrayList<T>`), możesz użyć `GetParameterizedType` do konstruowania na obiekt typu dla typu wystąpień, takie jak `ArrayList<int>`.</span><span class="sxs-lookup"><span data-stu-id="1f138-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="1f138-118">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="1f138-118">Background Information</span></span>  
 <span data-ttu-id="1f138-119">W wersjach programu .NET Framework 1.0 i 1.1 Każdy typ w metadanych może być bezpośrednio zmapowana do typu w uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="1f138-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="1f138-120">W związku z tym typ metadanych i typ środowiska uruchomieniowego w kończyły się jednym reprezentacji uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="1f138-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="1f138-121">Jednak pierwszego typu ogólnego w metadanych można mapować do wielu inne realizacje typu w uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="1f138-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="1f138-122">Na przykład typ metadanych `SortedList<K,V>` można mapować na `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="1f138-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="1f138-123">Dlatego należy sposób obsługi podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="1f138-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="1f138-124">.NET Framework w wersji 2.0 wprowadzono `ICorDebugType` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1f138-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="1f138-125">Dla typu ogólnego `ICorDebugClass` lub `ICorDebugClass2` obiekt reprezentuje typ bez wystąpień (`SortedList<K,V>`), a `ICorDebugType` obiekt reprezentuje różne typy wystąpień.</span><span class="sxs-lookup"><span data-stu-id="1f138-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="1f138-126">Biorąc pod uwagę `ICorDebugClass` lub `ICorDebugClass2` obiektu, można utworzyć `ICorDebugType` obiektów dla dowolnego wystąpienia przez wywołanie metody `ICorDebugClass2::GetParameterizedType` metody.</span><span class="sxs-lookup"><span data-stu-id="1f138-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="1f138-127">Można również utworzyć `ICorDebugType` obiektu dla typu prostego, takie jak Int32, lub dla typu nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="1f138-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="1f138-128">Wprowadzenie `ICorDebugType` obiekt do reprezentowania pojęcie środowiska wykonawczego typu ma falę w interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="1f138-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="1f138-129">Funkcje, które poprzednio miały `ICorDebugClass` lub `ICorDebugClass2` obiektu, a nawet `CorElementType` wartości zostały uogólnione podjęcie `ICorDebugType` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f138-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f138-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f138-130">Requirements</span></span>  
 <span data-ttu-id="1f138-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f138-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f138-132">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f138-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f138-133">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f138-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f138-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f138-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
