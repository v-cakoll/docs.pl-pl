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
ms.openlocfilehash: f53174bf060938d5a55cbd196944ac11916d59cd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661397"
---
# <a name="getnames-function"></a><span data-ttu-id="8c633-103">Funkcja GetNames</span><span class="sxs-lookup"><span data-stu-id="8c633-103">GetNames function</span></span>
<span data-ttu-id="8c633-104">Pobiera podzbiór lub wszystkie nazwy właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="8c633-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="8c633-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c633-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="8c633-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c633-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8c633-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="8c633-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8c633-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8c633-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="8c633-109">[in] Wskaźnik do prawidłowego `LPCWSTR` określający nazwę kwalifikator, która działa jako część filtru.</span><span class="sxs-lookup"><span data-stu-id="8c633-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="8c633-110">Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.</span><span class="sxs-lookup"><span data-stu-id="8c633-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="8c633-111">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="8c633-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="8c633-112">[in] Kombinacja pól bitowych.</span><span class="sxs-lookup"><span data-stu-id="8c633-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="8c633-113">Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.</span><span class="sxs-lookup"><span data-stu-id="8c633-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="8c633-114">[in] Wskaźnik do prawidłowego `VARIANT` struktury inicjowany do wartości filtru.</span><span class="sxs-lookup"><span data-stu-id="8c633-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="8c633-115">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="8c633-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="8c633-116">[out] A `SAFEARRAY` strukturę, która zawiera nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c633-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="8c633-117">Przy uruchamianiu, ten parametr musi być zawsze wskaźnik do `null`.</span><span class="sxs-lookup"><span data-stu-id="8c633-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="8c633-118">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8c633-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="8c633-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8c633-119">Return value</span></span>

<span data-ttu-id="8c633-120">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="8c633-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8c633-121">Stała</span><span class="sxs-lookup"><span data-stu-id="8c633-121">Constant</span></span>  |<span data-ttu-id="8c633-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="8c633-122">Value</span></span>  |<span data-ttu-id="8c633-123">Opis</span><span class="sxs-lookup"><span data-stu-id="8c633-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="8c633-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8c633-124">0x80041001</span></span> | <span data-ttu-id="8c633-125">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="8c633-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8c633-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8c633-126">0x80041008</span></span> | <span data-ttu-id="8c633-127">Jeden lub więcej parametrów są nieprawidłowe lub została określona nieprawidłowa kombinacja flag i parametry.</span><span class="sxs-lookup"><span data-stu-id="8c633-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8c633-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8c633-128">0x80041006</span></span> | <span data-ttu-id="8c633-129">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="8c633-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8c633-130">0</span><span class="sxs-lookup"><span data-stu-id="8c633-130">0</span></span> | <span data-ttu-id="8c633-131">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8c633-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8c633-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c633-132">Remarks</span></span>

<span data-ttu-id="8c633-133">Ta funkcja zawija wywołanie do [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) metody.</span><span class="sxs-lookup"><span data-stu-id="8c633-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="8c633-134">Nazwane zwracane są kontrolowane przez kombinacja flag i parametry.</span><span class="sxs-lookup"><span data-stu-id="8c633-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="8c633-135">Na przykład funkcja może zwrócić wszystkie właściwości lub tylko nazwy właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="8c633-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="8c633-136">Filtr podstawowy jest określony w `lFlags` parametru i inne parametry różnią się w zależności od jego.</span><span class="sxs-lookup"><span data-stu-id="8c633-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="8c633-137">Flaga wartości w `lFlags` pól bitowych</span><span class="sxs-lookup"><span data-stu-id="8c633-137">The flag values in `lFlags` are bit fields</span></span>


<span data-ttu-id="8c633-138">Flagi, które mogą być przekazywane jako `lEnumFlags` należą pola bitowe, które są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8c633-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="8c633-139">Można łączyć z jedną flagę z każdej grupy za pomocą jakakolwiek Flaga w żadnej innej grupy.</span><span class="sxs-lookup"><span data-stu-id="8c633-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="8c633-140">Jednak flagi z tej samej grupy wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="8c633-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="8c633-141">Flagi grupy 1</span><span class="sxs-lookup"><span data-stu-id="8c633-141">Group 1 flags</span></span> |<span data-ttu-id="8c633-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="8c633-142">Value</span></span>  |<span data-ttu-id="8c633-143">Opis</span><span class="sxs-lookup"><span data-stu-id="8c633-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="8c633-144">0</span><span class="sxs-lookup"><span data-stu-id="8c633-144">0</span></span> | <span data-ttu-id="8c633-145">Zwróć wszystkie nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c633-145">Return all property names.</span></span> <span data-ttu-id="8c633-146">`strQualifierName` i `pQualifierVal` są używane.</span><span class="sxs-lookup"><span data-stu-id="8c633-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="8c633-147">1</span><span class="sxs-lookup"><span data-stu-id="8c633-147">1</span></span> | <span data-ttu-id="8c633-148">Zwraca tylko właściwości, które mają kwalifikator o nazwie określonej przez `strQualifierName` parametru.</span><span class="sxs-lookup"><span data-stu-id="8c633-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="8c633-149">Jeśli ta flaga jest używany, należy określić `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="8c633-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="8c633-150">2</span><span class="sxs-lookup"><span data-stu-id="8c633-150">2</span></span> |  <span data-ttu-id="8c633-151">Zwraca tylko właściwości, które nie mają kwalifikator o nazwie określonej przez `strQualifierName` parametru.</span><span class="sxs-lookup"><span data-stu-id="8c633-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="8c633-152">Jeśli ta flaga jest używany, należy określić `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="8c633-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="8c633-153">3</span><span class="sxs-lookup"><span data-stu-id="8c633-153">3</span></span> | <span data-ttu-id="8c633-154">Zwraca tylko te właściwości, które mają kwalifikator o nazwie określonej przez `wszQualifierName` parametru i także mieć wartość taka sama jak określona przez `pQualifierVal` struktury.</span><span class="sxs-lookup"><span data-stu-id="8c633-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="8c633-155">Jeśli ta flaga jest używany, należy określić zarówno `wszQualifierName` i `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="8c633-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="8c633-156">Flags — grupa 2</span><span class="sxs-lookup"><span data-stu-id="8c633-156">Group 2 flags</span></span> |<span data-ttu-id="8c633-157">Wartość</span><span class="sxs-lookup"><span data-stu-id="8c633-157">Value</span></span>  |<span data-ttu-id="8c633-158">Opis</span><span class="sxs-lookup"><span data-stu-id="8c633-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="8c633-159">0x4</span><span class="sxs-lookup"><span data-stu-id="8c633-159">0x4</span></span> | <span data-ttu-id="8c633-160">Zwraca tylko nazwy właściwości, które definiują kluczy.</span><span class="sxs-lookup"><span data-stu-id="8c633-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="8c633-161">0x8</span><span class="sxs-lookup"><span data-stu-id="8c633-161">0x8</span></span> | <span data-ttu-id="8c633-162">Zwracane tylko nazwy właściwości, które są odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="8c633-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="8c633-163">Flagi grupa 3</span><span class="sxs-lookup"><span data-stu-id="8c633-163">Group 3 flags</span></span> |<span data-ttu-id="8c633-164">Wartość</span><span class="sxs-lookup"><span data-stu-id="8c633-164">Value</span></span>  |<span data-ttu-id="8c633-165">Opis</span><span class="sxs-lookup"><span data-stu-id="8c633-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="8c633-166">0x10</span><span class="sxs-lookup"><span data-stu-id="8c633-166">0x10</span></span> | <span data-ttu-id="8c633-167">Zwróć tylko nazwy właściwości, które należą do najbardziej pochodnej klasy.</span><span class="sxs-lookup"><span data-stu-id="8c633-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="8c633-168">Wyklucz właściwości z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="8c633-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="8c633-169">0x20</span><span class="sxs-lookup"><span data-stu-id="8c633-169">0x20</span></span> | <span data-ttu-id="8c633-170">Zwróć tylko nazwy właściwości, które należą do klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="8c633-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="8c633-171">0x30</span><span class="sxs-lookup"><span data-stu-id="8c633-171">0x30</span></span> | <span data-ttu-id="8c633-172">Zwraca tylko nazwy właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="8c633-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="8c633-173">0x40</span><span class="sxs-lookup"><span data-stu-id="8c633-173">0x40</span></span> | <span data-ttu-id="8c633-174">Zwraca tylko nazwy właściwości-system.</span><span class="sxs-lookup"><span data-stu-id="8c633-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="8c633-175">Funkcja zawsze przydziela nową `SAFEARRAY` Jeśli zwróci ona `WBEM_S_NO_ERROR`, i `pstrNames` ma zawsze wartość on.</span><span class="sxs-lookup"><span data-stu-id="8c633-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="8c633-176">Zwracana tablica może mieć 0 elementów, jeśli nie znaleziono właściwości pasujących określonych filtrów.</span><span class="sxs-lookup"><span data-stu-id="8c633-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="8c633-177">Jeśli funkcja zwraca wartości innych niż `WBM_S_NO_ERROR`, nowy `SAFEARRAY` struktura nie jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="8c633-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="8c633-178">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c633-178">Requirements</span></span>  
 <span data-ttu-id="8c633-179">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c633-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c633-180">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8c633-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8c633-181">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8c633-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c633-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c633-182">See also</span></span>  
[<span data-ttu-id="8c633-183">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="8c633-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
