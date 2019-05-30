---
title: Funkcja QualifierSet_Put (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_Put zapisuje kwalifikator nazwanych i jego wartość.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a11f19a9b5ebdf491b79c250da7fc5ac3d980b64
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377863"
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="aaa03-103">QualifierSet_Put — funkcja</span><span class="sxs-lookup"><span data-stu-id="aaa03-103">QualifierSet_Put function</span></span>

<span data-ttu-id="aaa03-104">Zapisuje kwalifikator o nazwie i wartości.</span><span class="sxs-lookup"><span data-stu-id="aaa03-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="aaa03-105">Nowy kwalifikator zastępuje poprzednią wartość taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="aaa03-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="aaa03-106">Jeśli kwalifikatora nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="aaa03-106">If the qualifier does not exist, it is created.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="aaa03-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="aaa03-107">Syntax</span></span>

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="aaa03-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="aaa03-108">Parameters</span></span>

`vFunc`\
<span data-ttu-id="aaa03-109">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="aaa03-109">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="aaa03-110">[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="aaa03-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`\
<span data-ttu-id="aaa03-111">[in] Nazwa kwalifikatora do zapisania.</span><span class="sxs-lookup"><span data-stu-id="aaa03-111">[in] The name of the qualifier to write.</span></span>

`pVal`\
<span data-ttu-id="aaa03-112">[in] Wskaźnik do prawidłowego `VARIANT` zawierający kwalifikator do zapisania.</span><span class="sxs-lookup"><span data-stu-id="aaa03-112">[in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="aaa03-113">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="aaa03-113">This parameter cannot be `null`.</span></span>

`lFlavor`\
<span data-ttu-id="aaa03-114">[in] Jeden z następujących stałych, które definiuje właściwą kwalifikator odpowiednią dla tego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="aaa03-114">[in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="aaa03-115">Wartość domyślna to `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="aaa03-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="aaa03-116">Stała</span><span class="sxs-lookup"><span data-stu-id="aaa03-116">Constant</span></span>  |<span data-ttu-id="aaa03-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="aaa03-117">Value</span></span>  |<span data-ttu-id="aaa03-118">Opis</span><span class="sxs-lookup"><span data-stu-id="aaa03-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="aaa03-119">0</span><span class="sxs-lookup"><span data-stu-id="aaa03-119">0</span></span> | <span data-ttu-id="aaa03-120">Kwalifikator może zostać przesłonięta w pochodnej klasy lub wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="aaa03-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="aaa03-121">**Jest to wartość domyślna.**</span><span class="sxs-lookup"><span data-stu-id="aaa03-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="aaa03-122">1</span><span class="sxs-lookup"><span data-stu-id="aaa03-122">1</span></span> | <span data-ttu-id="aaa03-123">Kwalifikator jest propagowana do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="aaa03-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="aaa03-124">2</span><span class="sxs-lookup"><span data-stu-id="aaa03-124">2</span></span> | <span data-ttu-id="aaa03-125">Kwalifikator jest propagowana do klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="aaa03-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="aaa03-126">0x10</span><span class="sxs-lookup"><span data-stu-id="aaa03-126">0x10</span></span> | <span data-ttu-id="aaa03-127">Nie można zastąpić kwalifikator w klasie pochodnej lub wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="aaa03-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="aaa03-128">0x80</span><span class="sxs-lookup"><span data-stu-id="aaa03-128">0x80</span></span> | <span data-ttu-id="aaa03-129">Kwalifikator jest zlokalizowana.</span><span class="sxs-lookup"><span data-stu-id="aaa03-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="aaa03-130">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aaa03-130">Return value</span></span>

<span data-ttu-id="aaa03-131">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="aaa03-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="aaa03-132">Stała</span><span class="sxs-lookup"><span data-stu-id="aaa03-132">Constant</span></span>  |<span data-ttu-id="aaa03-133">Wartość</span><span class="sxs-lookup"><span data-stu-id="aaa03-133">Value</span></span>  |<span data-ttu-id="aaa03-134">Opis</span><span class="sxs-lookup"><span data-stu-id="aaa03-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="aaa03-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="aaa03-135">0x8004101f</span></span> | <span data-ttu-id="aaa03-136">Wystąpił niedozwolona próba określenia **klucz** kwalifikator dla właściwości, która nie może być kluczem.</span><span class="sxs-lookup"><span data-stu-id="aaa03-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="aaa03-137">Klucze są określone w definicji klasy dla obiektu i nie może zostać zmieniona na podstawie poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="aaa03-137">The keys are specified in the class definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="aaa03-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="aaa03-138">0x80041008</span></span> | <span data-ttu-id="aaa03-139">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="aaa03-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="aaa03-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="aaa03-140">0x80041029</span></span> | <span data-ttu-id="aaa03-141">`pVal` Parametr nie jest dozwolonym typem kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="aaa03-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="aaa03-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="aaa03-142">0x8004101a</span></span> | <span data-ttu-id="aaa03-143">Nie jest możliwe do wywołania `QualifierSet_Put` metody kwalifikator, ponieważ obiekt-właściciel nie zezwala na zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="aaa03-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="aaa03-144">0</span><span class="sxs-lookup"><span data-stu-id="aaa03-144">0</span></span> | <span data-ttu-id="aaa03-145">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aaa03-145">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="aaa03-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aaa03-146">Remarks</span></span>

<span data-ttu-id="aaa03-147">Ta funkcja zawija wywołanie do [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) metody.</span><span class="sxs-lookup"><span data-stu-id="aaa03-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="aaa03-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aaa03-148">Requirements</span></span>

<span data-ttu-id="aaa03-149">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaa03-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="aaa03-150">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="aaa03-150">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="aaa03-151">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa03-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="aaa03-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aaa03-152">See also</span></span>

- [<span data-ttu-id="aaa03-153">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="aaa03-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
