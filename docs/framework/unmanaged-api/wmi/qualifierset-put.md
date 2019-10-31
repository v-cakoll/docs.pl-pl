---
title: QualifierSet_Put — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_Put zapisuje nazwany kwalifikator i jego wartość.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a35025c6d16455a51b7b22d822ba77337ddd894a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120233"
---
# <a name="qualifierset_put-function"></a><span data-ttu-id="7271e-103">QualifierSet_Put, funkcja</span><span class="sxs-lookup"><span data-stu-id="7271e-103">QualifierSet_Put function</span></span>

<span data-ttu-id="7271e-104">Zapisuje nazwany kwalifikator i wartość.</span><span class="sxs-lookup"><span data-stu-id="7271e-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="7271e-105">Nowy kwalifikator zastępuje poprzednią wartość tej samej nazwy.</span><span class="sxs-lookup"><span data-stu-id="7271e-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="7271e-106">Jeśli kwalifikator nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="7271e-106">If the qualifier does not exist, it is created.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="7271e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7271e-107">Syntax</span></span>

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="7271e-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="7271e-108">Parameters</span></span>

`vFunc`\
<span data-ttu-id="7271e-109">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="7271e-109">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="7271e-110">podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="7271e-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`\
<span data-ttu-id="7271e-111">podczas Nazwa kwalifikatora do zapisu.</span><span class="sxs-lookup"><span data-stu-id="7271e-111">[in] The name of the qualifier to write.</span></span>

`pVal`\
<span data-ttu-id="7271e-112">podczas Wskaźnik do prawidłowego `VARIANT`, który zawiera kwalifikator do zapisu.</span><span class="sxs-lookup"><span data-stu-id="7271e-112">[in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="7271e-113">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="7271e-113">This parameter cannot be `null`.</span></span>

`lFlavor`\
<span data-ttu-id="7271e-114">podczas Jedna z następujących stałych, która definiuje odpowiednie typy kwalifikatorów dla tego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="7271e-114">[in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="7271e-115">Wartość domyślna to `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="7271e-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="7271e-116">Stała</span><span class="sxs-lookup"><span data-stu-id="7271e-116">Constant</span></span>  |<span data-ttu-id="7271e-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="7271e-117">Value</span></span>  |<span data-ttu-id="7271e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="7271e-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="7271e-119">0</span><span class="sxs-lookup"><span data-stu-id="7271e-119">0</span></span> | <span data-ttu-id="7271e-120">Kwalifikator można zastąpić w klasie pochodnej lub w wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="7271e-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="7271e-121">**Jest to wartość domyślna.**</span><span class="sxs-lookup"><span data-stu-id="7271e-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="7271e-122">1</span><span class="sxs-lookup"><span data-stu-id="7271e-122">1</span></span> | <span data-ttu-id="7271e-123">Kwalifikator jest propagowany do wystąpień.</span><span class="sxs-lookup"><span data-stu-id="7271e-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="7271e-124">2</span><span class="sxs-lookup"><span data-stu-id="7271e-124">2</span></span> | <span data-ttu-id="7271e-125">Kwalifikator jest propagowany do klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="7271e-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="7271e-126">0x10</span><span class="sxs-lookup"><span data-stu-id="7271e-126">0x10</span></span> | <span data-ttu-id="7271e-127">Kwalifikator nie może zostać zastąpiony w klasie pochodnej lub w wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="7271e-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="7271e-128">0x80</span><span class="sxs-lookup"><span data-stu-id="7271e-128">0x80</span></span> | <span data-ttu-id="7271e-129">Kwalifikator jest zlokalizowany.</span><span class="sxs-lookup"><span data-stu-id="7271e-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="7271e-130">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7271e-130">Return value</span></span>

<span data-ttu-id="7271e-131">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="7271e-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7271e-132">Stała</span><span class="sxs-lookup"><span data-stu-id="7271e-132">Constant</span></span>  |<span data-ttu-id="7271e-133">Wartość</span><span class="sxs-lookup"><span data-stu-id="7271e-133">Value</span></span>  |<span data-ttu-id="7271e-134">Opis</span><span class="sxs-lookup"><span data-stu-id="7271e-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="7271e-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="7271e-135">0x8004101f</span></span> | <span data-ttu-id="7271e-136">Wystąpiła niedozwolona próba określenia kwalifikatora **klucza** dla właściwości, która nie może być kluczem.</span><span class="sxs-lookup"><span data-stu-id="7271e-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="7271e-137">Klucze są określone w definicji klasy dla obiektu i nie można ich zmienić dla poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="7271e-137">The keys are specified in the class definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7271e-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7271e-138">0x80041008</span></span> | <span data-ttu-id="7271e-139">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="7271e-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="7271e-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="7271e-140">0x80041029</span></span> | <span data-ttu-id="7271e-141">Parametr `pVal` nie jest dozwolonym typem kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="7271e-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="7271e-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="7271e-142">0x8004101a</span></span> | <span data-ttu-id="7271e-143">Nie można wywołać metody `QualifierSet_Put` w kwalifikatorze, ponieważ obiekt będący właścicielem nie zezwala na zastępowanie.</span><span class="sxs-lookup"><span data-stu-id="7271e-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="7271e-144">0</span><span class="sxs-lookup"><span data-stu-id="7271e-144">0</span></span> | <span data-ttu-id="7271e-145">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7271e-145">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="7271e-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7271e-146">Remarks</span></span>

<span data-ttu-id="7271e-147">Ta funkcja otacza wywołanie metody [IWbemQualifierSet::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) .</span><span class="sxs-lookup"><span data-stu-id="7271e-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7271e-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7271e-148">Requirements</span></span>

<span data-ttu-id="7271e-149">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7271e-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7271e-150">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="7271e-150">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="7271e-151">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7271e-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7271e-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7271e-152">See also</span></span>

- [<span data-ttu-id="7271e-153">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="7271e-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
