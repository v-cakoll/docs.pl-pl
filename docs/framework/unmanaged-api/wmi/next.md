---
title: Next — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja Next pobiera następną właściwość w wyliczeniu.
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
ms.openlocfilehash: 587e085f6fe9f6c19d3605c673cd3bd6f68162f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127380"
---
# <a name="next-function"></a><span data-ttu-id="2e3c2-103">Next — funkcja</span><span class="sxs-lookup"><span data-stu-id="2e3c2-103">Next function</span></span>
<span data-ttu-id="2e3c2-104">Pobiera następną właściwość w wyliczeniu, która rozpoczyna się od wywołania do [beingenumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2e3c2-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="2e3c2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e3c2-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="2e3c2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e3c2-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="2e3c2-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="2e3c2-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="2e3c2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`\
<span data-ttu-id="2e3c2-109">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-109">[in] Reserved.</span></span> <span data-ttu-id="2e3c2-110">Ten parametr musi być równy 0.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-110">This parameter must be 0.</span></span>

`pstrName`\
<span data-ttu-id="2e3c2-111">określoną Nowy `BSTR`, który zawiera nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="2e3c2-112">Można ustawić ten parametr, aby `null`, jeśli nazwa nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`\
<span data-ttu-id="2e3c2-113">określoną `VARIANT` wypełnione wartością właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="2e3c2-114">Można ustawić ten parametr, aby `null`, jeśli wartość nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="2e3c2-115">Jeśli funkcja zwraca kod błędu, `VARIANT` przeszedł do `pVal` nie został zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span>

`pvtType`\
<span data-ttu-id="2e3c2-116">określoną Wskaźnik do zmiennej `CIMTYPE` (`LONG`, do której zostanie umieszczony typ właściwości).</span><span class="sxs-lookup"><span data-stu-id="2e3c2-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="2e3c2-117">Wartość tej właściwości może być `VT_NULL_VARIANT`, w tym przypadku jest to konieczne do określenia rzeczywistego typu właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="2e3c2-118">Ten parametr może być również `null`.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-118">This parameter can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="2e3c2-119">[out] `null`lub wartość, która odbiera informacje w pochodzeniu właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="2e3c2-120">Zapoznaj się z sekcją [spostrzeżenia], aby poznać możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-120">See the [Remarks] section for possible values.</span></span>

## <a name="return-value"></a><span data-ttu-id="2e3c2-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2e3c2-121">Return value</span></span>

<span data-ttu-id="2e3c2-122">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="2e3c2-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2e3c2-123">Stała</span><span class="sxs-lookup"><span data-stu-id="2e3c2-123">Constant</span></span>  |<span data-ttu-id="2e3c2-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="2e3c2-124">Value</span></span>  |<span data-ttu-id="2e3c2-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2e3c2-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="2e3c2-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="2e3c2-126">0x80041001</span></span> | <span data-ttu-id="2e3c2-127">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2e3c2-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2e3c2-128">0x80041008</span></span> | <span data-ttu-id="2e3c2-129">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="2e3c2-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="2e3c2-130">0x8004101d</span></span> | <span data-ttu-id="2e3c2-131">Brak wywołania funkcji [`BeginEnumeration`](beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="2e3c2-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2e3c2-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2e3c2-132">0x80041006</span></span> | <span data-ttu-id="2e3c2-133">Za mało dostępnej pamięci, aby rozpocząć nowe Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="2e3c2-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="2e3c2-134">0x80041015</span></span> | <span data-ttu-id="2e3c2-135">Zdalne wywołanie procedury między bieżącym procesem a programem Windows Management nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-135">The remote procedure call between the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2e3c2-136">0</span><span class="sxs-lookup"><span data-stu-id="2e3c2-136">0</span></span> | <span data-ttu-id="2e3c2-137">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="2e3c2-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="2e3c2-138">0x40005</span></span> | <span data-ttu-id="2e3c2-139">Nie ma więcej właściwości w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-139">There are no more properties in the enumeration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2e3c2-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e3c2-140">Remarks</span></span>

<span data-ttu-id="2e3c2-141">Ta funkcja zawija wywołanie do metody [IWbemClassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) .</span><span class="sxs-lookup"><span data-stu-id="2e3c2-141">This function wraps a call to the [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) method.</span></span>

<span data-ttu-id="2e3c2-142">Ta metoda zwraca również właściwości systemowe.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-142">This method also returns system properties.</span></span>

<span data-ttu-id="2e3c2-143">Jeśli typ podstawowy właściwości jest ścieżką obiektu, datą lub godziną lub innym typem specjalnym, zwracany typ nie zawiera wystarczającej ilości informacji.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="2e3c2-144">Obiekt wywołujący musi sprawdzić `CIMTYPE` dla określonej właściwości, aby określić, czy właściwość jest odwołaniem do obiektu, datą lub godziną lub innym typem specjalnym.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="2e3c2-145">Jeśli `plFlavor` nie `null`, wartość `LONG` otrzymuje informacje o pochodzeniu właściwości w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2e3c2-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="2e3c2-146">Stała</span><span class="sxs-lookup"><span data-stu-id="2e3c2-146">Constant</span></span>  |<span data-ttu-id="2e3c2-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="2e3c2-147">Value</span></span>  |<span data-ttu-id="2e3c2-148">Opis</span><span class="sxs-lookup"><span data-stu-id="2e3c2-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="2e3c2-149">0x40</span><span class="sxs-lookup"><span data-stu-id="2e3c2-149">0x40</span></span> | <span data-ttu-id="2e3c2-150">Właściwość jest standardową właściwością systemu.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="2e3c2-151">0x20</span><span class="sxs-lookup"><span data-stu-id="2e3c2-151">0x20</span></span> | <span data-ttu-id="2e3c2-152">Dla klasy: właściwość jest dziedziczona z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-152">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="2e3c2-153">Dla wystąpienia: właściwość, podczas gdy dziedziczy z klasy nadrzędnej, nie została zmodyfikowana przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="2e3c2-154">0</span><span class="sxs-lookup"><span data-stu-id="2e3c2-154">0</span></span> | <span data-ttu-id="2e3c2-155">Dla klasy: właściwość należy do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-155">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="2e3c2-156">Dla wystąpienia: właściwość jest modyfikowana przez wystąpienie; oznacza to, że została podana wartość lub kwalifikator został dodany lub zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="2e3c2-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="2e3c2-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e3c2-157">Requirements</span></span>

<span data-ttu-id="2e3c2-158">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e3c2-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2e3c2-159">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="2e3c2-159">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="2e3c2-160">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2e3c2-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2e3c2-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e3c2-161">See also</span></span>

- [<span data-ttu-id="2e3c2-162">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="2e3c2-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
