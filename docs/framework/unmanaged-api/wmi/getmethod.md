---
title: GetMethod — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetMethod pobiera informacje o metodzie.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9cc185bf8cccb8ed3c24e28954afd86464602d7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798569"
---
# <a name="getmethod-function"></a><span data-ttu-id="d035e-103">GetMethod, funkcja</span><span class="sxs-lookup"><span data-stu-id="d035e-103">GetMethod function</span></span>

<span data-ttu-id="d035e-104">Pobiera informacje o określonej metodzie.</span><span class="sxs-lookup"><span data-stu-id="d035e-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="d035e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d035e-105">Syntax</span></span>

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a><span data-ttu-id="d035e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d035e-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="d035e-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="d035e-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="d035e-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="d035e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="d035e-109">podczas Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="d035e-109">[in] The method name.</span></span> <span data-ttu-id="d035e-110">Ten parametr nie może `null` być prawidłowy. `LPCWSTR`</span><span class="sxs-lookup"><span data-stu-id="d035e-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`\
<span data-ttu-id="d035e-111">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="d035e-111">[in] Reserved.</span></span> <span data-ttu-id="d035e-112">Ten parametr musi być równy 0.</span><span class="sxs-lookup"><span data-stu-id="d035e-112">This parameter must be 0.</span></span>

`ppInSignature`\
<span data-ttu-id="d035e-113">określoną Wskaźnik do adresu wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , który opisuje parametry w metodzie.</span><span class="sxs-lookup"><span data-stu-id="d035e-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in parameters to the method.</span></span> <span data-ttu-id="d035e-114">Ten parametr jest ignorowany, jeśli jest ustawiony `null`na.</span><span class="sxs-lookup"><span data-stu-id="d035e-114">This parameter is ignored if it is set to `null`.</span></span>

`ppOutSignature`\
<span data-ttu-id="d035e-115">określoną Wskaźnik do adresu wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , który opisuje parametry out metody.</span><span class="sxs-lookup"><span data-stu-id="d035e-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="d035e-116">Ten parametr jest ignorowany, jeśli jest ustawiony `null`na.</span><span class="sxs-lookup"><span data-stu-id="d035e-116">This parameter is ignored if it is set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d035e-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d035e-117">Return value</span></span>

<span data-ttu-id="d035e-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d035e-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d035e-119">Stała</span><span class="sxs-lookup"><span data-stu-id="d035e-119">Constant</span></span>  |<span data-ttu-id="d035e-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="d035e-120">Value</span></span>  |<span data-ttu-id="d035e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d035e-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="d035e-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="d035e-122">0x80041002</span></span> | <span data-ttu-id="d035e-123">Nie znaleziono określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d035e-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d035e-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d035e-124">0x80041006</span></span> | <span data-ttu-id="d035e-125">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="d035e-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d035e-126">0</span><span class="sxs-lookup"><span data-stu-id="d035e-126">0</span></span> | <span data-ttu-id="d035e-127">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d035e-127">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="d035e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d035e-128">Remarks</span></span>

<span data-ttu-id="d035e-129">Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .</span><span class="sxs-lookup"><span data-stu-id="d035e-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="d035e-130">Zarządzanie systemem Windows może ustawić [](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźnik `null` IWbemClassObject, jeśli metoda nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="d035e-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="d035e-131">W `ppInSignature` systemach `ppOutSignature` i opisują odpowiednio parametry in i out `IWbemClassObject` , jako właściwości w wystąpieniu klasy systemowej [_Parameters](/windows/desktop/WmiSdk/--parameters).</span><span class="sxs-lookup"><span data-stu-id="d035e-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="d035e-132">`ppInSignature` Właściwości w `Param`są nazwane *n*, gdzie *n* jest pozycją `Param1` `Param2`parametru w sygnaturze metody (na przykład itp.).</span><span class="sxs-lookup"><span data-stu-id="d035e-132">The properties in `ppInSignature` are named `Param`*n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="d035e-133">Właściwości w `ppOutSignature` są również nazywane `Param` *n*, a zwracaną wartością jest nazwa `ReturnValue`.</span><span class="sxs-lookup"><span data-stu-id="d035e-133">The properties in `ppOutSignature` are also named `Param`*n*, and the return value is named `ReturnValue`.</span></span> <span data-ttu-id="d035e-134">Aby uzyskać więcej informacji i przykład, zobacz [IWbemClassObject:: GetMethod Metoda](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="d035e-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="d035e-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d035e-135">Requirements</span></span>

<span data-ttu-id="d035e-136">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d035e-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d035e-137">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d035e-137">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="d035e-138">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d035e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d035e-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d035e-139">See also</span></span>

- [<span data-ttu-id="d035e-140">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="d035e-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
