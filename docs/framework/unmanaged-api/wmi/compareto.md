---
title: "CompareTo — funkcja (niezarządzany wykaz interfejsów API)"
description: "Funkcja CompareTo porównuje obiekt do innego obiektu WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CompareTo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CompareTo
helpviewer_keywords: CompareTo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 038074b5bb3adc816caa226d3167395758d2ae57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="compareto-function"></a><span data-ttu-id="a70a4-103">CompareTo — funkcja</span><span class="sxs-lookup"><span data-stu-id="a70a4-103">CompareTo function</span></span>
<span data-ttu-id="a70a4-104">Porównuje obiekt do innego obiektu zarządzania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a70a4-104">Compares an object to another Windows management object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a70a4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a70a4-105">Syntax</span></span>  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a><span data-ttu-id="a70a4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a70a4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a70a4-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="a70a4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a70a4-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a70a4-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`flags`  
<span data-ttu-id="a70a4-109">[in] Bitowe połączenie flagi określające właściwości obiektu wziąć pod uwagę do porównania.</span><span class="sxs-lookup"><span data-stu-id="a70a4-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="a70a4-110">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="a70a4-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`  

<span data-ttu-id="a70a4-111">[in] Obiekt do porównania.</span><span class="sxs-lookup"><span data-stu-id="a70a4-111">[in] The object for comparison.</span></span> <span data-ttu-id="a70a4-112">`pcompareTo`musi być prawidłową [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia klasy nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="a70a4-112">`pcompareTo` must be a valid [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="a70a4-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a70a4-113">Return value</span></span>

<span data-ttu-id="a70a4-114">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="a70a4-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a70a4-115">Stała</span><span class="sxs-lookup"><span data-stu-id="a70a4-115">Constant</span></span>  |<span data-ttu-id="a70a4-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="a70a4-116">Value</span></span>  |<span data-ttu-id="a70a4-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a70a4-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="a70a4-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a70a4-118">0x80041001</span></span> | <span data-ttu-id="a70a4-119">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="a70a4-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a70a4-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a70a4-120">0x80041008</span></span> | <span data-ttu-id="a70a4-121">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a70a4-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="a70a4-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="a70a4-122">0x8004101d</span></span> | <span data-ttu-id="a70a4-123">Drugie wywołanie `BeginEnumeration` został utworzony bez wywołania pośredniczące [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a70a4-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a70a4-124">0</span><span class="sxs-lookup"><span data-stu-id="a70a4-124">0</span></span> | <span data-ttu-id="a70a4-125">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a70a4-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="a70a4-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="a70a4-126">0x40003</span></span> | <span data-ttu-id="a70a4-127">Obiekty są różne.</span><span class="sxs-lookup"><span data-stu-id="a70a4-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="a70a4-128">0</span><span class="sxs-lookup"><span data-stu-id="a70a4-128">0</span></span> | <span data-ttu-id="a70a4-129">Obiekty są takie same oparte na flagi porównania.</span><span class="sxs-lookup"><span data-stu-id="a70a4-129">The objects are the same based on the comparison flags.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="a70a4-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a70a4-130">Remarks</span></span>

<span data-ttu-id="a70a4-131">Ta funkcja jest zawijana wywołanie [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="a70a4-131">This function wraps a call to the [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="a70a4-132">Flagi, które mogą być przekazywane jako `lEnumFlags` argumentu są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a70a4-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="a70a4-133">Można określić objętego Porównanie cech, podając bitowe połączenie z następujących flag:</span><span class="sxs-lookup"><span data-stu-id="a70a4-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="a70a4-134">Stała</span><span class="sxs-lookup"><span data-stu-id="a70a4-134">Constant</span></span>  |<span data-ttu-id="a70a4-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="a70a4-135">Value</span></span>  |<span data-ttu-id="a70a4-136">Opis</span><span class="sxs-lookup"><span data-stu-id="a70a4-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="a70a4-137">2</span><span class="sxs-lookup"><span data-stu-id="a70a4-137">2</span></span> | <span data-ttu-id="a70a4-138">Ignoruj źródło (serwer i przestrzeni nazw, które pochodzą z).</span><span class="sxs-lookup"><span data-stu-id="a70a4-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="a70a4-139">1</span><span class="sxs-lookup"><span data-stu-id="a70a4-139">1</span></span> | <span data-ttu-id="a70a4-140">Ignoruj wszystkie Kwalifikatory (łącznie z **klucza** i **dynamiczne**)</span><span class="sxs-lookup"><span data-stu-id="a70a4-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="a70a4-141">4</span><span class="sxs-lookup"><span data-stu-id="a70a4-141">4</span></span> | <span data-ttu-id="a70a4-142">Ignoruj wartości domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="a70a4-142">Ignore default values of properties.</span></span> <span data-ttu-id="a70a4-143">Ta flaga ma zastosowanie tylko do porównania z klas.</span><span class="sxs-lookup"><span data-stu-id="a70a4-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="a70a4-144">0x20</span><span class="sxs-lookup"><span data-stu-id="a70a4-144">0x20</span></span> | <span data-ttu-id="a70a4-145">Ignorowanie kwalifikatora odmian.</span><span class="sxs-lookup"><span data-stu-id="a70a4-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="a70a4-146">Ta flaga nadal uwzględnia kwalifikatory, ale ignoruje różnice wersji, takie jak reguły propagacji i zastępowanie ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a70a4-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="a70a4-147">0x10</span><span class="sxs-lookup"><span data-stu-id="a70a4-147">0x10</span></span> | <span data-ttu-id="a70a4-148">Ignoruj wielkość liter w porównanie wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="a70a4-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="a70a4-149">Dotyczy to zarówno do ciągów i wartości kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="a70a4-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="a70a4-150">Porównanie właściwości i kwalifikator nazwy zawsze jest rozróżniana wielkość liter, niezależnie od tego, czy ta flaga jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a70a4-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="a70a4-151">0x8</span><span class="sxs-lookup"><span data-stu-id="a70a4-151">0x8</span></span> | <span data-ttu-id="a70a4-152">Załóżmy, że są porównywane obiekty są instanes tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="a70a4-152">Assume that the objects being compared are instanes of the same class.</span></span> <span data-ttu-id="a70a4-153">W związku z tym ta flaga porównuje tylko informacje z związane z wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a70a4-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="a70a4-154">Optymalizowanie wydajności przy użyciu tej flagi.</span><span class="sxs-lookup"><span data-stu-id="a70a4-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="a70a4-155">Jeśli obiekty nie znajdują się w tej samej klasy, wyniki są niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="a70a4-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="a70a4-156">Lub możesz określić pojedynczy flagę złożonego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a70a4-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="a70a4-157">Stała</span><span class="sxs-lookup"><span data-stu-id="a70a4-157">Constant</span></span>  |<span data-ttu-id="a70a4-158">Wartość</span><span class="sxs-lookup"><span data-stu-id="a70a4-158">Value</span></span>  |<span data-ttu-id="a70a4-159">Opis</span><span class="sxs-lookup"><span data-stu-id="a70a4-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="a70a4-160">0</span><span class="sxs-lookup"><span data-stu-id="a70a4-160">0</span></span> | <span data-ttu-id="a70a4-161">Należy wziąć pod uwagę wszystkie funkcje do porównania.</span><span class="sxs-lookup"><span data-stu-id="a70a4-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a70a4-162">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a70a4-162">Requirements</span></span>  
 <span data-ttu-id="a70a4-163">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a70a4-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a70a4-164">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a70a4-164">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a70a4-165">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a70a4-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a70a4-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a70a4-166">See also</span></span>  
[<span data-ttu-id="a70a4-167">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="a70a4-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
