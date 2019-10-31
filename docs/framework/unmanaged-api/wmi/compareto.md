---
title: CompareTo — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja CompareTo porównuje obiekt z innym obiektem WMI.
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
ms.openlocfilehash: 0d210795016cd2e0179b902a224ca0c62f4ac01f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128700"
---
# <a name="compareto-function"></a><span data-ttu-id="e6274-103">CompareTo, funkcja</span><span class="sxs-lookup"><span data-stu-id="e6274-103">CompareTo function</span></span>

<span data-ttu-id="e6274-104">Porównuje obiekt z innym obiektem zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="e6274-104">Compares an object to another Windows management object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e6274-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6274-105">Syntax</span></span>

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a><span data-ttu-id="e6274-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6274-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="e6274-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="e6274-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="e6274-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="e6274-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`\
<span data-ttu-id="e6274-109">podczas Bitowa kombinacja flag, które określają właściwości obiektu, które należy wziąć pod uwagę w porównaniu z porównaniem.</span><span class="sxs-lookup"><span data-stu-id="e6274-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="e6274-110">Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="e6274-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`\
<span data-ttu-id="e6274-111">podczas Obiekt do porównania.</span><span class="sxs-lookup"><span data-stu-id="e6274-111">[in] The object for comparison.</span></span> <span data-ttu-id="e6274-112">`pCompareTo` musi być prawidłowym wystąpieniem [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ; nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="e6274-112">`pCompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="e6274-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e6274-113">Return value</span></span>

<span data-ttu-id="e6274-114">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="e6274-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e6274-115">Stała</span><span class="sxs-lookup"><span data-stu-id="e6274-115">Constant</span></span>  |<span data-ttu-id="e6274-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="e6274-116">Value</span></span>  |<span data-ttu-id="e6274-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e6274-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="e6274-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e6274-118">0x80041001</span></span> | <span data-ttu-id="e6274-119">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="e6274-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e6274-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e6274-120">0x80041008</span></span> | <span data-ttu-id="e6274-121">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e6274-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="e6274-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="e6274-122">0x8004101d</span></span> | <span data-ttu-id="e6274-123">Drugie wywołanie `BeginEnumeration` zostało wykonane bez interwencji wywołującego do [`EndEnumeration`](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e6274-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="e6274-124">0</span><span class="sxs-lookup"><span data-stu-id="e6274-124">0</span></span> | <span data-ttu-id="e6274-125">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e6274-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="e6274-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="e6274-126">0x40003</span></span> | <span data-ttu-id="e6274-127">Obiekty są różne.</span><span class="sxs-lookup"><span data-stu-id="e6274-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="e6274-128">0</span><span class="sxs-lookup"><span data-stu-id="e6274-128">0</span></span> | <span data-ttu-id="e6274-129">Obiekty są takie same, w zależności od flag porównania.</span><span class="sxs-lookup"><span data-stu-id="e6274-129">The objects are the same based on the comparison flags.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e6274-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6274-130">Remarks</span></span>

<span data-ttu-id="e6274-131">Ta funkcja otacza wywołanie metody [IWbemClassObject:: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) .</span><span class="sxs-lookup"><span data-stu-id="e6274-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="e6274-132">Flagi, które mogą być przesyłane jako argument `lEnumFlags`, są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e6274-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="e6274-133">Można określić poszczególne cechy, które są wykorzystywane w porównaniu, określając bitową kombinację następujących flag:</span><span class="sxs-lookup"><span data-stu-id="e6274-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="e6274-134">Stała</span><span class="sxs-lookup"><span data-stu-id="e6274-134">Constant</span></span>  |<span data-ttu-id="e6274-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="e6274-135">Value</span></span>  |<span data-ttu-id="e6274-136">Opis</span><span class="sxs-lookup"><span data-stu-id="e6274-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="e6274-137">2</span><span class="sxs-lookup"><span data-stu-id="e6274-137">2</span></span> | <span data-ttu-id="e6274-138">Zignoruj źródło (serwer i przestrzeń nazw, z których pochodzą).</span><span class="sxs-lookup"><span data-stu-id="e6274-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="e6274-139">1</span><span class="sxs-lookup"><span data-stu-id="e6274-139">1</span></span> | <span data-ttu-id="e6274-140">Ignoruj wszystkie kwalifikatory (w tym **klucz** i **dynamiczny**)</span><span class="sxs-lookup"><span data-stu-id="e6274-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="e6274-141">4</span><span class="sxs-lookup"><span data-stu-id="e6274-141">4</span></span> | <span data-ttu-id="e6274-142">Ignoruj wartości domyślne właściwości.</span><span class="sxs-lookup"><span data-stu-id="e6274-142">Ignore default values of properties.</span></span> <span data-ttu-id="e6274-143">Ta flaga ma zastosowanie tylko do porównania klas.</span><span class="sxs-lookup"><span data-stu-id="e6274-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="e6274-144">0x20</span><span class="sxs-lookup"><span data-stu-id="e6274-144">0x20</span></span> | <span data-ttu-id="e6274-145">Ignoruj typy kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="e6274-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="e6274-146">Ta flaga nadal przyjmuje kwalifikatory do konta, ale ignoruje różnice wersji, takie jak reguły propagacji i ograniczenia przesłonięć.</span><span class="sxs-lookup"><span data-stu-id="e6274-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="e6274-147">0x10</span><span class="sxs-lookup"><span data-stu-id="e6274-147">0x10</span></span> | <span data-ttu-id="e6274-148">Ignoruj wielkość liter podczas porównywania wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="e6274-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="e6274-149">Dotyczy to zarówno ciągów, jak i wartości kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="e6274-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="e6274-150">Porównanie nazw właściwości i kwalifikatora jest zawsze rozróżniana wielkość liter niezależnie od tego, czy flaga jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e6274-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="e6274-151">0x8</span><span class="sxs-lookup"><span data-stu-id="e6274-151">0x8</span></span> | <span data-ttu-id="e6274-152">Załóżmy, że porównywane obiekty są wystąpieniami tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="e6274-152">Assume that the objects being compared are instances of the same class.</span></span> <span data-ttu-id="e6274-153">W związku z tym flaga porównuje tylko informacje związane z wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="e6274-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="e6274-154">Użyj tych flag, aby zoptymalizować wydajność.</span><span class="sxs-lookup"><span data-stu-id="e6274-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="e6274-155">Jeśli obiekty nie należą do tej samej klasy, wyniki są niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="e6274-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="e6274-156">Lub można określić pojedynczą flagę złożoną w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e6274-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="e6274-157">Stała</span><span class="sxs-lookup"><span data-stu-id="e6274-157">Constant</span></span>  |<span data-ttu-id="e6274-158">Wartość</span><span class="sxs-lookup"><span data-stu-id="e6274-158">Value</span></span>  |<span data-ttu-id="e6274-159">Opis</span><span class="sxs-lookup"><span data-stu-id="e6274-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="e6274-160">0</span><span class="sxs-lookup"><span data-stu-id="e6274-160">0</span></span> | <span data-ttu-id="e6274-161">Należy wziąć pod uwagę wszystkie funkcje w porównaniu.</span><span class="sxs-lookup"><span data-stu-id="e6274-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="e6274-162">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e6274-162">Requirements</span></span>

<span data-ttu-id="e6274-163">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6274-163">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e6274-164">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="e6274-164">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="e6274-165">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e6274-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e6274-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6274-166">See also</span></span>

- [<span data-ttu-id="e6274-167">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="e6274-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
