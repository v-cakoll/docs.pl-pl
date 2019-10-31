---
title: GetPropertyQualifierSet — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetPropertyQualifierSet pobiera kwalifikator dla właściwości.
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
ms.openlocfilehash: 4133145c7bea1fb3c018d809b9fea3de38270619
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127454"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="aad91-103">GetPropertyQualifierSet, funkcja</span><span class="sxs-lookup"><span data-stu-id="aad91-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="aad91-104">Pobiera kwalifikator zestawu dla określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="aad91-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="aad91-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="aad91-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="aad91-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aad91-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="aad91-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="aad91-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="aad91-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="aad91-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="aad91-109">podczas Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="aad91-109">[in] The property  name.</span></span> <span data-ttu-id="aad91-110">`wszProperty` musi wskazywać prawidłowy `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="aad91-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="aad91-111">określoną Odbiera wskaźnik interfejsu, który umożliwia dostęp do kwalifikatorów właściwości.</span><span class="sxs-lookup"><span data-stu-id="aad91-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="aad91-112">nie można `null``ppQualSet`.</span><span class="sxs-lookup"><span data-stu-id="aad91-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="aad91-113">Jeśli wystąpi błąd, nowy obiekt nie jest zwracany, a wskaźnik zostanie ustawiony na wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="aad91-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="aad91-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aad91-114">Return value</span></span>

<span data-ttu-id="aad91-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="aad91-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="aad91-116">Stała</span><span class="sxs-lookup"><span data-stu-id="aad91-116">Constant</span></span>  |<span data-ttu-id="aad91-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="aad91-117">Value</span></span>  |<span data-ttu-id="aad91-118">Opis</span><span class="sxs-lookup"><span data-stu-id="aad91-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="aad91-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="aad91-119">0x80041001</span></span> | <span data-ttu-id="aad91-120">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="aad91-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="aad91-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="aad91-121">0x80041002</span></span> | <span data-ttu-id="aad91-122">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="aad91-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="aad91-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="aad91-123">0x80041006</span></span> | <span data-ttu-id="aad91-124">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="aad91-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="aad91-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="aad91-125">0x80041008</span></span> | <span data-ttu-id="aad91-126">Parametr jest `null`.</span><span class="sxs-lookup"><span data-stu-id="aad91-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="aad91-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="aad91-127">0x80041030</span></span> | <span data-ttu-id="aad91-128">Funkcja próbuje uzyskać kwalifikatory właściwości System.</span><span class="sxs-lookup"><span data-stu-id="aad91-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="aad91-129">0</span><span class="sxs-lookup"><span data-stu-id="aad91-129">0</span></span> | <span data-ttu-id="aad91-130">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aad91-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="aad91-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aad91-131">Remarks</span></span>

<span data-ttu-id="aad91-132">Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="aad91-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="aad91-133">Wywołanie tej funkcji jest obsługiwane tylko wtedy, gdy bieżący obiekt jest definicją klasy CIM.</span><span class="sxs-lookup"><span data-stu-id="aad91-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="aad91-134">Operowanie metodami nie jest dostępne dla wskaźników [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , które wskazują wystąpienia modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="aad91-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="aad91-135">Ponieważ każda metoda może mieć własne kwalifikatory, [wskaźnik IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umożliwia obiektowi wywołującemu Dodawanie, edytowanie lub usuwanie tych kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="aad91-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="aad91-136">Ponieważ właściwości systemu nie mają kwalifikatorów, funkcja zwraca `WBEM_E_SYSTEM_PROPERTY`, jeśli próbujesz uzyskać wskaźnik [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) dla właściwości System.</span><span class="sxs-lookup"><span data-stu-id="aad91-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="aad91-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aad91-137">Requirements</span></span>

<span data-ttu-id="aad91-138">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aad91-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="aad91-139">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="aad91-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="aad91-140">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aad91-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="aad91-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aad91-141">See also</span></span>

- [<span data-ttu-id="aad91-142">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="aad91-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
