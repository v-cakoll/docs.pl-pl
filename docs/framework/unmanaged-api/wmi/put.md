---
title: "Funkcja Put (niezarządzany wykaz interfejsów API)"
description: "Funkcja Put przypisuje nową wartość do nazwanej właściwości."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Put
helpviewer_keywords: Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09d3edc74b34688d5cc36e688f634850cfb60910
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="put-function"></a><span data-ttu-id="91f78-103">Put — funkcja</span><span class="sxs-lookup"><span data-stu-id="91f78-103">Put function</span></span>
<span data-ttu-id="91f78-104">Ustawia właściwość o nazwie na nową wartość.</span><span class="sxs-lookup"><span data-stu-id="91f78-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="91f78-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="91f78-105">Syntax</span></span>  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a><span data-ttu-id="91f78-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="91f78-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="91f78-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="91f78-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="91f78-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="91f78-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="91f78-109">[in] Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="91f78-109">[in] The name of the property.</span></span> <span data-ttu-id="91f78-110">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="91f78-110">This parameter cannot be `null`.</span></span>

`lFlags`  
<span data-ttu-id="91f78-111">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="91f78-111">[in] Reserved.</span></span> <span data-ttu-id="91f78-112">Ten parametr musi wynosić 0.</span><span class="sxs-lookup"><span data-stu-id="91f78-112">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="91f78-113">[in] Wskaźnik do prawidłowej `VARIANT` jako nowa wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="91f78-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="91f78-114">Jeśli `pVal` jest `null` lub wskazuje `VARIANT` typu `VT_NULL`, ma ustawioną właściwość `null`.</span><span class="sxs-lookup"><span data-stu-id="91f78-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span> 

`vtType`  
<span data-ttu-id="91f78-115">[in] Typ `VARIANT` wskazywana przez `pVal`.</span><span class="sxs-lookup"><span data-stu-id="91f78-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="91f78-116">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="91f78-116">See the [Remarks](#remarks) section for more information.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="91f78-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="91f78-117">Return value</span></span>

<span data-ttu-id="91f78-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="91f78-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="91f78-119">Stała</span><span class="sxs-lookup"><span data-stu-id="91f78-119">Constant</span></span>  |<span data-ttu-id="91f78-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="91f78-120">Value</span></span>  |<span data-ttu-id="91f78-121">Opis</span><span class="sxs-lookup"><span data-stu-id="91f78-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="91f78-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="91f78-122">0x80041001</span></span> | <span data-ttu-id="91f78-123">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="91f78-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="91f78-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="91f78-124">0x80041008</span></span> | <span data-ttu-id="91f78-125">Jeden lub więcej parametrów nie są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="91f78-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="91f78-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="91f78-126">0x8004102a</span></span> | <span data-ttu-id="91f78-127">Nie rozpoznano typu właściwości.</span><span class="sxs-lookup"><span data-stu-id="91f78-127">The property type is not recognized.</span></span> <span data-ttu-id="91f78-128">Ta wartość jest zwracana w trakcie tworzenia wystąpień klasy, jeśli klasa już istnieje.</span><span class="sxs-lookup"><span data-stu-id="91f78-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="91f78-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="91f78-129">0x80041006</span></span> | <span data-ttu-id="91f78-130">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="91f78-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="91f78-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="91f78-131">0x80041005</span></span> | <span data-ttu-id="91f78-132">Dla wystąpień: wskazuje, że `pVal` wskazuje `VARIANT` niepoprawnego typu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="91f78-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="91f78-133">Dla definicji klasy: właściwość już istnieje w klasie nadrzędnej, a nowy typ COM różni się od starego typu COM.</span><span class="sxs-lookup"><span data-stu-id="91f78-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="91f78-134">0</span><span class="sxs-lookup"><span data-stu-id="91f78-134">0</span></span> | <span data-ttu-id="91f78-135">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="91f78-135">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="91f78-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91f78-136">Remarks</span></span>

<span data-ttu-id="91f78-137">Ta funkcja jest zawijana wywołanie [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="91f78-137">This function wraps a call to the [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="91f78-138">Ta funkcja zastępuje zawsze bieżącą wartość właściwości nowej.</span><span class="sxs-lookup"><span data-stu-id="91f78-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="91f78-139">Jeśli [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wskazuje definicję klasy `Put` tworzy lub aktualizuje wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="91f78-139">If the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="91f78-140">Gdy [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wskazuje na wystąpienie CIM, `Put` aktualizacji wartości właściwości. `Put` nie można utworzyć wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="91f78-140">When [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="91f78-141">`__CLASS` Systemu właściwość jest tylko zapisu podczas tworzenia klasy, jeśli go nie może pozostać puste.</span><span class="sxs-lookup"><span data-stu-id="91f78-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="91f78-142">Wszystkie inne właściwości systemu są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="91f78-142">All other system properties are read-only.</span></span>

<span data-ttu-id="91f78-143">Użytkownik nie można utworzyć właściwości o nazwach rozpoczynać się ani kończyć znakiem podkreślenia ("_").</span><span class="sxs-lookup"><span data-stu-id="91f78-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="91f78-144">Jest to zarezerwowana dla systemu klas i właściwości.</span><span class="sxs-lookup"><span data-stu-id="91f78-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="91f78-145">Jeśli właściwość jest ustawiona `Put` funkcja istnieje w klasie nadrzędnej, wartością domyślną właściwości zostanie zmieniona, chyba że typ właściwości nie jest zgodny z typem klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="91f78-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="91f78-146">Jeśli właściwość nie istnieje i nie jest niezgodność typów, właściwość jest ceated.</span><span class="sxs-lookup"><span data-stu-id="91f78-146">If the property does not exist and it is not a type mismatch, the property is ceated.</span></span>

<span data-ttu-id="91f78-147">Użyj `vtType` parametru tylko podczas tworzenia nowych właściwości w definicji klasy modelu wspólnych informacji i `pVal` jest `null` lub wskazuje `VARIANT` typu `VT_NULL`.</span><span class="sxs-lookup"><span data-stu-id="91f78-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="91f78-148">W takim przypadku `vType` parametr określa typ CIM właściwości.</span><span class="sxs-lookup"><span data-stu-id="91f78-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="91f78-149">W każdym przypadku `vtType` musi być równa 0.</span><span class="sxs-lookup"><span data-stu-id="91f78-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="91f78-150">`vtType`również musi wynosić 0, jeśli obiekt jest wystąpieniem (nawet jeśli `Val` jest `null`), ponieważ typ właściwości jest stała i nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="91f78-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>   

## <a name="example"></a><span data-ttu-id="91f78-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="91f78-151">Example</span></span>

<span data-ttu-id="91f78-152">Na przykład zobacz [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="91f78-152">For an example, see the [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="91f78-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91f78-153">Requirements</span></span>  
 <span data-ttu-id="91f78-154">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91f78-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91f78-155">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="91f78-155">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="91f78-156">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="91f78-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f78-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91f78-157">See also</span></span>  
[<span data-ttu-id="91f78-158">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="91f78-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
