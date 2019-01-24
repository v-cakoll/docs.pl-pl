---
title: Funkcja GetMethodOrigin (niezarządzany wykaz interfejsów API)
description: Funkcja GetMethodOrigin Określa klasę, w którym zadeklarowany jest metodą.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76f449e52168001a2aaac6cbc3707361cf7f809a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582471"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="4dfd2-103">Funkcja GetMethodOrigin</span><span class="sxs-lookup"><span data-stu-id="4dfd2-103">GetMethodOrigin function</span></span>
<span data-ttu-id="4dfd2-104">Określa klasę, w którym zadeklarowany jest metodą.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4dfd2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dfd2-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="4dfd2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4dfd2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4dfd2-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4dfd2-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="4dfd2-109">[in] Nazwa metody dla obiektu, którego klasa będąca właścicielem jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="4dfd2-110">[out] Uzyskuje nazwę klasy, która jest właścicielem metody.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="4dfd2-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4dfd2-111">Return value</span></span>

<span data-ttu-id="4dfd2-112">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="4dfd2-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4dfd2-113">Stała</span><span class="sxs-lookup"><span data-stu-id="4dfd2-113">Constant</span></span>  |<span data-ttu-id="4dfd2-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="4dfd2-114">Value</span></span>  |<span data-ttu-id="4dfd2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4dfd2-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="4dfd2-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4dfd2-116">0x80041002</span></span> | <span data-ttu-id="4dfd2-117">Nie można odnaleźć określonej metody.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4dfd2-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4dfd2-118">0x80041008</span></span> | <span data-ttu-id="4dfd2-119">Jeden lub więcej parametrów są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4dfd2-120">0</span><span class="sxs-lookup"><span data-stu-id="4dfd2-120">0</span></span> | <span data-ttu-id="4dfd2-121">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4dfd2-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4dfd2-122">Remarks</span></span>

<span data-ttu-id="4dfd2-123">Ta funkcja zawija wywołanie do [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="4dfd2-124">Ponieważ klasa może dziedziczyć metody z jednego lub więcej klas bazowych, deweloperzy często chcą określić klasę, w którym zdefiniowano danej metody.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="4dfd2-125">`pstrClassName` Parametru nie musi wskazywać na prawidłową `BSTR` przed wywołaniem funkcji, ponieważ jest to `out` parametru; ten wskaźnik nie cofnięto przydziału po powrocie z tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="4dfd2-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="4dfd2-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4dfd2-126">Requirements</span></span>  
<span data-ttu-id="4dfd2-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dfd2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dfd2-128">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4dfd2-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4dfd2-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4dfd2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dfd2-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dfd2-130">See also</span></span>
- [<span data-ttu-id="4dfd2-131">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="4dfd2-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
