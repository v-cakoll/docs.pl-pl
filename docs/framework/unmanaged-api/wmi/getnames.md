---
title: GetNames, funkcja (odwołanie do niezarządzanego interfejsu API)
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
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174956"
---
# <a name="getnames-function"></a><span data-ttu-id="51a3b-103">GetNames, funkcja</span><span class="sxs-lookup"><span data-stu-id="51a3b-103">GetNames function</span></span>
<span data-ttu-id="51a3b-104">Pobiera podzbiór lub wszystkie nazwy właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="51a3b-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="51a3b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="51a3b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
);
```  

## <a name="parameters"></a><span data-ttu-id="51a3b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="51a3b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="51a3b-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="51a3b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="51a3b-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="51a3b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="51a3b-109">[w] Wskaźnik do prawidłowego, `LPCWSTR` który określa nazwę kwalifikatora, który działa jako część filtru.</span><span class="sxs-lookup"><span data-stu-id="51a3b-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="51a3b-110">Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.</span><span class="sxs-lookup"><span data-stu-id="51a3b-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="51a3b-111">Ten parametr `null`może być .</span><span class="sxs-lookup"><span data-stu-id="51a3b-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="51a3b-112">[w] Kombinacja pól bitowych.</span><span class="sxs-lookup"><span data-stu-id="51a3b-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="51a3b-113">Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.</span><span class="sxs-lookup"><span data-stu-id="51a3b-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="51a3b-114">`pQualifierValue`[w] Wskaźnik do prawidłowej `VARIANT` struktury zainicjowany do wartości filtru.</span><span class="sxs-lookup"><span data-stu-id="51a3b-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="51a3b-115">Ten parametr `null`może być .</span><span class="sxs-lookup"><span data-stu-id="51a3b-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="51a3b-116">[na zewnątrz] Struktura `SAFEARRAY` zawierająca nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="51a3b-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="51a3b-117">Przy wprowadzaniu ten parametr musi `null`być zawsze wskaźnikiem do .</span><span class="sxs-lookup"><span data-stu-id="51a3b-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="51a3b-118">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="51a3b-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="51a3b-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="51a3b-119">Return value</span></span>

<span data-ttu-id="51a3b-120">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="51a3b-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="51a3b-121">Stały</span><span class="sxs-lookup"><span data-stu-id="51a3b-121">Constant</span></span>  |<span data-ttu-id="51a3b-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="51a3b-122">Value</span></span>  |<span data-ttu-id="51a3b-123">Opis</span><span class="sxs-lookup"><span data-stu-id="51a3b-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="51a3b-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="51a3b-124">0x80041001</span></span> | <span data-ttu-id="51a3b-125">Wystąpiła ogólna porażka.</span><span class="sxs-lookup"><span data-stu-id="51a3b-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="51a3b-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="51a3b-126">0x80041008</span></span> | <span data-ttu-id="51a3b-127">Jeden lub więcej parametrów jest nieprawidłowych lub określono niepoprawną kombinację flag i parametrów.</span><span class="sxs-lookup"><span data-stu-id="51a3b-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="51a3b-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="51a3b-128">0x80041006</span></span> | <span data-ttu-id="51a3b-129">Za mało pamięci jest dostępna do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="51a3b-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="51a3b-130">0</span><span class="sxs-lookup"><span data-stu-id="51a3b-130">0</span></span> | <span data-ttu-id="51a3b-131">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="51a3b-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="51a3b-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51a3b-132">Remarks</span></span>

<span data-ttu-id="51a3b-133">Ta funkcja zawija wywołanie [metody IWbemClassObject::GetNames.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)</span><span class="sxs-lookup"><span data-stu-id="51a3b-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="51a3b-134">Zwracane nazwy są kontrolowane przez kombinację flag i parametrów.</span><span class="sxs-lookup"><span data-stu-id="51a3b-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="51a3b-135">Na przykład funkcja może zwracać nazwy wszystkich właściwości lub tylko nazwy właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="51a3b-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="51a3b-136">Filtr podstawowy jest określony `lFlags` w parametrze, a inne parametry różnią się w zależności od niego.</span><span class="sxs-lookup"><span data-stu-id="51a3b-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="51a3b-137">Wartości flagi `lFlags` są polami bitowymi</span><span class="sxs-lookup"><span data-stu-id="51a3b-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="51a3b-138">Flagi, które mogą być `lEnumFlags` przekazywane jako argument są pola bitowe, które są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="51a3b-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="51a3b-139">Można połączyć jedną flagę z każdej grupy z dowolną flagą z dowolnej innej grupy.</span><span class="sxs-lookup"><span data-stu-id="51a3b-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="51a3b-140">Jednak flagi z tej samej grupy wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="51a3b-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="51a3b-141">Flagi grupy 1</span><span class="sxs-lookup"><span data-stu-id="51a3b-141">Group 1 flags</span></span> |<span data-ttu-id="51a3b-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="51a3b-142">Value</span></span>  |<span data-ttu-id="51a3b-143">Opis</span><span class="sxs-lookup"><span data-stu-id="51a3b-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="51a3b-144">0</span><span class="sxs-lookup"><span data-stu-id="51a3b-144">0</span></span> | <span data-ttu-id="51a3b-145">Zwraca wszystkie nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="51a3b-145">Return all property names.</span></span> <span data-ttu-id="51a3b-146">`strQualifierName`i `pQualifierVal` są nieużywane.</span><span class="sxs-lookup"><span data-stu-id="51a3b-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="51a3b-147">1</span><span class="sxs-lookup"><span data-stu-id="51a3b-147">1</span></span> | <span data-ttu-id="51a3b-148">Zwraca tylko właściwości, które mają kwalifikator nazwy określonej `strQualifierName` przez parametr.</span><span class="sxs-lookup"><span data-stu-id="51a3b-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="51a3b-149">Jeśli ta flaga jest `strQualifierName`używana, należy określić .</span><span class="sxs-lookup"><span data-stu-id="51a3b-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="51a3b-150">2</span><span class="sxs-lookup"><span data-stu-id="51a3b-150">2</span></span> |  <span data-ttu-id="51a3b-151">Zwraca tylko właściwości, które nie mają kwalifikator nazwy określonej przez `strQualifierName` parametr.</span><span class="sxs-lookup"><span data-stu-id="51a3b-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="51a3b-152">Jeśli ta flaga jest `strQualifierName`używana, należy określić .</span><span class="sxs-lookup"><span data-stu-id="51a3b-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="51a3b-153">3</span><span class="sxs-lookup"><span data-stu-id="51a3b-153">3</span></span> | <span data-ttu-id="51a3b-154">Zwraca tylko właściwości, które mają kwalifikator nazwy określonej przez `wszQualifierName` parametr, `pQualifierVal` a także mają wartość identyczną z określoną przez strukturę.</span><span class="sxs-lookup"><span data-stu-id="51a3b-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="51a3b-155">Jeśli ta flaga jest używana, `wszQualifierName` należy `pQualifierValue`określić zarówno a, jak i .</span><span class="sxs-lookup"><span data-stu-id="51a3b-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="51a3b-156">Flagi grupy 2</span><span class="sxs-lookup"><span data-stu-id="51a3b-156">Group 2 flags</span></span> |<span data-ttu-id="51a3b-157">Wartość</span><span class="sxs-lookup"><span data-stu-id="51a3b-157">Value</span></span>  |<span data-ttu-id="51a3b-158">Opis</span><span class="sxs-lookup"><span data-stu-id="51a3b-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="51a3b-159">0x4</span><span class="sxs-lookup"><span data-stu-id="51a3b-159">0x4</span></span> | <span data-ttu-id="51a3b-160">Zwraca tylko nazwy właściwości, które definiują klucze.</span><span class="sxs-lookup"><span data-stu-id="51a3b-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="51a3b-161">0x8</span><span class="sxs-lookup"><span data-stu-id="51a3b-161">0x8</span></span> | <span data-ttu-id="51a3b-162">Zwracanie tylko nazw właściwości, które są odwołaniami do obiektów.</span><span class="sxs-lookup"><span data-stu-id="51a3b-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="51a3b-163">Flagi grupy 3</span><span class="sxs-lookup"><span data-stu-id="51a3b-163">Group 3 flags</span></span> |<span data-ttu-id="51a3b-164">Wartość</span><span class="sxs-lookup"><span data-stu-id="51a3b-164">Value</span></span>  |<span data-ttu-id="51a3b-165">Opis</span><span class="sxs-lookup"><span data-stu-id="51a3b-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="51a3b-166">0x10</span><span class="sxs-lookup"><span data-stu-id="51a3b-166">0x10</span></span> | <span data-ttu-id="51a3b-167">Zwraca tylko nazwy właściwości, które należą do najbardziej pochodnej klasy.</span><span class="sxs-lookup"><span data-stu-id="51a3b-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="51a3b-168">Wyklucz właściwości z klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="51a3b-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="51a3b-169">0x20</span><span class="sxs-lookup"><span data-stu-id="51a3b-169">0x20</span></span> | <span data-ttu-id="51a3b-170">Zwracanie tylko nazw właściwości, które należą do klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="51a3b-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="51a3b-171">0x30</span><span class="sxs-lookup"><span data-stu-id="51a3b-171">0x30</span></span> | <span data-ttu-id="51a3b-172">Zwraca tylko nazwy właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="51a3b-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="51a3b-173">0x40</span><span class="sxs-lookup"><span data-stu-id="51a3b-173">0x40</span></span> | <span data-ttu-id="51a3b-174">Zwraca tylko nazwy właściwości niesystemowych.</span><span class="sxs-lookup"><span data-stu-id="51a3b-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="51a3b-175">Funkcja zawsze przydziela nowy, `SAFEARRAY` jeśli `WBEM_S_NO_ERROR`zwraca `pstrNames` , i jest zawsze ustawiony, aby wskazać na niego.</span><span class="sxs-lookup"><span data-stu-id="51a3b-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="51a3b-176">Zwrócona tablica może mieć 0 elementów, jeśli żadne właściwości nie pasują do określonych filtrów.</span><span class="sxs-lookup"><span data-stu-id="51a3b-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="51a3b-177">Jeśli funkcja zwraca wartość `WBM_S_NO_ERROR`inną niż `SAFEARRAY` , nowa struktura nie jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="51a3b-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="51a3b-178">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51a3b-178">Requirements</span></span>  
 <span data-ttu-id="51a3b-179">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51a3b-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51a3b-180">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="51a3b-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="51a3b-181">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="51a3b-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51a3b-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51a3b-182">See also</span></span>

- [<span data-ttu-id="51a3b-183">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="51a3b-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
