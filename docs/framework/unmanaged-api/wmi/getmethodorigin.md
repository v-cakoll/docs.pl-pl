---
title: GetMethodOrigin — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetMethodOrigin określa klasę, w której jest zadeklarowana Metoda.
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
ms.openlocfilehash: 9cea7251353dae093f64448c8d84157917fa74c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798559"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="d5ff8-103">GetMethodOrigin, funkcja</span><span class="sxs-lookup"><span data-stu-id="d5ff8-103">GetMethodOrigin function</span></span>
<span data-ttu-id="d5ff8-104">Określa klasę, w której jest zadeklarowana Metoda.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d5ff8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5ff8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="d5ff8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5ff8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d5ff8-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d5ff8-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="d5ff8-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="d5ff8-109">podczas Nazwa metody dla obiektu, którego właścicielem jest żądana Klasa.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="d5ff8-110">określoną Odbiera nazwę klasy, która jest właścicielem metody.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="d5ff8-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d5ff8-111">Return value</span></span>

<span data-ttu-id="d5ff8-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d5ff8-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d5ff8-113">Stała</span><span class="sxs-lookup"><span data-stu-id="d5ff8-113">Constant</span></span>  |<span data-ttu-id="d5ff8-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="d5ff8-114">Value</span></span>  |<span data-ttu-id="d5ff8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d5ff8-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="d5ff8-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="d5ff8-116">0x80041002</span></span> | <span data-ttu-id="d5ff8-117">Nie znaleziono określonej metody.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d5ff8-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d5ff8-118">0x80041008</span></span> | <span data-ttu-id="d5ff8-119">Co najmniej jeden parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d5ff8-120">0</span><span class="sxs-lookup"><span data-stu-id="d5ff8-120">0</span></span> | <span data-ttu-id="d5ff8-121">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d5ff8-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5ff8-122">Remarks</span></span>

<span data-ttu-id="d5ff8-123">Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .</span><span class="sxs-lookup"><span data-stu-id="d5ff8-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="d5ff8-124">Ponieważ Klasa może dziedziczyć metody z co najmniej jednej klasy bazowej, deweloperzy często chcą określić klasę, w której zdefiniowana jest dana metoda.</span><span class="sxs-lookup"><span data-stu-id="d5ff8-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="d5ff8-125">Parametr nie może wskazywać prawidłowego `BSTR` przed `out` wywołaniem funkcji, ponieważ jest to parametr; ten wskaźnik nie jest cofany po powrocie funkcji. `pstrClassName`</span><span class="sxs-lookup"><span data-stu-id="d5ff8-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="d5ff8-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5ff8-126">Requirements</span></span>  
<span data-ttu-id="d5ff8-127">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5ff8-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5ff8-128">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d5ff8-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d5ff8-129">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d5ff8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ff8-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5ff8-130">See also</span></span>

- [<span data-ttu-id="d5ff8-131">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="d5ff8-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
