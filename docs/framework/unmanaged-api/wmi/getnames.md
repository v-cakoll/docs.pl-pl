---
title: Funkcja GetNames (niezarządzany wykaz interfejsów API)
description: Funkcja GetNames pobiera nazwy właściwości obiektu.
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0065b2cbbd17c5bb3dca6773951cdb8729e59fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583564"
---
# <a name="getnames-function"></a><span data-ttu-id="cb74e-103">Funkcja GetNames</span><span class="sxs-lookup"><span data-stu-id="cb74e-103">GetNames function</span></span>
<span data-ttu-id="cb74e-104">Pobiera podzbiór lub wszystkie nazwy właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="cb74e-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="cb74e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb74e-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="cb74e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb74e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="cb74e-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="cb74e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="cb74e-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cb74e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="cb74e-109">[in] Wskaźnik do prawidłowego `LPCWSTR` określający nazwę kwalifikator, która działa jako część filtru.</span><span class="sxs-lookup"><span data-stu-id="cb74e-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="cb74e-110">Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.</span><span class="sxs-lookup"><span data-stu-id="cb74e-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="cb74e-111">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="cb74e-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="cb74e-112">[in] Kombinacja pól bitowych.</span><span class="sxs-lookup"><span data-stu-id="cb74e-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="cb74e-113">Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.</span><span class="sxs-lookup"><span data-stu-id="cb74e-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="cb74e-114">[in] Wskaźnik do prawidłowego `VARIANT` struktury inicjowany do wartości filtru.</span><span class="sxs-lookup"><span data-stu-id="cb74e-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="cb74e-115">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="cb74e-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="cb74e-116">[out] A `SAFEARRAY` strukturę, która zawiera nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb74e-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="cb74e-117">Przy uruchamianiu, ten parametr musi być zawsze wskaźnik do `null`.</span><span class="sxs-lookup"><span data-stu-id="cb74e-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="cb74e-118">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="cb74e-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="cb74e-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cb74e-119">Return value</span></span>

<span data-ttu-id="cb74e-120">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="cb74e-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cb74e-121">Stała</span><span class="sxs-lookup"><span data-stu-id="cb74e-121">Constant</span></span>  |<span data-ttu-id="cb74e-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="cb74e-122">Value</span></span>  |<span data-ttu-id="cb74e-123">Opis</span><span class="sxs-lookup"><span data-stu-id="cb74e-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="cb74e-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="cb74e-124">0x80041001</span></span> | <span data-ttu-id="cb74e-125">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="cb74e-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="cb74e-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="cb74e-126">0x80041008</span></span> | <span data-ttu-id="cb74e-127">Jeden lub więcej parametrów są nieprawidłowe lub została określona nieprawidłowa kombinacja flag i parametry.</span><span class="sxs-lookup"><span data-stu-id="cb74e-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="cb74e-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="cb74e-128">0x80041006</span></span> | <span data-ttu-id="cb74e-129">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="cb74e-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="cb74e-130">0</span><span class="sxs-lookup"><span data-stu-id="cb74e-130">0</span></span> | <span data-ttu-id="cb74e-131">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cb74e-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="cb74e-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb74e-132">Remarks</span></span>

<span data-ttu-id="cb74e-133">Ta funkcja zawija wywołanie do [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) metody.</span><span class="sxs-lookup"><span data-stu-id="cb74e-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="cb74e-134">Nazwane zwracane są kontrolowane przez kombinacja flag i parametry.</span><span class="sxs-lookup"><span data-stu-id="cb74e-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="cb74e-135">Na przykład funkcja może zwrócić wszystkie właściwości lub tylko nazwy właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="cb74e-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="cb74e-136">Filtr podstawowy jest określony w `lFlags` parametru i inne parametry różnią się w zależności od jego.</span><span class="sxs-lookup"><span data-stu-id="cb74e-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="cb74e-137">Flaga wartości w `lFlags` pól bitowych</span><span class="sxs-lookup"><span data-stu-id="cb74e-137">The flag values in `lFlags` are bit fields</span></span>


<span data-ttu-id="cb74e-138">Flagi, które mogą być przekazywane jako `lEnumFlags` należą pola bitowe, które są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="cb74e-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="cb74e-139">Można łączyć z jedną flagę z każdej grupy za pomocą jakakolwiek Flaga w żadnej innej grupy.</span><span class="sxs-lookup"><span data-stu-id="cb74e-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="cb74e-140">Jednak flagi z tej samej grupy wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="cb74e-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="cb74e-141">Flagi grupy 1</span><span class="sxs-lookup"><span data-stu-id="cb74e-141">Group 1 flags</span></span> |<span data-ttu-id="cb74e-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="cb74e-142">Value</span></span>  |<span data-ttu-id="cb74e-143">Opis</span><span class="sxs-lookup"><span data-stu-id="cb74e-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="cb74e-144">0</span><span class="sxs-lookup"><span data-stu-id="cb74e-144">0</span></span> | <span data-ttu-id="cb74e-145">Zwróć wszystkie nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb74e-145">Return all property names.</span></span> <span data-ttu-id="cb74e-146">`strQualifierName` i `pQualifierVal` są używane.</span><span class="sxs-lookup"><span data-stu-id="cb74e-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="cb74e-147">1</span><span class="sxs-lookup"><span data-stu-id="cb74e-147">1</span></span> | <span data-ttu-id="cb74e-148">Zwraca tylko właściwości, które mają kwalifikator o nazwie określonej przez `strQualifierName` parametru.</span><span class="sxs-lookup"><span data-stu-id="cb74e-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="cb74e-149">Jeśli ta flaga jest używany, należy określić `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="cb74e-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="cb74e-150">2</span><span class="sxs-lookup"><span data-stu-id="cb74e-150">2</span></span> |  <span data-ttu-id="cb74e-151">Zwraca tylko właściwości, które nie mają kwalifikator o nazwie określonej przez `strQualifierName` parametru.</span><span class="sxs-lookup"><span data-stu-id="cb74e-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="cb74e-152">Jeśli ta flaga jest używany, należy określić `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="cb74e-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="cb74e-153">3</span><span class="sxs-lookup"><span data-stu-id="cb74e-153">3</span></span> | <span data-ttu-id="cb74e-154">Zwraca tylko te właściwości, które mają kwalifikator o nazwie określonej przez `wszQualifierName` parametru i także mieć wartość taka sama jak określona przez `pQualifierVal` struktury.</span><span class="sxs-lookup"><span data-stu-id="cb74e-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="cb74e-155">Jeśli ta flaga jest używany, należy określić zarówno `wszQualifierName` i `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="cb74e-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="cb74e-156">Flags — grupa 2</span><span class="sxs-lookup"><span data-stu-id="cb74e-156">Group 2 flags</span></span> |<span data-ttu-id="cb74e-157">Wartość</span><span class="sxs-lookup"><span data-stu-id="cb74e-157">Value</span></span>  |<span data-ttu-id="cb74e-158">Opis</span><span class="sxs-lookup"><span data-stu-id="cb74e-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="cb74e-159">0x4</span><span class="sxs-lookup"><span data-stu-id="cb74e-159">0x4</span></span> | <span data-ttu-id="cb74e-160">Zwraca tylko nazwy właściwości, które definiują kluczy.</span><span class="sxs-lookup"><span data-stu-id="cb74e-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="cb74e-161">0x8</span><span class="sxs-lookup"><span data-stu-id="cb74e-161">0x8</span></span> | <span data-ttu-id="cb74e-162">Zwracane tylko nazwy właściwości, które są odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="cb74e-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="cb74e-163">Flagi grupa 3</span><span class="sxs-lookup"><span data-stu-id="cb74e-163">Group 3 flags</span></span> |<span data-ttu-id="cb74e-164">Wartość</span><span class="sxs-lookup"><span data-stu-id="cb74e-164">Value</span></span>  |<span data-ttu-id="cb74e-165">Opis</span><span class="sxs-lookup"><span data-stu-id="cb74e-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="cb74e-166">0x10</span><span class="sxs-lookup"><span data-stu-id="cb74e-166">0x10</span></span> | <span data-ttu-id="cb74e-167">Zwróć tylko nazwy właściwości, które należą do najbardziej pochodnej klasy.</span><span class="sxs-lookup"><span data-stu-id="cb74e-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="cb74e-168">Wyklucz właściwości z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="cb74e-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="cb74e-169">0x20</span><span class="sxs-lookup"><span data-stu-id="cb74e-169">0x20</span></span> | <span data-ttu-id="cb74e-170">Zwróć tylko nazwy właściwości, które należą do klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="cb74e-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="cb74e-171">0x30</span><span class="sxs-lookup"><span data-stu-id="cb74e-171">0x30</span></span> | <span data-ttu-id="cb74e-172">Zwraca tylko nazwy właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="cb74e-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="cb74e-173">0x40</span><span class="sxs-lookup"><span data-stu-id="cb74e-173">0x40</span></span> | <span data-ttu-id="cb74e-174">Zwraca tylko nazwy właściwości-system.</span><span class="sxs-lookup"><span data-stu-id="cb74e-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="cb74e-175">Funkcja zawsze przydziela nową `SAFEARRAY` Jeśli zwróci ona `WBEM_S_NO_ERROR`, i `pstrNames` ma zawsze wartość on.</span><span class="sxs-lookup"><span data-stu-id="cb74e-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="cb74e-176">Zwracana tablica może mieć 0 elementów, jeśli nie znaleziono właściwości pasujących określonych filtrów.</span><span class="sxs-lookup"><span data-stu-id="cb74e-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="cb74e-177">Jeśli funkcja zwraca wartości innych niż `WBM_S_NO_ERROR`, nowy `SAFEARRAY` struktura nie jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="cb74e-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="cb74e-178">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb74e-178">Requirements</span></span>  
 <span data-ttu-id="cb74e-179">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb74e-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb74e-180">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cb74e-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cb74e-181">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cb74e-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb74e-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb74e-182">See also</span></span>
- [<span data-ttu-id="cb74e-183">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="cb74e-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
