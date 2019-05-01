---
title: Funkcja GetMethodQualifierSet (niezarządzany wykaz interfejsów API)
description: Funkcja GetMethodQualifierSet pobiera zestaw kwalifikator metody.
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
ms.openlocfilehash: 9257ba57e0d087e3d6b9c7bb995b49a6b814c5f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040745"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="c4ca1-103">GetMethodQualifierSet, funkcja</span><span class="sxs-lookup"><span data-stu-id="c4ca1-103">GetMethodQualifierSet function</span></span>

<span data-ttu-id="c4ca1-104">Pobiera kwalifikator ustawione dla konkretnych metod.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="c4ca1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4ca1-105">Syntax</span></span>

```cpp
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="c4ca1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4ca1-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="c4ca1-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="c4ca1-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="c4ca1-109">[in] Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-109">[in] The method  name.</span></span> <span data-ttu-id="c4ca1-110">`wszMethod` musi wskazywać prawidłowy `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="c4ca1-111">[out] Otrzymuje wskaźnik interfejsu, który umożliwia dostęp do kwalifikatory metody.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="c4ca1-112">`ppQualSet` nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="c4ca1-113">Jeśli wystąpi błąd, nowy obiekt nie jest zwracana i wskaźnik jest ustawiony na wskaż `null`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="c4ca1-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c4ca1-114">Return value</span></span>

<span data-ttu-id="c4ca1-115">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c4ca1-116">Stała</span><span class="sxs-lookup"><span data-stu-id="c4ca1-116">Constant</span></span>  |<span data-ttu-id="c4ca1-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="c4ca1-117">Value</span></span>  |<span data-ttu-id="c4ca1-118">Opis</span><span class="sxs-lookup"><span data-stu-id="c4ca1-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="c4ca1-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c4ca1-119">0x80041002</span></span> | <span data-ttu-id="c4ca1-120">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c4ca1-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c4ca1-121">0x80041008</span></span> | <span data-ttu-id="c4ca1-122">Parametr jest `null`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c4ca1-123">0</span><span class="sxs-lookup"><span data-stu-id="c4ca1-123">0</span></span> | <span data-ttu-id="c4ca1-124">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="c4ca1-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4ca1-125">Remarks</span></span>

<span data-ttu-id="c4ca1-126">Ta funkcja zawija wywołanie do [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) metody.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span>

<span data-ttu-id="c4ca1-127">Wywołanie tej funkcji jest obsługiwana tylko wtedy, gdy bieżący obiekt jest definicją klasy modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="c4ca1-128">Metoda manipulowania nie jest dostępna dla [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźniki prowadzące do wystąpienia modelu CIM.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="c4ca1-129">Ponieważ każda metoda może mieć własną kwalifikatory [wskaźnik IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umożliwia obiekt wywołujący, dodawać, edytować lub usuwać kwalifikatory.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4ca1-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4ca1-130">Requirements</span></span>

<span data-ttu-id="c4ca1-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4ca1-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="c4ca1-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c4ca1-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="c4ca1-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c4ca1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c4ca1-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4ca1-134">See also</span></span>

- [<span data-ttu-id="c4ca1-135">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="c4ca1-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)