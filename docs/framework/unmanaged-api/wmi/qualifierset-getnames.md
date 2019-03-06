---
title: Funkcja QualifierSet_GetNames (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_GetNames pobiera nazwy kwalifikatory z obiektu lub właściwości.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da6321e50082c3f73477b8187cc5bf671655df21
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365948"
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="1ad1e-103">QualifierSet_GetNames — funkcja</span><span class="sxs-lookup"><span data-stu-id="1ad1e-103">QualifierSet_GetNames function</span></span>

<span data-ttu-id="1ad1e-104">Pobiera nazwy wszystkich kwalifikatorów lub niektórych kwalifikatorów, które są dostępne z bieżącego obiektu lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1ad1e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ad1e-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a><span data-ttu-id="1ad1e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ad1e-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="1ad1e-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="1ad1e-108">[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="1ad1e-109">[in] Jedną z następujących flag lub wartości, które określa nazwy, w których do uwzględnienia w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="1ad1e-110">Stała</span><span class="sxs-lookup"><span data-stu-id="1ad1e-110">Constant</span></span>  |<span data-ttu-id="1ad1e-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="1ad1e-111">Value</span></span>  |<span data-ttu-id="1ad1e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad1e-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="1ad1e-113">0</span><span class="sxs-lookup"><span data-stu-id="1ad1e-113">0</span></span> | <span data-ttu-id="1ad1e-114">Zwraca nazwy wszystkich kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="1ad1e-115">0x10</span><span class="sxs-lookup"><span data-stu-id="1ad1e-115">0x10</span></span> | <span data-ttu-id="1ad1e-116">Zwróć tylko nazwy kwalifikatory określonych do bieżącej właściwości lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="1ad1e-117">Dla właściwości: Zwróć tylko kwalifikatory określone dla właściwości (w tym zastąpień), a nie kwalifikatory propagowane z poziomu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="1ad1e-118">W przypadku wystąpienia: Zwróć tylko nazwy kwalifikator danego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="1ad1e-119">Dla klasy: Zwróć tylko kwalifikatory określonej klasy pochodnej jest.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-119">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="1ad1e-120">0x20</span><span class="sxs-lookup"><span data-stu-id="1ad1e-120">0x20</span></span> | <span data-ttu-id="1ad1e-121">Zwróć tylko nazwy kwalifikatory propagowane z innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="1ad1e-122">Dla właściwości: Zwróć tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="1ad1e-123">W przypadku wystąpienia: Zwróć tylko tych kwalifikatory propagowane z poziomu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="1ad1e-124">Dla klasy: Zwróć tylko nazwy kwalifikator dziedziczone z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

`pstrNames`\
<span data-ttu-id="1ad1e-125">[out] Nowy `SAFEARRAY` zawierający żądanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-125">[out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="1ad1e-126">Tablica może mieć elementów 0.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-126">The array can have 0 elements.</span></span> <span data-ttu-id="1ad1e-127">Jeśli wystąpi błąd, nowy `SAFEARRAY` nie jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ad1e-128">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1ad1e-128">Return value</span></span>

<span data-ttu-id="1ad1e-129">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="1ad1e-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1ad1e-130">Stała</span><span class="sxs-lookup"><span data-stu-id="1ad1e-130">Constant</span></span>  |<span data-ttu-id="1ad1e-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="1ad1e-131">Value</span></span>  |<span data-ttu-id="1ad1e-132">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad1e-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1ad1e-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1ad1e-133">0x80041008</span></span> | <span data-ttu-id="1ad1e-134">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1ad1e-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1ad1e-135">0x80041006</span></span> | <span data-ttu-id="1ad1e-136">Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1ad1e-137">0</span><span class="sxs-lookup"><span data-stu-id="1ad1e-137">0</span></span> | <span data-ttu-id="1ad1e-138">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-138">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="1ad1e-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ad1e-139">Remarks</span></span>

<span data-ttu-id="1ad1e-140">Ta funkcja zawija wywołanie do [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) metody.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="1ad1e-141">Po po pobraniu nazwy kwalifikator, są dostępne każdego kwalifikator według nazwy przez wywołanie metody [QualifierSet_Get](qualifierset-get.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span>

<span data-ttu-id="1ad1e-142">Nie jest błąd dla danego obiektu, który ma zero kwalifikatorów, więc liczba ciągów w `pstrNames` przy powrocie może przyjąć wartość 0, nawet jeśli funkcja zwraca `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="1ad1e-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ad1e-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ad1e-143">Requirements</span></span>

<span data-ttu-id="1ad1e-144">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ad1e-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="1ad1e-145">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1ad1e-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="1ad1e-146">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1ad1e-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1ad1e-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ad1e-147">See also</span></span>

- [<span data-ttu-id="1ad1e-148">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="1ad1e-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)