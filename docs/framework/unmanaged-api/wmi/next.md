---
title: Użycie funkcji Next (niezarządzany wykaz interfejsów API)
description: Następna funkcja pobiera następną właściwość w wyliczeniu.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 240544330fa352cbfdc01944e4be6bcad28dc96f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373204"
---
# <a name="next-function"></a><span data-ttu-id="2fd19-103">Użycie funkcji Next</span><span class="sxs-lookup"><span data-stu-id="2fd19-103">Next function</span></span>
<span data-ttu-id="2fd19-104">Pobiera następną właściwość w wyliczenie, które zaczyna się od wywołania [Beingenumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2fd19-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="2fd19-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fd19-105">Syntax</span></span>

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="2fd19-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fd19-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="2fd19-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="2fd19-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="2fd19-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2fd19-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`\
<span data-ttu-id="2fd19-109">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="2fd19-109">[in] Reserved.</span></span> <span data-ttu-id="2fd19-110">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="2fd19-110">This parameter must be 0.</span></span>

`pstrName`\
<span data-ttu-id="2fd19-111">[out] Nowy `BSTR` zawierający nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="2fd19-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="2fd19-112">Ten parametr zostanie ustawiony na `null` Jeśli nazwa nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="2fd19-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`\
<span data-ttu-id="2fd19-113">[out] A `VARIANT` wypełnione wartością właściwości.</span><span class="sxs-lookup"><span data-stu-id="2fd19-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="2fd19-114">Ten parametr zostanie ustawiony na `null` Jeśli wartość nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="2fd19-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="2fd19-115">Jeśli funkcja zwraca kod błędu: `VARIANT` przekazany do `pVal` się po lewej stronie w niezmienionej postaci.</span><span class="sxs-lookup"><span data-stu-id="2fd19-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span>

`pvtType`\
<span data-ttu-id="2fd19-116">[out] Wskaźnik do `CIMTYPE` zmiennej ( `LONG` do jest umieszczany typ właściwości).</span><span class="sxs-lookup"><span data-stu-id="2fd19-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="2fd19-117">Wartość tej właściwości może być `VT_NULL_VARIANT`, w którym to przypadku należy określić rzeczywisty typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="2fd19-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="2fd19-118">Ten parametr może być również `null`.</span><span class="sxs-lookup"><span data-stu-id="2fd19-118">This parameter can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="2fd19-119">[out] `null`, lub wartość, która otrzymuje informacje o pochodzeniu właściwości.</span><span class="sxs-lookup"><span data-stu-id="2fd19-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="2fd19-120">W sekcji [Uwagi] możliwych wartości.</span><span class="sxs-lookup"><span data-stu-id="2fd19-120">See the [Remarks] section for possible values.</span></span>

## <a name="return-value"></a><span data-ttu-id="2fd19-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2fd19-121">Return value</span></span>

<span data-ttu-id="2fd19-122">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="2fd19-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2fd19-123">Stała</span><span class="sxs-lookup"><span data-stu-id="2fd19-123">Constant</span></span>  |<span data-ttu-id="2fd19-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="2fd19-124">Value</span></span>  |<span data-ttu-id="2fd19-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2fd19-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="2fd19-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="2fd19-126">0x80041001</span></span> | <span data-ttu-id="2fd19-127">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="2fd19-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2fd19-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2fd19-128">0x80041008</span></span> | <span data-ttu-id="2fd19-129">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2fd19-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="2fd19-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="2fd19-130">0x8004101d</span></span> | <span data-ttu-id="2fd19-131">Wystąpił brak wywołania [ `BeginEnumeration` ](beginenumeration.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="2fd19-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2fd19-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2fd19-132">0x80041006</span></span> | <span data-ttu-id="2fd19-133">Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="2fd19-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="2fd19-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="2fd19-134">0x80041015</span></span> | <span data-ttu-id="2fd19-135">Zdalne wywołanie procedury między bieżącym procesem a usługą Windows Management nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="2fd19-135">The remote procedure call between the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2fd19-136">0</span><span class="sxs-lookup"><span data-stu-id="2fd19-136">0</span></span> | <span data-ttu-id="2fd19-137">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2fd19-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="2fd19-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="2fd19-138">0x40005</span></span> | <span data-ttu-id="2fd19-139">Nie ma żadnych więcej właściwości w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="2fd19-139">There are no more properties in the enumeration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2fd19-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2fd19-140">Remarks</span></span>

<span data-ttu-id="2fd19-141">Ta funkcja zawija wywołanie do [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) metody.</span><span class="sxs-lookup"><span data-stu-id="2fd19-141">This function wraps a call to the [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) method.</span></span>

<span data-ttu-id="2fd19-142">Ta metoda zwraca również wartość właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="2fd19-142">This method also returns system properties.</span></span>

<span data-ttu-id="2fd19-143">W przypadku ścieżki obiektu, daty lub godziny lub innego specjalny typ podstawowy typu właściwości zwracany typ nie zawiera wystarczającej ilości informacji.</span><span class="sxs-lookup"><span data-stu-id="2fd19-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="2fd19-144">Obiekt wywołujący należy zbadać `CIMTYPE` dla określonej właściwości w celu ustalenia, czy właściwość jest odwołanie do obiektu, daty lub godziny lub innego typu specjalne.</span><span class="sxs-lookup"><span data-stu-id="2fd19-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="2fd19-145">Jeśli `plFlavor` nie `null`, `LONG` wartość otrzymuje informacje na temat źródła właściwości, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2fd19-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="2fd19-146">Stała</span><span class="sxs-lookup"><span data-stu-id="2fd19-146">Constant</span></span>  |<span data-ttu-id="2fd19-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="2fd19-147">Value</span></span>  |<span data-ttu-id="2fd19-148">Opis</span><span class="sxs-lookup"><span data-stu-id="2fd19-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="2fd19-149">0x40</span><span class="sxs-lookup"><span data-stu-id="2fd19-149">0x40</span></span> | <span data-ttu-id="2fd19-150">Właściwość jest właściwością standardowych systemowych.</span><span class="sxs-lookup"><span data-stu-id="2fd19-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="2fd19-151">0x20</span><span class="sxs-lookup"><span data-stu-id="2fd19-151">0x20</span></span> | <span data-ttu-id="2fd19-152">Dla klasy: Właściwość jest dziedziczona z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2fd19-152">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="2fd19-153">W przypadku wystąpienia: Właściwości, podczas gdy dziedziczone z klasy nadrzędnej, nie został zmodyfikowany przez to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="2fd19-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="2fd19-154">0</span><span class="sxs-lookup"><span data-stu-id="2fd19-154">0</span></span> | <span data-ttu-id="2fd19-155">Dla klasy: Właściwość należy do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="2fd19-155">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="2fd19-156">W przypadku wystąpienia: Ta właściwość jest modyfikowana przez wystąpienie; oznacza to, że podano wartość lub kwalifikator został dodany lub zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="2fd19-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="2fd19-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2fd19-157">Requirements</span></span>

<span data-ttu-id="2fd19-158">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fd19-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="2fd19-159">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2fd19-159">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="2fd19-160">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2fd19-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2fd19-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2fd19-161">See also</span></span>

- [<span data-ttu-id="2fd19-162">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="2fd19-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)