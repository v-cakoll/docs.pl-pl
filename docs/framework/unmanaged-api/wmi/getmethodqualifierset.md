---
title: GetMethodQualifierSet — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetMethodQualifierSet Pobiera zestaw kwalifikatora metody.
ms.date: 11/06/2017
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86a7788736c3c12cfcfd405de88dfadfb14c1eca
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798527"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="ccc1b-103">GetMethodQualifierSet, funkcja</span><span class="sxs-lookup"><span data-stu-id="ccc1b-103">GetMethodQualifierSet function</span></span>

<span data-ttu-id="ccc1b-104">Pobiera kwalifikator zestawu dla określonej metody.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ccc1b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccc1b-105">Syntax</span></span>

```cpp
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="ccc1b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccc1b-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="ccc1b-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="ccc1b-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="ccc1b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="ccc1b-109">podczas Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-109">[in] The method  name.</span></span> <span data-ttu-id="ccc1b-110">`wszMethod`musi wskazywać prawidłowy `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="ccc1b-111">określoną Odbiera wskaźnik interfejsu, który umożliwia dostęp do kwalifikatorów metody.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="ccc1b-112">`ppQualSet`nie może `null`być.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="ccc1b-113">Jeśli wystąpi błąd, nowy obiekt nie jest zwracany, a wskaźnik zostanie ustawiony na `null`wartość.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ccc1b-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ccc1b-114">Return value</span></span>

<span data-ttu-id="ccc1b-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="ccc1b-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ccc1b-116">Stała</span><span class="sxs-lookup"><span data-stu-id="ccc1b-116">Constant</span></span>  |<span data-ttu-id="ccc1b-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="ccc1b-117">Value</span></span>  |<span data-ttu-id="ccc1b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ccc1b-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="ccc1b-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ccc1b-119">0x80041002</span></span> | <span data-ttu-id="ccc1b-120">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ccc1b-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ccc1b-121">0x80041008</span></span> | <span data-ttu-id="ccc1b-122">Parametr ma `null`wartość.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ccc1b-123">0</span><span class="sxs-lookup"><span data-stu-id="ccc1b-123">0</span></span> | <span data-ttu-id="ccc1b-124">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ccc1b-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ccc1b-125">Remarks</span></span>

<span data-ttu-id="ccc1b-126">Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="ccc1b-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span>

<span data-ttu-id="ccc1b-127">Wywołanie tej funkcji jest obsługiwane tylko wtedy, gdy bieżący obiekt jest definicją klasy CIM.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="ccc1b-128">Operowanie metodami nie jest dostępne dla wskaźników [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , które wskazują wystąpienia modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="ccc1b-129">Ponieważ każda metoda może mieć własne kwalifikatory, [wskaźnik IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umożliwia obiektowi wywołującemu Dodawanie, edytowanie lub usuwanie tych kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="ccc1b-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="ccc1b-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ccc1b-130">Requirements</span></span>

<span data-ttu-id="ccc1b-131">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccc1b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ccc1b-132">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ccc1b-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="ccc1b-133">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ccc1b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ccc1b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccc1b-134">See also</span></span>

- [<span data-ttu-id="ccc1b-135">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="ccc1b-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
