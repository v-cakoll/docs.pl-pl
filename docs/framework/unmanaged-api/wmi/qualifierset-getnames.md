---
title: QualifierSet_GetNames — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_GetNames pobiera nazwy kwalifikatorów z obiektu lub właściwości.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: bd0a67987dd8ffa825114726d066249aed40cf05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141692"
---
# <a name="qualifierset_getnames-function"></a><span data-ttu-id="10498-103">QualifierSet_GetNames, funkcja</span><span class="sxs-lookup"><span data-stu-id="10498-103">QualifierSet_GetNames function</span></span>

<span data-ttu-id="10498-104">Pobiera nazwy wszystkich kwalifikatorów lub niektórych kwalifikatorów, które są dostępne z bieżącego obiektu lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="10498-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="10498-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="10498-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a><span data-ttu-id="10498-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="10498-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="10498-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="10498-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="10498-108">podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="10498-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="10498-109">podczas Jedna z następujących flag lub wartości, które określają, które nazwy mają być uwzględnione w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="10498-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="10498-110">Stała</span><span class="sxs-lookup"><span data-stu-id="10498-110">Constant</span></span>  |<span data-ttu-id="10498-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="10498-111">Value</span></span>  |<span data-ttu-id="10498-112">Opis</span><span class="sxs-lookup"><span data-stu-id="10498-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="10498-113">0</span><span class="sxs-lookup"><span data-stu-id="10498-113">0</span></span> | <span data-ttu-id="10498-114">Zwróć nazwy wszystkich kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="10498-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="10498-115">0x10</span><span class="sxs-lookup"><span data-stu-id="10498-115">0x10</span></span> | <span data-ttu-id="10498-116">Zwraca tylko nazwy kwalifikatorów specyficzne dla bieżącej właściwości lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="10498-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="10498-117">Dla właściwości: zwracają tylko kwalifikatory charakterystyczne dla właściwości (w tym przesłonięć), a nie te kwalifikatory propagowane z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="10498-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="10498-118">Dla wystąpienia: Zwróć tylko nazwy kwalifikatorów specyficznych dla wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="10498-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="10498-119">Dla klasy: zwracają tylko kwalifikatory charakterystyczne dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="10498-119">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="10498-120">0x20</span><span class="sxs-lookup"><span data-stu-id="10498-120">0x20</span></span> | <span data-ttu-id="10498-121">Zwraca tylko nazwy kwalifikatorów, które zostały przekazane z innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="10498-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="10498-122">Dla właściwości: Zwróć tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="10498-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="10498-123">Dla wystąpienia: Zwróć tylko te kwalifikatory, które zostały przekazane z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="10498-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="10498-124">Dla klasy: Zwróć tylko te nazwy kwalifikatorów dziedziczone z klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="10498-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

`pstrNames`\
<span data-ttu-id="10498-125">określoną Nowy `SAFEARRAY` zawierający żądane nazwy.</span><span class="sxs-lookup"><span data-stu-id="10498-125">[out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="10498-126">Tablica może zawierać 0 elementów.</span><span class="sxs-lookup"><span data-stu-id="10498-126">The array can have 0 elements.</span></span> <span data-ttu-id="10498-127">Jeśli wystąpi błąd, nowy `SAFEARRAY` nie zostanie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="10498-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="10498-128">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="10498-128">Return value</span></span>

<span data-ttu-id="10498-129">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="10498-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="10498-130">Stała</span><span class="sxs-lookup"><span data-stu-id="10498-130">Constant</span></span>  |<span data-ttu-id="10498-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="10498-131">Value</span></span>  |<span data-ttu-id="10498-132">Opis</span><span class="sxs-lookup"><span data-stu-id="10498-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="10498-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="10498-133">0x80041008</span></span> | <span data-ttu-id="10498-134">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="10498-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="10498-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="10498-135">0x80041006</span></span> | <span data-ttu-id="10498-136">Za mało dostępnej pamięci, aby rozpocząć nowe Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="10498-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="10498-137">0</span><span class="sxs-lookup"><span data-stu-id="10498-137">0</span></span> | <span data-ttu-id="10498-138">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="10498-138">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="10498-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10498-139">Remarks</span></span>

<span data-ttu-id="10498-140">Ta funkcja otacza wywołanie metody [IWbemQualifierSet:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) .</span><span class="sxs-lookup"><span data-stu-id="10498-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="10498-141">Po pobraniu nazw kwalifikatorów możesz uzyskać dostęp do każdego kwalifikatora według nazwy, wywołując funkcję [QualifierSet_Get](qualifierset-get.md) .</span><span class="sxs-lookup"><span data-stu-id="10498-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span>

<span data-ttu-id="10498-142">Nie jest to błąd dla danego obiektu, aby mieć kwalifikatory zerowe, więc liczba ciągów w `pstrNames` on return może wynosić 0, mimo że funkcja zwraca `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="10498-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="10498-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10498-143">Requirements</span></span>

<span data-ttu-id="10498-144">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10498-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="10498-145">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="10498-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="10498-146">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="10498-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="10498-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10498-147">See also</span></span>

- [<span data-ttu-id="10498-148">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="10498-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
