---
title: Funkcja GetPropertyOrigin (niezarządzany wykaz interfejsów API)
description: Funkcja GetPropertyOrigin Określa klasę, w którym zadeklarowany jest właściwością.
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
ms.openlocfilehash: 42e5cd6ee438b33fd07fd7c3242cc3c2a6513dd9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368876"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="cb62a-103">Funkcja GetPropertyOrigin</span><span class="sxs-lookup"><span data-stu-id="cb62a-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="cb62a-104">Określa klasę, w którym zadeklarowany jest właściwością.</span><span class="sxs-lookup"><span data-stu-id="cb62a-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="cb62a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb62a-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="cb62a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb62a-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="cb62a-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="cb62a-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="cb62a-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cb62a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="cb62a-109">[in] Nazwa właściwości dla obiektu, którego klasa będąca właścicielem jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="cb62a-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="cb62a-110">[out] Uzyskuje nazwę klasy, która jest właścicielem właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb62a-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="cb62a-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cb62a-111">Return value</span></span>

<span data-ttu-id="cb62a-112">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="cb62a-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cb62a-113">Stała</span><span class="sxs-lookup"><span data-stu-id="cb62a-113">Constant</span></span>  |<span data-ttu-id="cb62a-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="cb62a-114">Value</span></span>  |<span data-ttu-id="cb62a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="cb62a-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="cb62a-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="cb62a-116">0x80041001</span></span> | <span data-ttu-id="cb62a-117">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="cb62a-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="cb62a-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="cb62a-118">0x80041002</span></span> | <span data-ttu-id="cb62a-119">Nie znaleziono określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb62a-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="cb62a-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="cb62a-120">0x80041008</span></span> | <span data-ttu-id="cb62a-121">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="cb62a-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="cb62a-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="cb62a-122">0x80041006</span></span> | <span data-ttu-id="cb62a-123">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="cb62a-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="cb62a-124">0</span><span class="sxs-lookup"><span data-stu-id="cb62a-124">0</span></span> | <span data-ttu-id="cb62a-125">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cb62a-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="cb62a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb62a-126">Remarks</span></span>

<span data-ttu-id="cb62a-127">Ta funkcja zawija wywołanie do [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) metody.</span><span class="sxs-lookup"><span data-stu-id="cb62a-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="cb62a-128">Ponieważ klasy mogą dziedziczyć właściwości jednego lub więcej klas bazowych, deweloperzy często chcemy określić właściwości, w którym zdefiniowano danej metody.</span><span class="sxs-lookup"><span data-stu-id="cb62a-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="cb62a-129">`pstrClassName` Parametru nie musi wskazywać na prawidłową `BSTR` przed wywołaniem funkcji, ponieważ jest to `out` parametru; ten wskaźnik nie cofnięto przydziału po powrocie z tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="cb62a-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb62a-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb62a-130">Requirements</span></span>

<span data-ttu-id="cb62a-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb62a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="cb62a-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cb62a-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="cb62a-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cb62a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cb62a-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb62a-134">See also</span></span>

- [<span data-ttu-id="cb62a-135">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="cb62a-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)