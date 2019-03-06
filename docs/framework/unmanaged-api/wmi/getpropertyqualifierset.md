---
title: Funkcja GetPropertyQualifierSet (niezarządzany wykaz interfejsów API)
description: Funkcja GetPropertyQualifierSet pobiera kwalifikator, ustaw dla właściwości.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdb9f748279e4e74c0dbd1ced1f48e3a24b9904d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358421"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="a52c7-103">GetPropertyQualifierSet — funkcja</span><span class="sxs-lookup"><span data-stu-id="a52c7-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="a52c7-104">Pobiera kwalifikator, ustaw dla określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="a52c7-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a52c7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a52c7-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="a52c7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a52c7-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="a52c7-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="a52c7-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="a52c7-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a52c7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="a52c7-109">[in] Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="a52c7-109">[in] The property  name.</span></span> <span data-ttu-id="a52c7-110">`wszProperty` musi wskazywać prawidłowy `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="a52c7-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="a52c7-111">[out] Otrzymuje wskaźnik interfejsu, który umożliwia dostęp do kwalifikatory właściwości.</span><span class="sxs-lookup"><span data-stu-id="a52c7-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="a52c7-112">`ppQualSet` nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="a52c7-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="a52c7-113">Jeśli wystąpi błąd, nowy obiekt nie jest zwracana i wskaźnik jest ustawiony na wskaż `null`.</span><span class="sxs-lookup"><span data-stu-id="a52c7-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="a52c7-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a52c7-114">Return value</span></span>

<span data-ttu-id="a52c7-115">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="a52c7-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a52c7-116">Stała</span><span class="sxs-lookup"><span data-stu-id="a52c7-116">Constant</span></span>  |<span data-ttu-id="a52c7-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="a52c7-117">Value</span></span>  |<span data-ttu-id="a52c7-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a52c7-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="a52c7-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a52c7-119">0x80041001</span></span> | <span data-ttu-id="a52c7-120">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="a52c7-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="a52c7-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a52c7-121">0x80041002</span></span> | <span data-ttu-id="a52c7-122">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="a52c7-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a52c7-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a52c7-123">0x80041006</span></span> | <span data-ttu-id="a52c7-124">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="a52c7-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a52c7-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a52c7-125">0x80041008</span></span> | <span data-ttu-id="a52c7-126">Parametr jest `null`.</span><span class="sxs-lookup"><span data-stu-id="a52c7-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="a52c7-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="a52c7-127">0x80041030</span></span> | <span data-ttu-id="a52c7-128">Funkcja podejmie próbę uzyskania kwalifikatorów właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="a52c7-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a52c7-129">0</span><span class="sxs-lookup"><span data-stu-id="a52c7-129">0</span></span> | <span data-ttu-id="a52c7-130">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a52c7-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a52c7-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a52c7-131">Remarks</span></span>

<span data-ttu-id="a52c7-132">Ta funkcja zawija wywołanie do [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) metody.</span><span class="sxs-lookup"><span data-stu-id="a52c7-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="a52c7-133">Wywołanie tej funkcji jest obsługiwana tylko wtedy, gdy bieżący obiekt jest definicją klasy modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="a52c7-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="a52c7-134">Metoda manipulowania nie jest dostępna dla [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźniki prowadzące do wystąpienia modelu CIM.</span><span class="sxs-lookup"><span data-stu-id="a52c7-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="a52c7-135">Ponieważ każda metoda może mieć własną kwalifikatory [wskaźnik IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umożliwia obiekt wywołujący, dodawać, edytować lub usuwać kwalifikatory.</span><span class="sxs-lookup"><span data-stu-id="a52c7-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="a52c7-136">Ponieważ właściwości systemu mieć nie kwalifikatorów, funkcja zwraca `WBEM_E_SYSTEM_PROPERTY` Jeśli użytkownik podejmie próbę uzyskania [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wskaźnik dla właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="a52c7-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="a52c7-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a52c7-137">Requirements</span></span>

<span data-ttu-id="a52c7-138">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a52c7-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a52c7-139">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a52c7-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="a52c7-140">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a52c7-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a52c7-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a52c7-141">See also</span></span>

- [<span data-ttu-id="a52c7-142">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="a52c7-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)