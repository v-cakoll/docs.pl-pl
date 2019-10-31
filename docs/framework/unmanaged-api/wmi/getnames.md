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
ms.openlocfilehash: 5b03ed6a68fbe288e93dedb4f425f1511563dfeb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102523"
---
# <a name="getnames-function"></a><span data-ttu-id="a03a2-103">GetNames, funkcja</span><span class="sxs-lookup"><span data-stu-id="a03a2-103">GetNames function</span></span>
<span data-ttu-id="a03a2-104">Pobiera podzestaw lub wszystkie nazwy właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="a03a2-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a03a2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a03a2-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="a03a2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a03a2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a03a2-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="a03a2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a03a2-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="a03a2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="a03a2-109">podczas Wskaźnik do prawidłowego `LPCWSTR`, który określa nazwę kwalifikatora, który działa jako część filtru.</span><span class="sxs-lookup"><span data-stu-id="a03a2-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="a03a2-110">Aby uzyskać więcej informacji, zobacz sekcję [uwagi](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="a03a2-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="a03a2-111">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="a03a2-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="a03a2-112">podczas Kombinacja pól bitowych.</span><span class="sxs-lookup"><span data-stu-id="a03a2-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="a03a2-113">Aby uzyskać więcej informacji, zobacz sekcję [uwagi](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="a03a2-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="a03a2-114">podczas Zainicjowano wskaźnik do prawidłowej struktury `VARIANT` w wartości filtru.</span><span class="sxs-lookup"><span data-stu-id="a03a2-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="a03a2-115">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="a03a2-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="a03a2-116">określoną Struktura `SAFEARRAY`, która zawiera nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="a03a2-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="a03a2-117">We wpisie, ten parametr musi być zawsze wskaźnikiem do `null`.</span><span class="sxs-lookup"><span data-stu-id="a03a2-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="a03a2-118">Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="a03a2-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="a03a2-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a03a2-119">Return value</span></span>

<span data-ttu-id="a03a2-120">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="a03a2-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a03a2-121">Stała</span><span class="sxs-lookup"><span data-stu-id="a03a2-121">Constant</span></span>  |<span data-ttu-id="a03a2-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="a03a2-122">Value</span></span>  |<span data-ttu-id="a03a2-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a03a2-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="a03a2-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a03a2-124">0x80041001</span></span> | <span data-ttu-id="a03a2-125">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="a03a2-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a03a2-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a03a2-126">0x80041008</span></span> | <span data-ttu-id="a03a2-127">Co najmniej jeden parametr jest nieprawidłowy lub określono niepoprawną kombinację flag i parametrów.</span><span class="sxs-lookup"><span data-stu-id="a03a2-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a03a2-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a03a2-128">0x80041006</span></span> | <span data-ttu-id="a03a2-129">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="a03a2-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a03a2-130">0</span><span class="sxs-lookup"><span data-stu-id="a03a2-130">0</span></span> | <span data-ttu-id="a03a2-131">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a03a2-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a03a2-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a03a2-132">Remarks</span></span>

<span data-ttu-id="a03a2-133">Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) .</span><span class="sxs-lookup"><span data-stu-id="a03a2-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="a03a2-134">Nazwane zwracane są kontrolowane przez kombinację flag i parametrów.</span><span class="sxs-lookup"><span data-stu-id="a03a2-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="a03a2-135">Na przykład funkcja może zwracać nazwy wszystkich właściwości lub tylko nazwy właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="a03a2-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="a03a2-136">Filtr podstawowy jest określony w parametrze `lFlags`, a inne parametry różnią się w zależności od tego.</span><span class="sxs-lookup"><span data-stu-id="a03a2-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="a03a2-137">Wartości flag w `lFlags` są polami bitowymi</span><span class="sxs-lookup"><span data-stu-id="a03a2-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="a03a2-138">Flagi, które mogą być przesyłane jako argument `lEnumFlags` są polami bitowymi, które są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a03a2-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="a03a2-139">Można połączyć jedną flagę z każdej grupy z dowolną flagą z dowolnej innej grupy.</span><span class="sxs-lookup"><span data-stu-id="a03a2-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="a03a2-140">Jednak flagi z tej samej grupy wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="a03a2-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="a03a2-141">Flagi grupy 1</span><span class="sxs-lookup"><span data-stu-id="a03a2-141">Group 1 flags</span></span> |<span data-ttu-id="a03a2-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="a03a2-142">Value</span></span>  |<span data-ttu-id="a03a2-143">Opis</span><span class="sxs-lookup"><span data-stu-id="a03a2-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="a03a2-144">0</span><span class="sxs-lookup"><span data-stu-id="a03a2-144">0</span></span> | <span data-ttu-id="a03a2-145">Zwróć wszystkie nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="a03a2-145">Return all property names.</span></span> <span data-ttu-id="a03a2-146">`strQualifierName` i `pQualifierVal` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="a03a2-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="a03a2-147">1</span><span class="sxs-lookup"><span data-stu-id="a03a2-147">1</span></span> | <span data-ttu-id="a03a2-148">Zwraca tylko właściwości, które mają kwalifikator o nazwie określonej przez parametr `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="a03a2-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="a03a2-149">Jeśli ta flaga jest używana, należy określić `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="a03a2-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="a03a2-150">2</span><span class="sxs-lookup"><span data-stu-id="a03a2-150">2</span></span> |  <span data-ttu-id="a03a2-151">Zwraca tylko właściwości, które nie mają kwalifikatora nazwy określonej przez parametr `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="a03a2-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="a03a2-152">Jeśli ta flaga jest używana, należy określić `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="a03a2-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="a03a2-153">3</span><span class="sxs-lookup"><span data-stu-id="a03a2-153">3</span></span> | <span data-ttu-id="a03a2-154">Zwraca tylko właściwości, które mają kwalifikator o nazwie określonej przez parametr `wszQualifierName` i ma również wartość identyczną z określoną przez strukturę `pQualifierVal`.</span><span class="sxs-lookup"><span data-stu-id="a03a2-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="a03a2-155">Jeśli ta flaga jest używana, należy określić zarówno `wszQualifierName`, jak i `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="a03a2-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="a03a2-156">Flagi grupy 2</span><span class="sxs-lookup"><span data-stu-id="a03a2-156">Group 2 flags</span></span> |<span data-ttu-id="a03a2-157">Wartość</span><span class="sxs-lookup"><span data-stu-id="a03a2-157">Value</span></span>  |<span data-ttu-id="a03a2-158">Opis</span><span class="sxs-lookup"><span data-stu-id="a03a2-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="a03a2-159">0x4</span><span class="sxs-lookup"><span data-stu-id="a03a2-159">0x4</span></span> | <span data-ttu-id="a03a2-160">Zwróć tylko nazwy właściwości, które definiują klucze.</span><span class="sxs-lookup"><span data-stu-id="a03a2-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="a03a2-161">0x8</span><span class="sxs-lookup"><span data-stu-id="a03a2-161">0x8</span></span> | <span data-ttu-id="a03a2-162">Zwraca tylko nazwy właściwości, które są odwołaniami do obiektów.</span><span class="sxs-lookup"><span data-stu-id="a03a2-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="a03a2-163">Flagi grupy 3</span><span class="sxs-lookup"><span data-stu-id="a03a2-163">Group 3 flags</span></span> |<span data-ttu-id="a03a2-164">Wartość</span><span class="sxs-lookup"><span data-stu-id="a03a2-164">Value</span></span>  |<span data-ttu-id="a03a2-165">Opis</span><span class="sxs-lookup"><span data-stu-id="a03a2-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="a03a2-166">0x10</span><span class="sxs-lookup"><span data-stu-id="a03a2-166">0x10</span></span> | <span data-ttu-id="a03a2-167">Zwracaj tylko nazwy właściwości, które należą do klasy najbardziej pochodnej.</span><span class="sxs-lookup"><span data-stu-id="a03a2-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="a03a2-168">Wyklucz właściwości z klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a03a2-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="a03a2-169">0x20</span><span class="sxs-lookup"><span data-stu-id="a03a2-169">0x20</span></span> | <span data-ttu-id="a03a2-170">Zwraca tylko nazwy właściwości należące do klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a03a2-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="a03a2-171">0x30</span><span class="sxs-lookup"><span data-stu-id="a03a2-171">0x30</span></span> | <span data-ttu-id="a03a2-172">Zwraca tylko nazwy właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="a03a2-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="a03a2-173">0x40</span><span class="sxs-lookup"><span data-stu-id="a03a2-173">0x40</span></span> | <span data-ttu-id="a03a2-174">Zwróć tylko nazwy właściwości niesystemowych.</span><span class="sxs-lookup"><span data-stu-id="a03a2-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="a03a2-175">Funkcja zawsze przydziela nowy `SAFEARRAY`, jeśli zwraca `WBEM_S_NO_ERROR`, a `pstrNames` jest zawsze ustawiona na to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="a03a2-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="a03a2-176">Zwracana tablica może zawierać 0 elementów, jeśli żadne właściwości nie pasują do określonych filtrów.</span><span class="sxs-lookup"><span data-stu-id="a03a2-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="a03a2-177">Jeśli funkcja zwraca wartość inną niż `WBM_S_NO_ERROR`, Nowa struktura `SAFEARRAY` nie jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="a03a2-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="a03a2-178">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a03a2-178">Requirements</span></span>  
 <span data-ttu-id="a03a2-179">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a03a2-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a03a2-180">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="a03a2-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a03a2-181">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a03a2-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a03a2-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a03a2-182">See also</span></span>

- [<span data-ttu-id="a03a2-183">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="a03a2-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
