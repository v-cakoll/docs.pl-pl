---
title: GetNames — funkcja (niezarządzana dokumentacja interfejsu API)
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
ms.openlocfilehash: 748767596a8f4680a2d7b63cb0579acaed5f53f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798513"
---
# <a name="getnames-function"></a><span data-ttu-id="227f4-103">GetNames, funkcja</span><span class="sxs-lookup"><span data-stu-id="227f4-103">GetNames function</span></span>
<span data-ttu-id="227f4-104">Pobiera podzestaw lub wszystkie nazwy właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="227f4-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="227f4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="227f4-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="227f4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="227f4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="227f4-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="227f4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="227f4-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="227f4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="227f4-109">podczas Wskaźnik do prawidłowego `LPCWSTR` , który określa nazwę kwalifikatora, który działa jako część filtra.</span><span class="sxs-lookup"><span data-stu-id="227f4-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="227f4-110">Aby uzyskać więcej informacji, zobacz sekcję [uwagi](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="227f4-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="227f4-111">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="227f4-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="227f4-112">podczas Kombinacja pól bitowych.</span><span class="sxs-lookup"><span data-stu-id="227f4-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="227f4-113">Aby uzyskać więcej informacji, zobacz sekcję [uwagi](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="227f4-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="227f4-114">podczas Zainicjowano wskaźnik do `VARIANT` prawidłowej struktury na wartość filtru.</span><span class="sxs-lookup"><span data-stu-id="227f4-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="227f4-115">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="227f4-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="227f4-116">określoną `SAFEARRAY` Struktura, która zawiera nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="227f4-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="227f4-117">We wpisie, ten parametr musi być zawsze wskaźnikiem `null`do.</span><span class="sxs-lookup"><span data-stu-id="227f4-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="227f4-118">Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="227f4-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="227f4-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="227f4-119">Return value</span></span>

<span data-ttu-id="227f4-120">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="227f4-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="227f4-121">Stała</span><span class="sxs-lookup"><span data-stu-id="227f4-121">Constant</span></span>  |<span data-ttu-id="227f4-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="227f4-122">Value</span></span>  |<span data-ttu-id="227f4-123">Opis</span><span class="sxs-lookup"><span data-stu-id="227f4-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="227f4-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="227f4-124">0x80041001</span></span> | <span data-ttu-id="227f4-125">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="227f4-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="227f4-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="227f4-126">0x80041008</span></span> | <span data-ttu-id="227f4-127">Co najmniej jeden parametr jest nieprawidłowy lub określono niepoprawną kombinację flag i parametrów.</span><span class="sxs-lookup"><span data-stu-id="227f4-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="227f4-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="227f4-128">0x80041006</span></span> | <span data-ttu-id="227f4-129">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="227f4-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="227f4-130">0</span><span class="sxs-lookup"><span data-stu-id="227f4-130">0</span></span> | <span data-ttu-id="227f4-131">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="227f4-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="227f4-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="227f4-132">Remarks</span></span>

<span data-ttu-id="227f4-133">Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) .</span><span class="sxs-lookup"><span data-stu-id="227f4-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="227f4-134">Nazwane zwracane są kontrolowane przez kombinację flag i parametrów.</span><span class="sxs-lookup"><span data-stu-id="227f4-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="227f4-135">Na przykład funkcja może zwracać nazwy wszystkich właściwości lub tylko nazwy właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="227f4-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="227f4-136">Filtr podstawowy jest określony w `lFlags` parametrze, a inne parametry różnią się w zależności od tego.</span><span class="sxs-lookup"><span data-stu-id="227f4-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="227f4-137">Wartości flag w programie `lFlags` są polami bitowymi</span><span class="sxs-lookup"><span data-stu-id="227f4-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="227f4-138">Flagi, które mogą być przesyłane jako `lEnumFlags` argument są polami bitowymi, które są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="227f4-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="227f4-139">Można połączyć jedną flagę z każdej grupy z dowolną flagą z dowolnej innej grupy.</span><span class="sxs-lookup"><span data-stu-id="227f4-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="227f4-140">Jednak flagi z tej samej grupy wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="227f4-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="227f4-141">Flagi grupy 1</span><span class="sxs-lookup"><span data-stu-id="227f4-141">Group 1 flags</span></span> |<span data-ttu-id="227f4-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="227f4-142">Value</span></span>  |<span data-ttu-id="227f4-143">Opis</span><span class="sxs-lookup"><span data-stu-id="227f4-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="227f4-144">0</span><span class="sxs-lookup"><span data-stu-id="227f4-144">0</span></span> | <span data-ttu-id="227f4-145">Zwróć wszystkie nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="227f4-145">Return all property names.</span></span> <span data-ttu-id="227f4-146">`strQualifierName`i `pQualifierVal` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="227f4-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="227f4-147">1</span><span class="sxs-lookup"><span data-stu-id="227f4-147">1</span></span> | <span data-ttu-id="227f4-148">Zwraca tylko właściwości, które mają kwalifikator o nazwie określonej przez `strQualifierName` parametr.</span><span class="sxs-lookup"><span data-stu-id="227f4-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="227f4-149">Jeśli ta flaga jest używana, należy określić `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="227f4-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="227f4-150">2</span><span class="sxs-lookup"><span data-stu-id="227f4-150">2</span></span> |  <span data-ttu-id="227f4-151">Zwraca tylko właściwości, które nie mają kwalifikatora nazwy określonej przez `strQualifierName` parametr.</span><span class="sxs-lookup"><span data-stu-id="227f4-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="227f4-152">Jeśli ta flaga jest używana, należy określić `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="227f4-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="227f4-153">3</span><span class="sxs-lookup"><span data-stu-id="227f4-153">3</span></span> | <span data-ttu-id="227f4-154">Zwróć tylko właściwości, które mają kwalifikator o nazwie określonej przez `wszQualifierName` parametr, a także mają wartość identyczną z określoną `pQualifierVal` przez strukturę.</span><span class="sxs-lookup"><span data-stu-id="227f4-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="227f4-155">Jeśli ta flaga jest używana, należy określić zarówno `wszQualifierName` , `pQualifierValue`jak i.</span><span class="sxs-lookup"><span data-stu-id="227f4-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="227f4-156">Flagi grupy 2</span><span class="sxs-lookup"><span data-stu-id="227f4-156">Group 2 flags</span></span> |<span data-ttu-id="227f4-157">Wartość</span><span class="sxs-lookup"><span data-stu-id="227f4-157">Value</span></span>  |<span data-ttu-id="227f4-158">Opis</span><span class="sxs-lookup"><span data-stu-id="227f4-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="227f4-159">0x4</span><span class="sxs-lookup"><span data-stu-id="227f4-159">0x4</span></span> | <span data-ttu-id="227f4-160">Zwróć tylko nazwy właściwości, które definiują klucze.</span><span class="sxs-lookup"><span data-stu-id="227f4-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="227f4-161">0x8</span><span class="sxs-lookup"><span data-stu-id="227f4-161">0x8</span></span> | <span data-ttu-id="227f4-162">Zwraca tylko nazwy właściwości, które są odwołaniami do obiektów.</span><span class="sxs-lookup"><span data-stu-id="227f4-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="227f4-163">Flagi grupy 3</span><span class="sxs-lookup"><span data-stu-id="227f4-163">Group 3 flags</span></span> |<span data-ttu-id="227f4-164">Wartość</span><span class="sxs-lookup"><span data-stu-id="227f4-164">Value</span></span>  |<span data-ttu-id="227f4-165">Opis</span><span class="sxs-lookup"><span data-stu-id="227f4-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="227f4-166">0x10</span><span class="sxs-lookup"><span data-stu-id="227f4-166">0x10</span></span> | <span data-ttu-id="227f4-167">Zwracaj tylko nazwy właściwości, które należą do klasy najbardziej pochodnej.</span><span class="sxs-lookup"><span data-stu-id="227f4-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="227f4-168">Wyklucz właściwości z klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="227f4-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="227f4-169">0x20</span><span class="sxs-lookup"><span data-stu-id="227f4-169">0x20</span></span> | <span data-ttu-id="227f4-170">Zwraca tylko nazwy właściwości należące do klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="227f4-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="227f4-171">0x30</span><span class="sxs-lookup"><span data-stu-id="227f4-171">0x30</span></span> | <span data-ttu-id="227f4-172">Zwraca tylko nazwy właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="227f4-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="227f4-173">0x40</span><span class="sxs-lookup"><span data-stu-id="227f4-173">0x40</span></span> | <span data-ttu-id="227f4-174">Zwróć tylko nazwy właściwości niesystemowych.</span><span class="sxs-lookup"><span data-stu-id="227f4-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="227f4-175">Funkcja zawsze przydziela nowe `SAFEARRAY` , jeśli zwraca `WBEM_S_NO_ERROR`, i `pstrNames` zawsze jest ustawione na wartość.</span><span class="sxs-lookup"><span data-stu-id="227f4-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="227f4-176">Zwracana tablica może zawierać 0 elementów, jeśli żadne właściwości nie pasują do określonych filtrów.</span><span class="sxs-lookup"><span data-stu-id="227f4-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="227f4-177">Jeśli funkcja zwraca wartość inną niż `WBM_S_NO_ERROR`, Nowa `SAFEARRAY` struktura nie jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="227f4-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="227f4-178">Wymagania</span><span class="sxs-lookup"><span data-stu-id="227f4-178">Requirements</span></span>  
 <span data-ttu-id="227f4-179">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="227f4-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="227f4-180">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="227f4-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="227f4-181">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="227f4-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="227f4-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="227f4-182">See also</span></span>

- [<span data-ttu-id="227f4-183">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="227f4-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
