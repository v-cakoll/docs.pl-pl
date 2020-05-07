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
ms.openlocfilehash: 329bcee441b395982a8a8b539c0a938fa8170b14
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894056"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="f252f-102">ICorDebugClass2::GetParameterizedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="f252f-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="f252f-103">Pobiera deklarację typu dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f252f-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f252f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f252f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f252f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f252f-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="f252f-106">podczas Wartość wyliczenia CorElementType —, która określa typ elementu dla tej klasy: Ustaw tę wartość na ELEMENT_TYPE_VALUETYPE, jeśli ten ICorDebugClass2 reprezentuje typ wartości.</span><span class="sxs-lookup"><span data-stu-id="f252f-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="f252f-107">Ustaw tę wartość na ELEMENT_TYPE_CLASS, jeśli `ICorDebugClass2` reprezentuje typ złożony.</span><span class="sxs-lookup"><span data-stu-id="f252f-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="f252f-108">podczas Liczba parametrów typu, jeśli typ jest ogólny.</span><span class="sxs-lookup"><span data-stu-id="f252f-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="f252f-109">Liczba parametrów typu (jeśli istnieją) musi być zgodna z liczbą wymaganą przez klasę.</span><span class="sxs-lookup"><span data-stu-id="f252f-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="f252f-110">podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugType reprezentujący parametr typu.</span><span class="sxs-lookup"><span data-stu-id="f252f-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="f252f-111">Jeśli Klasa nie jest ogólna, ta wartość jest równa null.</span><span class="sxs-lookup"><span data-stu-id="f252f-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="f252f-112">określoną Wskaźnik do adresu `ICorDebugType` obiektu, który reprezentuje deklarację typu.</span><span class="sxs-lookup"><span data-stu-id="f252f-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="f252f-113">Ten obiekt jest równoważny <xref:System.Type> obiektowi w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="f252f-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f252f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f252f-114">Remarks</span></span>  
 <span data-ttu-id="f252f-115">Jeśli klasa jest nieogólna, to oznacza, że jeśli nie ma parametrów typu, `GetParameterizedType` po prostu pobiera obiekt typu środowiska uruchomieniowego odpowiadający klasie.</span><span class="sxs-lookup"><span data-stu-id="f252f-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="f252f-116">`elementType` Parametr powinien być ustawiony na prawidłowy typ elementu dla klasy: ELEMENT_TYPE_VALUETYPE, jeśli klasa jest typem wartości; w przeciwnym razie ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="f252f-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="f252f-117">Jeśli Klasa akceptuje parametry typu (na przykład `ArrayList<T>`), można użyć `GetParameterizedType` do konstruowania obiektu typu dla wystąpienia typu, takiego jak. `ArrayList<int>`</span><span class="sxs-lookup"><span data-stu-id="f252f-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="f252f-118">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="f252f-118">Background Information</span></span>  
 <span data-ttu-id="f252f-119">W .NET Framework wersje 1,0 i 1,1 Każdy typ w metadanych może być bezpośrednio zamapowany na typ w uruchomionym procesie.</span><span class="sxs-lookup"><span data-stu-id="f252f-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="f252f-120">W ten sposób typ metadanych i typ środowiska uruchomieniowego miały jedną reprezentację w uruchomionym procesie.</span><span class="sxs-lookup"><span data-stu-id="f252f-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="f252f-121">Jednak jeden typ ogólny w metadanych można zamapować na wiele różnych wystąpień typu w uruchomionym procesie.</span><span class="sxs-lookup"><span data-stu-id="f252f-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="f252f-122">`SortedList<K,V>` Na przykład typ metadanych może być mapowany `SortedList<String, EmployeeRecord>`na, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="f252f-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="f252f-123">W tym celu musisz mieć możliwość obsługi tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="f252f-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="f252f-124">W .NET Framework w wersji 2,0 wprowadzono `ICorDebugType` interfejs.</span><span class="sxs-lookup"><span data-stu-id="f252f-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="f252f-125">W przypadku typu ogólnego `ICorDebugClass` obiekt lub `ICorDebugClass2` reprezentuje typ nieskonkretyzowany (`SortedList<K,V>`), a `ICorDebugType` obiekt reprezentuje różne typy wystąpień.</span><span class="sxs-lookup"><span data-stu-id="f252f-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="f252f-126">Mając obiekt `ICorDebugClass` lub `ICorDebugClass2` , można utworzyć `ICorDebugType` obiekt dla dowolnego wystąpienia, wywołując `ICorDebugClass2::GetParameterizedType` metodę.</span><span class="sxs-lookup"><span data-stu-id="f252f-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="f252f-127">Można również utworzyć `ICorDebugType` obiekt dla typu prostego, takiego jak Int32 lub dla typu innego niż ogólny.</span><span class="sxs-lookup"><span data-stu-id="f252f-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="f252f-128">Wprowadzenie `ICorDebugType` obiektu do reprezentowania koncepcji czasu wykonywania typu ma wpływ na działanie narzędzia Ripple w całym interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="f252f-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="f252f-129">Funkcje, `ICorDebugClass` które wcześniej brały `ICorDebugClass2` obiekt lub, a `CorElementType` nawet wartość, są uogólnione w `ICorDebugType` celu wykonania obiektu.</span><span class="sxs-lookup"><span data-stu-id="f252f-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f252f-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f252f-130">Requirements</span></span>  
 <span data-ttu-id="f252f-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f252f-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f252f-132">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f252f-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f252f-133">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f252f-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f252f-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f252f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
