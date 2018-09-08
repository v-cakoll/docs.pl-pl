---
title: Funkcja CompareTo (niezarządzany wykaz interfejsów API)
description: Funkcja CompareTo porównuje obiekt do innego obiektu WMI.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bde25ae7455dd7fe35fe1a0a43bb2a6b560c0e3e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184230"
---
# <a name="compareto-function"></a><span data-ttu-id="8a8d5-103">Funkcja CompareTo</span><span class="sxs-lookup"><span data-stu-id="8a8d5-103">CompareTo function</span></span>
<span data-ttu-id="8a8d5-104">Porównuje obiekt do innego obiektu zarządzania Windows.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-104">Compares an object to another Windows management object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="8a8d5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a8d5-105">Syntax</span></span>  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a><span data-ttu-id="8a8d5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a8d5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8a8d5-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8a8d5-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`  
<span data-ttu-id="8a8d5-109">[in] Bitowa kombinacja flagi określające właściwości obiektu do rozważenia do porównania.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="8a8d5-110">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`  

<span data-ttu-id="8a8d5-111">[in] Obiekt do porównania.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-111">[in] The object for comparison.</span></span> <span data-ttu-id="8a8d5-112">`pcompareTo` musi być prawidłowym [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia klasy nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-112">`pcompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="8a8d5-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8a8d5-113">Return value</span></span>

<span data-ttu-id="8a8d5-114">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="8a8d5-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8a8d5-115">Stała</span><span class="sxs-lookup"><span data-stu-id="8a8d5-115">Constant</span></span>  |<span data-ttu-id="8a8d5-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="8a8d5-116">Value</span></span>  |<span data-ttu-id="8a8d5-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8a8d5-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="8a8d5-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8a8d5-118">0x80041001</span></span> | <span data-ttu-id="8a8d5-119">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8a8d5-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8a8d5-120">0x80041008</span></span> | <span data-ttu-id="8a8d5-121">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="8a8d5-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="8a8d5-122">0x8004101d</span></span> | <span data-ttu-id="8a8d5-123">Drugie wywołanie `BeginEnumeration` został utworzony bez interwencyjnego wywołania [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8a8d5-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="8a8d5-124">0</span><span class="sxs-lookup"><span data-stu-id="8a8d5-124">0</span></span> | <span data-ttu-id="8a8d5-125">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="8a8d5-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="8a8d5-126">0x40003</span></span> | <span data-ttu-id="8a8d5-127">Obiekty są różne.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="8a8d5-128">0</span><span class="sxs-lookup"><span data-stu-id="8a8d5-128">0</span></span> | <span data-ttu-id="8a8d5-129">Obiekty są takie same oparte na porównanie flag.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-129">The objects are the same based on the comparison flags.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="8a8d5-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a8d5-130">Remarks</span></span>

<span data-ttu-id="8a8d5-131">Ta funkcja zawija wywołanie do [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) metody.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="8a8d5-132">Flagi, które mogą być przekazywane jako `lEnumFlags` argument są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="8a8d5-133">Należy określić cech zaangażowanych w porównaniu, określając bitową kombinację następujących flag:</span><span class="sxs-lookup"><span data-stu-id="8a8d5-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="8a8d5-134">Stała</span><span class="sxs-lookup"><span data-stu-id="8a8d5-134">Constant</span></span>  |<span data-ttu-id="8a8d5-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="8a8d5-135">Value</span></span>  |<span data-ttu-id="8a8d5-136">Opis</span><span class="sxs-lookup"><span data-stu-id="8a8d5-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="8a8d5-137">2</span><span class="sxs-lookup"><span data-stu-id="8a8d5-137">2</span></span> | <span data-ttu-id="8a8d5-138">Ignoruj źródło (serwer i przestrzeni nazw, które pochodzą z).</span><span class="sxs-lookup"><span data-stu-id="8a8d5-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="8a8d5-139">1</span><span class="sxs-lookup"><span data-stu-id="8a8d5-139">1</span></span> | <span data-ttu-id="8a8d5-140">Ignoruj wszystkie Kwalifikatory (w tym **klucz** i **dynamiczne**)</span><span class="sxs-lookup"><span data-stu-id="8a8d5-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="8a8d5-141">4</span><span class="sxs-lookup"><span data-stu-id="8a8d5-141">4</span></span> | <span data-ttu-id="8a8d5-142">Pomiń domyślne wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-142">Ignore default values of properties.</span></span> <span data-ttu-id="8a8d5-143">Ta flaga ma zastosowanie tylko do porównania z klas.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="8a8d5-144">0x20</span><span class="sxs-lookup"><span data-stu-id="8a8d5-144">0x20</span></span> | <span data-ttu-id="8a8d5-145">Ignorowanie kwalifikatora odmian.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="8a8d5-146">Ta flaga nadal uwzględnia kwalifikatorów, ale ignoruje różnice wersji, takich jak zasady propagacji i zastąpić ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="8a8d5-147">0x10</span><span class="sxs-lookup"><span data-stu-id="8a8d5-147">0x10</span></span> | <span data-ttu-id="8a8d5-148">Ignoruj wielkość liter przy porównywaniu wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="8a8d5-149">Dotyczy to zarówno do ciągów i wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="8a8d5-150">Porównanie nazw właściwości i kwalifikator zawsze jest rozróżniana wielkość liter, niezależnie od tego, czy ta flaga jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="8a8d5-151">0x8</span><span class="sxs-lookup"><span data-stu-id="8a8d5-151">0x8</span></span> | <span data-ttu-id="8a8d5-152">Przyjęto założenie, czy obiekty są porównywane są instanes tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-152">Assume that the objects being compared are instanes of the same class.</span></span> <span data-ttu-id="8a8d5-153">W związku z tym ta flaga porównuje dotyczącego wystąpienia wyłącznie informacyjne.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="8a8d5-154">Użyj tej flagi w celu zoptymalizowania wydajności.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="8a8d5-155">Jeśli obiekty nie są tego samego rodzaju, wyniki są niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="8a8d5-156">Lub można określić pojedynczej flagi złożonego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8a8d5-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="8a8d5-157">Stała</span><span class="sxs-lookup"><span data-stu-id="8a8d5-157">Constant</span></span>  |<span data-ttu-id="8a8d5-158">Wartość</span><span class="sxs-lookup"><span data-stu-id="8a8d5-158">Value</span></span>  |<span data-ttu-id="8a8d5-159">Opis</span><span class="sxs-lookup"><span data-stu-id="8a8d5-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="8a8d5-160">0</span><span class="sxs-lookup"><span data-stu-id="8a8d5-160">0</span></span> | <span data-ttu-id="8a8d5-161">Należy wziąć pod uwagę wszystkie funkcje do porównania.</span><span class="sxs-lookup"><span data-stu-id="8a8d5-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="8a8d5-162">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a8d5-162">Requirements</span></span>  
 <span data-ttu-id="8a8d5-163">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a8d5-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a8d5-164">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8a8d5-164">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8a8d5-165">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8a8d5-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a8d5-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a8d5-166">See also</span></span>  
[<span data-ttu-id="8a8d5-167">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="8a8d5-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
