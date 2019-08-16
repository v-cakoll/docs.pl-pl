---
title: GetPropertyHandle — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetPropertyHandle zwraca unikatowy uchwyt, który identyfikuje właściwość.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6dc2792b572aae30e9989c81967b86f340d7b83
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038260"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="4ca51-103">GetPropertyHandle, funkcja</span><span class="sxs-lookup"><span data-stu-id="4ca51-103">GetPropertyHandle function</span></span>

<span data-ttu-id="4ca51-104">Zwraca unikatowy uchwyt identyfikujący właściwość.</span><span class="sxs-lookup"><span data-stu-id="4ca51-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="4ca51-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ca51-105">Syntax</span></span>

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a><span data-ttu-id="4ca51-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ca51-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="4ca51-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="4ca51-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="4ca51-108">podczas Wskaźnik do wystąpienia [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .</span><span class="sxs-lookup"><span data-stu-id="4ca51-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`\
<span data-ttu-id="4ca51-109">podczas Ciąg zakończony znakiem NULL znaków UTF16, który zawiera nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ca51-109">[in] A null-terminated string of UTF16-encoded characters that contains the property name.</span></span>

`pType`\
<span data-ttu-id="4ca51-110">określoną Wskaźnik do [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) elementu członkowskiego wyliczenia, który reprezentuje typ CIM właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ca51-110">[out] A pointer to a [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`\
<span data-ttu-id="4ca51-111">określoną Wskaźnik do liczby całkowitej, która zawiera uchwyt właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ca51-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="4ca51-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4ca51-112">Return value</span></span>

<span data-ttu-id="4ca51-113">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="4ca51-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4ca51-114">Stała</span><span class="sxs-lookup"><span data-stu-id="4ca51-114">Constant</span></span>  |<span data-ttu-id="4ca51-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="4ca51-115">Value</span></span>  |<span data-ttu-id="4ca51-116">Opis</span><span class="sxs-lookup"><span data-stu-id="4ca51-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="4ca51-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4ca51-117">0x80041002</span></span> | <span data-ttu-id="4ca51-118">Nie znaleziono określonej nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ca51-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4ca51-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4ca51-119">0x80041008</span></span> | <span data-ttu-id="4ca51-120">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="4ca51-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="4ca51-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="4ca51-121">0x8004100c</span></span> | <span data-ttu-id="4ca51-122">Żądana właściwość jest typu `CIM_OBJECT` lub. `CIM_ARRAY`</span><span class="sxs-lookup"><span data-stu-id="4ca51-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4ca51-123">0</span><span class="sxs-lookup"><span data-stu-id="4ca51-123">0</span></span> | <span data-ttu-id="4ca51-124">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4ca51-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="4ca51-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ca51-125">Remarks</span></span>

<span data-ttu-id="4ca51-126">Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) .</span><span class="sxs-lookup"><span data-stu-id="4ca51-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="4ca51-127">Tego uchwytu można użyć do zidentyfikowania właściwości przy użyciu metod [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) do odczytu lub zapisu wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ca51-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="4ca51-128">Dojścia można pobrać dla właściwości wszystkich typów danych innych niż `CIM_OBJECT` i. `CIM_ARRAY`</span><span class="sxs-lookup"><span data-stu-id="4ca51-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="4ca51-129">Zwraca obsługę dla wszystkich wystąpień klasy.</span><span class="sxs-lookup"><span data-stu-id="4ca51-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="4ca51-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ca51-130">Requirements</span></span>

<span data-ttu-id="4ca51-131">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ca51-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="4ca51-132">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4ca51-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="4ca51-133">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4ca51-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4ca51-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ca51-134">See also</span></span>

- [<span data-ttu-id="4ca51-135">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="4ca51-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
