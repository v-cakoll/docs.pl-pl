---
title: GetPropertyOrigin — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetPropertyOrigin określa klasę, w której jest zadeklarowana właściwość.
ms.date: 11/06/2017
api_name:
- GetPropertyOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyOrigin
helpviewer_keywords:
- GetPropertyOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c2d0f23f3dd2d52f73f09c32d4e3118a9ed5ea3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798494"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="59dfd-103">GetPropertyOrigin, funkcja</span><span class="sxs-lookup"><span data-stu-id="59dfd-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="59dfd-104">Określa klasę, w której jest zadeklarowana właściwość.</span><span class="sxs-lookup"><span data-stu-id="59dfd-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="59dfd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="59dfd-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="59dfd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="59dfd-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="59dfd-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="59dfd-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="59dfd-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="59dfd-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="59dfd-109">podczas Nazwa właściwości obiektu, którego właścicielem jest żądana Klasa.</span><span class="sxs-lookup"><span data-stu-id="59dfd-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="59dfd-110">określoną Odbiera nazwę klasy, która jest właścicielem właściwości.</span><span class="sxs-lookup"><span data-stu-id="59dfd-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="59dfd-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="59dfd-111">Return value</span></span>

<span data-ttu-id="59dfd-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="59dfd-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="59dfd-113">Stała</span><span class="sxs-lookup"><span data-stu-id="59dfd-113">Constant</span></span>  |<span data-ttu-id="59dfd-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="59dfd-114">Value</span></span>  |<span data-ttu-id="59dfd-115">Opis</span><span class="sxs-lookup"><span data-stu-id="59dfd-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="59dfd-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="59dfd-116">0x80041001</span></span> | <span data-ttu-id="59dfd-117">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="59dfd-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="59dfd-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="59dfd-118">0x80041002</span></span> | <span data-ttu-id="59dfd-119">Nie znaleziono określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="59dfd-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="59dfd-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="59dfd-120">0x80041008</span></span> | <span data-ttu-id="59dfd-121">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="59dfd-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="59dfd-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="59dfd-122">0x80041006</span></span> | <span data-ttu-id="59dfd-123">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="59dfd-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="59dfd-124">0</span><span class="sxs-lookup"><span data-stu-id="59dfd-124">0</span></span> | <span data-ttu-id="59dfd-125">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="59dfd-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="59dfd-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59dfd-126">Remarks</span></span>

<span data-ttu-id="59dfd-127">Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) .</span><span class="sxs-lookup"><span data-stu-id="59dfd-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="59dfd-128">Ponieważ Klasa może dziedziczyć właściwości z co najmniej jednej klasy bazowej, deweloperzy często chcą określić właściwość, w której jest zdefiniowana dana metoda.</span><span class="sxs-lookup"><span data-stu-id="59dfd-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="59dfd-129">Parametr nie może wskazywać prawidłowego `BSTR` przed `out` wywołaniem funkcji, ponieważ jest to parametr; ten wskaźnik nie jest cofany po powrocie funkcji. `pstrClassName`</span><span class="sxs-lookup"><span data-stu-id="59dfd-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="59dfd-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59dfd-130">Requirements</span></span>

<span data-ttu-id="59dfd-131">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59dfd-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="59dfd-132">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="59dfd-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="59dfd-133">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="59dfd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="59dfd-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59dfd-134">See also</span></span>

- [<span data-ttu-id="59dfd-135">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="59dfd-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
