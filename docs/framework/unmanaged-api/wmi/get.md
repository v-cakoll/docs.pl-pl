---
title: Get — funkcja (niezarządzany wykaz interfejsów API)
description: Funkcja Get pobiera wartość określonej właściwości.
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
ms.openlocfilehash: e996a299de7b365a1513d5b1fb7ca0e758f6005b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966063"
---
# <a name="get-function"></a><span data-ttu-id="80bfa-103">Get — funkcja</span><span class="sxs-lookup"><span data-stu-id="80bfa-103">Get function</span></span>
<span data-ttu-id="80bfa-104">Pobiera wartość określonej właściwości, jeśli taki istnieje.</span><span class="sxs-lookup"><span data-stu-id="80bfa-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="80bfa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="80bfa-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="80bfa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="80bfa-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="80bfa-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="80bfa-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="80bfa-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="80bfa-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="80bfa-109">[in] Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="80bfa-109">[in] The name of the property.</span></span>

<span data-ttu-id="80bfa-110">`lFlags` [in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="80bfa-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="80bfa-111">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="80bfa-111">This parameter must be 0.</span></span>

<span data-ttu-id="80bfa-112">`pVal` [out] Jeśli funkcja zwraca pomyślnie, zawiera wartość `wszName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="80bfa-112">`pVal` [out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="80bfa-113">`pval` Argument jest przypisany poprawny typ i wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="80bfa-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

<span data-ttu-id="80bfa-114">`pvtType` [out] Jeśli funkcja zwraca pomyślnie, zawiera [stałą typu modelu wspólnych informacji](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) oznacza typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="80bfa-114">`pvtType` [out] If the function returns successfully, contains a [CIM-type constant](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="80bfa-115">Wartość może być również `null`.</span><span class="sxs-lookup"><span data-stu-id="80bfa-115">Its value can also be `null`.</span></span> 

<span data-ttu-id="80bfa-116">`plFlavor` [out] Jeśli funkcja zwraca pomyślnie, otrzymuje informacje na temat źródła właściwości.</span><span class="sxs-lookup"><span data-stu-id="80bfa-116">`plFlavor` [out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="80bfa-117">Wartość może być `null`, lub jeden z następujących stałych WBEM_FLAVOR_TYPE zdefiniowane w *WbemCli.h* pliku nagłówka:</span><span class="sxs-lookup"><span data-stu-id="80bfa-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="80bfa-118">Stała</span><span class="sxs-lookup"><span data-stu-id="80bfa-118">Constant</span></span>  |<span data-ttu-id="80bfa-119">Wartość</span><span class="sxs-lookup"><span data-stu-id="80bfa-119">Value</span></span>  |<span data-ttu-id="80bfa-120">Opis</span><span class="sxs-lookup"><span data-stu-id="80bfa-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="80bfa-121">0x40</span><span class="sxs-lookup"><span data-stu-id="80bfa-121">0x40</span></span> | <span data-ttu-id="80bfa-122">Właściwość jest właściwością standardowych systemowych.</span><span class="sxs-lookup"><span data-stu-id="80bfa-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="80bfa-123">0x20</span><span class="sxs-lookup"><span data-stu-id="80bfa-123">0x20</span></span> | <span data-ttu-id="80bfa-124">Dla klasy: Właściwość jest dziedziczona z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="80bfa-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="80bfa-125">W przypadku wystąpienia: Właściwości, podczas gdy dziedziczone z klasy nadrzędnej, nie został zmodyfikowany przez to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="80bfa-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="80bfa-126">0</span><span class="sxs-lookup"><span data-stu-id="80bfa-126">0</span></span> | <span data-ttu-id="80bfa-127">Dla klasy: Właściwość należy do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="80bfa-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="80bfa-128">W przypadku wystąpienia: Ta właściwość jest modyfikowana przez wystąpienie; oznacza to, że podano wartość lub kwalifikator został dodany lub zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="80bfa-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="80bfa-129">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="80bfa-129">Return value</span></span>

<span data-ttu-id="80bfa-130">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="80bfa-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="80bfa-131">Stała</span><span class="sxs-lookup"><span data-stu-id="80bfa-131">Constant</span></span>  |<span data-ttu-id="80bfa-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="80bfa-132">Value</span></span>  |<span data-ttu-id="80bfa-133">Opis</span><span class="sxs-lookup"><span data-stu-id="80bfa-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="80bfa-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="80bfa-134">0x80041001</span></span> | <span data-ttu-id="80bfa-135">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="80bfa-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="80bfa-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="80bfa-136">0x80041008</span></span> | <span data-ttu-id="80bfa-137">Jeden lub więcej parametrów są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="80bfa-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="80bfa-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="80bfa-138">0x80041002</span></span> | <span data-ttu-id="80bfa-139">Nie znaleziono określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="80bfa-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="80bfa-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="80bfa-140">0x80041006</span></span> | <span data-ttu-id="80bfa-141">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="80bfa-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="80bfa-142">0</span><span class="sxs-lookup"><span data-stu-id="80bfa-142">0</span></span> | <span data-ttu-id="80bfa-143">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="80bfa-143">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="80bfa-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80bfa-144">Remarks</span></span>

<span data-ttu-id="80bfa-145">Ta funkcja zawija wywołanie do [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) metody.</span><span class="sxs-lookup"><span data-stu-id="80bfa-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="80bfa-146">`Get` Funkcji może również zwracać właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="80bfa-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="80bfa-147">`pVal` Argument jest przypisany poprawny typ i wartość kwalifikatora i COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) — funkcja</span><span class="sxs-lookup"><span data-stu-id="80bfa-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="80bfa-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80bfa-148">Requirements</span></span>  
 <span data-ttu-id="80bfa-149">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80bfa-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80bfa-150">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="80bfa-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="80bfa-151">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="80bfa-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80bfa-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80bfa-152">See also</span></span>
- [<span data-ttu-id="80bfa-153">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="80bfa-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
