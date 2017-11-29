---
title: "GetNames — funkcja (niezarządzany wykaz interfejsów API)"
description: "Funkcja GetNames pobiera nazwy właściwości obiektu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetNames
helpviewer_keywords: GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2ba2530dd43e6924187c80214d5efa13ebc548de
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="getnames-function"></a><span data-ttu-id="51310-103">GetNames — funkcja</span><span class="sxs-lookup"><span data-stu-id="51310-103">GetNames function</span></span>
<span data-ttu-id="51310-104">Pobiera podzbiór lub wszystkie nazwy właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="51310-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="51310-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="51310-105">Syntax</span></span>  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="51310-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="51310-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="51310-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="51310-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="51310-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="51310-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="51310-109">[in] Wskaźnik do prawidłowej `LPCWSTR` określający nazwę kwalifikator, który działa jako część filtru.</span><span class="sxs-lookup"><span data-stu-id="51310-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="51310-110">Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.</span><span class="sxs-lookup"><span data-stu-id="51310-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="51310-111">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="51310-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="51310-112">[in] Kombinacja pól bitowych.</span><span class="sxs-lookup"><span data-stu-id="51310-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="51310-113">Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.</span><span class="sxs-lookup"><span data-stu-id="51310-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="51310-114">[in] Wskaźnik do prawidłowej `VARIANT` struktury zainicjowany do wartości filtru.</span><span class="sxs-lookup"><span data-stu-id="51310-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="51310-115">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="51310-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="51310-116">[out] A `SAFEARRAY` struktury, która zawiera nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="51310-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="51310-117">Na pozycji tego parametru zawsze musi być wskaźnikiem do `null`.</span><span class="sxs-lookup"><span data-stu-id="51310-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="51310-118">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="51310-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="51310-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="51310-119">Return value</span></span>

<span data-ttu-id="51310-120">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="51310-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="51310-121">Stała</span><span class="sxs-lookup"><span data-stu-id="51310-121">Constant</span></span>  |<span data-ttu-id="51310-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="51310-122">Value</span></span>  |<span data-ttu-id="51310-123">Opis</span><span class="sxs-lookup"><span data-stu-id="51310-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="51310-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="51310-124">0x80041001</span></span> | <span data-ttu-id="51310-125">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="51310-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="51310-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="51310-126">0x80041008</span></span> | <span data-ttu-id="51310-127">Jeden lub więcej parametrów nie są prawidłowe, lub określono niepoprawne kombinacją flag i parametry.</span><span class="sxs-lookup"><span data-stu-id="51310-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="51310-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="51310-128">0x80041006</span></span> | <span data-ttu-id="51310-129">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="51310-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="51310-130">0</span><span class="sxs-lookup"><span data-stu-id="51310-130">0</span></span> | <span data-ttu-id="51310-131">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="51310-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="51310-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51310-132">Remarks</span></span>

<span data-ttu-id="51310-133">Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="51310-133">This function wraps a call to the [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="51310-134">Nazwane zwracane są kontrolowane przez kombinacją flag i parametry.</span><span class="sxs-lookup"><span data-stu-id="51310-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="51310-135">Na przykład funkcja może zwracać wszystkie właściwości lub tylko nazwy właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="51310-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="51310-136">Filtr główny jest określona w `lFlags` parametr i inne parametry różnią się w zależności od jej.</span><span class="sxs-lookup"><span data-stu-id="51310-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="51310-137">Wartości flagi `lFlags` są pola bitowe</span><span class="sxs-lookup"><span data-stu-id="51310-137">The flag values in `lFlags` are bit fields</span></span>


<span data-ttu-id="51310-138">Flagi, które mogą być przekazywane jako `lEnumFlags` argumentu są pola bitowe, które są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="51310-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="51310-139">Możesz łączyć jedną flagę z każdej grupy z flagą dowolnego z innej grupy.</span><span class="sxs-lookup"><span data-stu-id="51310-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="51310-140">Jednak flagi z tej samej grupy wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="51310-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="51310-141">Flagi grupy 1</span><span class="sxs-lookup"><span data-stu-id="51310-141">Group 1 flags</span></span> |<span data-ttu-id="51310-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="51310-142">Value</span></span>  |<span data-ttu-id="51310-143">Opis</span><span class="sxs-lookup"><span data-stu-id="51310-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="51310-144">0</span><span class="sxs-lookup"><span data-stu-id="51310-144">0</span></span> | <span data-ttu-id="51310-145">Zwróć wszystkie nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="51310-145">Return all property names.</span></span> <span data-ttu-id="51310-146">`strQualifierName`i `pQualifierVal` są używane.</span><span class="sxs-lookup"><span data-stu-id="51310-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="51310-147">1</span><span class="sxs-lookup"><span data-stu-id="51310-147">1</span></span> | <span data-ttu-id="51310-148">Zwróć tylko właściwości, które mają Kwalifikator nazwy podanej przez `strQualifierName` parametru.</span><span class="sxs-lookup"><span data-stu-id="51310-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="51310-149">Jeśli ta flaga jest wykorzystywana, należy określić `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="51310-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="51310-150">2</span><span class="sxs-lookup"><span data-stu-id="51310-150">2</span></span> |  <span data-ttu-id="51310-151">Zwróć tylko właściwości, które nie mają Kwalifikator nazwy podanej przez `strQualifierName` parametru.</span><span class="sxs-lookup"><span data-stu-id="51310-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="51310-152">Jeśli ta flaga jest wykorzystywana, należy określić `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="51310-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="51310-153">3</span><span class="sxs-lookup"><span data-stu-id="51310-153">3</span></span> | <span data-ttu-id="51310-154">Zwraca tylko te właściwości, które mają Kwalifikator nazwy podanej przez `wszQualifierName` parametr i wartość jest taka sama jak określona przez `pQualifierVal` struktury.</span><span class="sxs-lookup"><span data-stu-id="51310-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="51310-155">Jeśli ta flaga jest wykorzystywana, należy określić zarówno `wszQualifierName` i `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="51310-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="51310-156">Flagi grupy 2</span><span class="sxs-lookup"><span data-stu-id="51310-156">Group 2 flags</span></span> |<span data-ttu-id="51310-157">Wartość</span><span class="sxs-lookup"><span data-stu-id="51310-157">Value</span></span>  |<span data-ttu-id="51310-158">Opis</span><span class="sxs-lookup"><span data-stu-id="51310-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="51310-159">0x4</span><span class="sxs-lookup"><span data-stu-id="51310-159">0x4</span></span> | <span data-ttu-id="51310-160">Zwraca tylko nazwy właściwości, które definiują kluczy.</span><span class="sxs-lookup"><span data-stu-id="51310-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="51310-161">0x8</span><span class="sxs-lookup"><span data-stu-id="51310-161">0x8</span></span> | <span data-ttu-id="51310-162">Zwracane tylko nazwy właściwości, które są odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="51310-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="51310-163">Flagi grupa 3</span><span class="sxs-lookup"><span data-stu-id="51310-163">Group 3 flags</span></span> |<span data-ttu-id="51310-164">Wartość</span><span class="sxs-lookup"><span data-stu-id="51310-164">Value</span></span>  |<span data-ttu-id="51310-165">Opis</span><span class="sxs-lookup"><span data-stu-id="51310-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="51310-166">0x10</span><span class="sxs-lookup"><span data-stu-id="51310-166">0x10</span></span> | <span data-ttu-id="51310-167">Zwraca tylko te nazwy właściwości, które należą do klasy najdalszych pochodnych.</span><span class="sxs-lookup"><span data-stu-id="51310-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="51310-168">Wyklucz właściwości z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="51310-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="51310-169">0x20</span><span class="sxs-lookup"><span data-stu-id="51310-169">0x20</span></span> | <span data-ttu-id="51310-170">Zwraca tylko te nazwy właściwości, które należą do klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="51310-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="51310-171">0x30</span><span class="sxs-lookup"><span data-stu-id="51310-171">0x30</span></span> | <span data-ttu-id="51310-172">Zwraca tylko nazwy właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="51310-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="51310-173">0x40</span><span class="sxs-lookup"><span data-stu-id="51310-173">0x40</span></span> | <span data-ttu-id="51310-174">Zwraca tylko nazwy właściwości nie ma systemu.</span><span class="sxs-lookup"><span data-stu-id="51310-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="51310-175">Funkcja zawsze przydziela nowy `SAFEARRAY` Jeśli zwróci ona `WBEM_S_NO_ERROR`, i `pstrNames` ma zawsze wartość on.</span><span class="sxs-lookup"><span data-stu-id="51310-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="51310-176">Zwracana tablica mogą mieć 0 elementów, jeśli nie znaleziono właściwości pasujących określonych filtrów.</span><span class="sxs-lookup"><span data-stu-id="51310-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="51310-177">Jeśli funkcja zwraca wartość innych niż `WBM_S_NO_ERROR`, nowy `SAFEARRAY` struktury nie są zwracane.</span><span class="sxs-lookup"><span data-stu-id="51310-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="51310-178">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51310-178">Requirements</span></span>  
 <span data-ttu-id="51310-179">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51310-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51310-180">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="51310-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="51310-181">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="51310-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51310-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51310-182">See also</span></span>  
[<span data-ttu-id="51310-183">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="51310-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
