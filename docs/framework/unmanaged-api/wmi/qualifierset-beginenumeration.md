---
title: Funkcja QualifierSet_BeginEnumeration (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_BeginEnumeration resetuje moduł wyliczający kwalifikatory obiektu.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663434d3e3d44dc0c406e71592651493bd8f8dc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375418"
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="5ed96-103">QualifierSet_BeginEnumeration — funkcja</span><span class="sxs-lookup"><span data-stu-id="5ed96-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="5ed96-104">Resetuje moduł wyliczający kwalifikatory obiektu na początku tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5ed96-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="5ed96-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ed96-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="5ed96-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ed96-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="5ed96-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="5ed96-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="5ed96-108">[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5ed96-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="5ed96-109">[in] Bitowa kombinacja wartości opisanych w lub flag [uwagi](#remarks) sekcja, która określa kwalifikatory do uwzględnienia w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="5ed96-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="5ed96-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5ed96-110">Return value</span></span>

<span data-ttu-id="5ed96-111">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="5ed96-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5ed96-112">Stała</span><span class="sxs-lookup"><span data-stu-id="5ed96-112">Constant</span></span>  |<span data-ttu-id="5ed96-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="5ed96-113">Value</span></span>  |<span data-ttu-id="5ed96-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5ed96-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5ed96-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5ed96-115">0x80041008</span></span> | <span data-ttu-id="5ed96-116">`lFlags` Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="5ed96-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="5ed96-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="5ed96-117">0x8004101d</span></span> | <span data-ttu-id="5ed96-118">Drugie wywołanie `QualifierSet_BeginEnumeration` został utworzony bez interwencyjnego wywołania [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="5ed96-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5ed96-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5ed96-119">0x80041006</span></span> | <span data-ttu-id="5ed96-120">Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="5ed96-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5ed96-121">0</span><span class="sxs-lookup"><span data-stu-id="5ed96-121">0</span></span> | <span data-ttu-id="5ed96-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5ed96-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="5ed96-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ed96-123">Remarks</span></span>

<span data-ttu-id="5ed96-124">Ta funkcja zawija wywołanie do [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) metody.</span><span class="sxs-lookup"><span data-stu-id="5ed96-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="5ed96-125">Wyliczono wszystkie kwalifikatory dla obiektu, ta metoda musi zostać wywołana przed pierwszym wywołaniu [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="5ed96-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="5ed96-126">Kolejność, w którym są wyliczane kwalifikatory może być inwariantny dla danego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5ed96-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="5ed96-127">Flagi, które mogą być przekazywane jako `lEnumFlags` argument są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5ed96-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="5ed96-128">Stała</span><span class="sxs-lookup"><span data-stu-id="5ed96-128">Constant</span></span>  |<span data-ttu-id="5ed96-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="5ed96-129">Value</span></span>  |<span data-ttu-id="5ed96-130">Opis</span><span class="sxs-lookup"><span data-stu-id="5ed96-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="5ed96-131">0</span><span class="sxs-lookup"><span data-stu-id="5ed96-131">0</span></span> | <span data-ttu-id="5ed96-132">Zwraca nazwy wszystkich kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="5ed96-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="5ed96-133">0x10</span><span class="sxs-lookup"><span data-stu-id="5ed96-133">0x10</span></span> | <span data-ttu-id="5ed96-134">Zwróć tylko nazwy kwalifikatory określonych do bieżącej właściwości lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="5ed96-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="5ed96-135">Dla właściwości: Zwróć tylko kwalifikatory określone dla właściwości (w tym zastąpień), a nie kwalifikatory propagowane z poziomu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="5ed96-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="5ed96-136">W przypadku wystąpienia: Zwróć tylko nazwy kwalifikator danego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5ed96-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="5ed96-137">Dla klasy: Zwróć tylko kwalifikatory określonej klasy pochodnej jest.</span><span class="sxs-lookup"><span data-stu-id="5ed96-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="5ed96-138">0x20</span><span class="sxs-lookup"><span data-stu-id="5ed96-138">0x20</span></span> | <span data-ttu-id="5ed96-139">Zwróć tylko nazwy kwalifikatory propagowane z innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5ed96-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="5ed96-140">Dla właściwości: Zwróć tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ed96-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="5ed96-141">W przypadku wystąpienia: Zwróć tylko tych kwalifikatory propagowane z poziomu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="5ed96-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="5ed96-142">Dla klasy: Zwróć tylko nazwy kwalifikator dziedziczone z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="5ed96-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="5ed96-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ed96-143">Requirements</span></span>

<span data-ttu-id="5ed96-144">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ed96-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5ed96-145">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5ed96-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="5ed96-146">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed96-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5ed96-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ed96-147">See also</span></span>

- [<span data-ttu-id="5ed96-148">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="5ed96-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)