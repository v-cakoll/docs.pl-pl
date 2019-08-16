---
title: Get — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja Get pobiera określoną wartość właściwości.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 265d3edbd3175eebcf6fd35be24f5b66144c960f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037951"
---
# <a name="get-function"></a><span data-ttu-id="dcd3b-103">Get, funkcja</span><span class="sxs-lookup"><span data-stu-id="dcd3b-103">Get function</span></span>

<span data-ttu-id="dcd3b-104">Pobiera określoną wartość właściwości, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="dcd3b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcd3b-105">Syntax</span></span>

```cpp
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```

## <a name="parameters"></a><span data-ttu-id="dcd3b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcd3b-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="dcd3b-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="dcd3b-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="dcd3b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="dcd3b-109">podczas Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="dcd3b-110">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-110">[in] Reserved.</span></span> <span data-ttu-id="dcd3b-111">Ten parametr musi być równy 0.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="dcd3b-112">określoną Jeśli funkcja zwróci się pomyślnie, zawiera wartość `wszName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="dcd3b-113">Do `pval` argumentu jest przypisany prawidłowy typ i wartość dla kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="dcd3b-114">określoną Jeśli funkcja zwróci się pomyślnie, zawiera [stałą typu CIM](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) , która wskazuje typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="dcd3b-115">Jego wartość może być `null`również.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-115">Its value can also be `null`.</span></span> 

`plFlavor`\
<span data-ttu-id="dcd3b-116">określoną Jeśli funkcja zwróci się pomyślnie, otrzymuje informacje o pochodzeniu właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="dcd3b-117">Jego wartością może być `null`lub jedna z następujących stałych WBEM_FLAVOR_TYPE zdefiniowanych w pliku nagłówkowym *WbemCli. h* :</span><span class="sxs-lookup"><span data-stu-id="dcd3b-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="dcd3b-118">Stała</span><span class="sxs-lookup"><span data-stu-id="dcd3b-118">Constant</span></span>  |<span data-ttu-id="dcd3b-119">Wartość</span><span class="sxs-lookup"><span data-stu-id="dcd3b-119">Value</span></span>  |<span data-ttu-id="dcd3b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="dcd3b-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="dcd3b-121">0x40</span><span class="sxs-lookup"><span data-stu-id="dcd3b-121">0x40</span></span> | <span data-ttu-id="dcd3b-122">Właściwość jest standardową właściwością systemu.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="dcd3b-123">0x20</span><span class="sxs-lookup"><span data-stu-id="dcd3b-123">0x20</span></span> | <span data-ttu-id="dcd3b-124">Dla klasy: Właściwość jest dziedziczona z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="dcd3b-125">Dla wystąpienia: Właściwość, podczas gdy dziedziczy z klasy nadrzędnej, nie została zmodyfikowana przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="dcd3b-126">0</span><span class="sxs-lookup"><span data-stu-id="dcd3b-126">0</span></span> | <span data-ttu-id="dcd3b-127">Dla klasy: Właściwość należy do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="dcd3b-128">Dla wystąpienia: Właściwość jest modyfikowana przez wystąpienie; oznacza to, że została podana wartość lub kwalifikator został dodany lub zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="dcd3b-129">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dcd3b-129">Return value</span></span>

<span data-ttu-id="dcd3b-130">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="dcd3b-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="dcd3b-131">Stała</span><span class="sxs-lookup"><span data-stu-id="dcd3b-131">Constant</span></span>  |<span data-ttu-id="dcd3b-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="dcd3b-132">Value</span></span>  |<span data-ttu-id="dcd3b-133">Opis</span><span class="sxs-lookup"><span data-stu-id="dcd3b-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="dcd3b-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="dcd3b-134">0x80041001</span></span> | <span data-ttu-id="dcd3b-135">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="dcd3b-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="dcd3b-136">0x80041008</span></span> | <span data-ttu-id="dcd3b-137">Co najmniej jeden parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="dcd3b-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="dcd3b-138">0x80041002</span></span> | <span data-ttu-id="dcd3b-139">Nie znaleziono określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="dcd3b-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="dcd3b-140">0x80041006</span></span> | <span data-ttu-id="dcd3b-141">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="dcd3b-142">0</span><span class="sxs-lookup"><span data-stu-id="dcd3b-142">0</span></span> | <span data-ttu-id="dcd3b-143">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="dcd3b-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcd3b-144">Remarks</span></span>

<span data-ttu-id="dcd3b-145">Ta funkcja otacza wywołanie metody [IWbemClassObject:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) .</span><span class="sxs-lookup"><span data-stu-id="dcd3b-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="dcd3b-146">`Get` Funkcja może również zwracać właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="dcd3b-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="dcd3b-147">Do argumentu jest przypisany prawidłowy typ i wartość dla kwalifikatora oraz funkcja com [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) `pVal`</span><span class="sxs-lookup"><span data-stu-id="dcd3b-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="dcd3b-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dcd3b-148">Requirements</span></span>

 <span data-ttu-id="dcd3b-149">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcd3b-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="dcd3b-150">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="dcd3b-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="dcd3b-151">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dcd3b-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dcd3b-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcd3b-152">See also</span></span>

- [<span data-ttu-id="dcd3b-153">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="dcd3b-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
