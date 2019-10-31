---
title: QualifierSet_BeginEnumeration — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_BeginEnumeration resetuje moduł wyliczający kwalifikatorów obiektu.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 79edbd876fc9992f088b9adb159e005c735a72cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127327"
---
# <a name="qualifierset_beginenumeration-function"></a><span data-ttu-id="a72d6-103">QualifierSet_BeginEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="a72d6-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="a72d6-104">Resetuje moduł wyliczający kwalifikatorów obiektu na początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a72d6-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a72d6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a72d6-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="a72d6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a72d6-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="a72d6-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="a72d6-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="a72d6-108">podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="a72d6-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="a72d6-109">podczas Bitowa kombinacja flag lub wartości opisanych w sekcji [uwagi](#remarks) , która określa kwalifikatory do uwzględnienia w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="a72d6-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a72d6-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a72d6-110">Return value</span></span>

<span data-ttu-id="a72d6-111">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="a72d6-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a72d6-112">Stała</span><span class="sxs-lookup"><span data-stu-id="a72d6-112">Constant</span></span>  |<span data-ttu-id="a72d6-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="a72d6-113">Value</span></span>  |<span data-ttu-id="a72d6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a72d6-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a72d6-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a72d6-115">0x80041008</span></span> | <span data-ttu-id="a72d6-116">Parametr `lFlags` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a72d6-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="a72d6-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="a72d6-117">0x8004101d</span></span> | <span data-ttu-id="a72d6-118">Drugie wywołanie `QualifierSet_BeginEnumeration` zostało wykonane bez interwencji wywołującego do [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a72d6-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a72d6-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a72d6-119">0x80041006</span></span> | <span data-ttu-id="a72d6-120">Za mało dostępnej pamięci, aby rozpocząć nowe Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="a72d6-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a72d6-121">0</span><span class="sxs-lookup"><span data-stu-id="a72d6-121">0</span></span> | <span data-ttu-id="a72d6-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a72d6-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a72d6-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a72d6-123">Remarks</span></span>

<span data-ttu-id="a72d6-124">Ta funkcja otacza wywołanie metody [IWbemQualifierSet:: beingenumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) .</span><span class="sxs-lookup"><span data-stu-id="a72d6-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="a72d6-125">Aby wyliczyć wszystkie kwalifikatory obiektu, należy wywołać tę metodę przed pierwszym wywołaniem do [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="a72d6-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="a72d6-126">Kolejność, w której są wyliczane kwalifikatory, jest gwarantowany jako niezmienna dla danego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a72d6-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="a72d6-127">Flagi, które mogą być przesyłane jako argument `lEnumFlags`, są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a72d6-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="a72d6-128">Stała</span><span class="sxs-lookup"><span data-stu-id="a72d6-128">Constant</span></span>  |<span data-ttu-id="a72d6-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="a72d6-129">Value</span></span>  |<span data-ttu-id="a72d6-130">Opis</span><span class="sxs-lookup"><span data-stu-id="a72d6-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="a72d6-131">0</span><span class="sxs-lookup"><span data-stu-id="a72d6-131">0</span></span> | <span data-ttu-id="a72d6-132">Zwróć nazwy wszystkich kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="a72d6-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="a72d6-133">0x10</span><span class="sxs-lookup"><span data-stu-id="a72d6-133">0x10</span></span> | <span data-ttu-id="a72d6-134">Zwraca tylko nazwy kwalifikatorów specyficzne dla bieżącej właściwości lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="a72d6-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="a72d6-135">Dla właściwości: zwracają tylko kwalifikatory charakterystyczne dla właściwości (w tym przesłonięć), a nie te kwalifikatory propagowane z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="a72d6-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="a72d6-136">Dla wystąpienia: Zwróć tylko nazwy kwalifikatorów specyficznych dla wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a72d6-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="a72d6-137">Dla klasy: zwracają tylko kwalifikatory charakterystyczne dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="a72d6-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="a72d6-138">0x20</span><span class="sxs-lookup"><span data-stu-id="a72d6-138">0x20</span></span> | <span data-ttu-id="a72d6-139">Zwraca tylko nazwy kwalifikatorów, które zostały przekazane z innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a72d6-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="a72d6-140">Dla właściwości: Zwróć tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="a72d6-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="a72d6-141">Dla wystąpienia: Zwróć tylko te kwalifikatory, które zostały przekazane z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="a72d6-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="a72d6-142">Dla klasy: Zwróć tylko te nazwy kwalifikatorów dziedziczone z klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a72d6-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a72d6-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a72d6-143">Requirements</span></span>

<span data-ttu-id="a72d6-144">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a72d6-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a72d6-145">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="a72d6-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="a72d6-146">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a72d6-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a72d6-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a72d6-147">See also</span></span>

- [<span data-ttu-id="a72d6-148">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="a72d6-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
