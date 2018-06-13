---
title: Funkcja GetMethodOrigin (niezarządzany wykaz interfejsów API)
description: Funkcja GetMethodOrigin Określa klasę, w którym zadeklarowany jest metoda.
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
ms.openlocfilehash: 35e56494d0082db970afce21da8e63a597f0a535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458153"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="cedd1-103">Funkcja GetMethodOrigin</span><span class="sxs-lookup"><span data-stu-id="cedd1-103">GetMethodOrigin function</span></span>
<span data-ttu-id="cedd1-104">Określa klasę, w którym zadeklarowany jest metoda.</span><span class="sxs-lookup"><span data-stu-id="cedd1-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="cedd1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cedd1-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="cedd1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cedd1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="cedd1-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="cedd1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="cedd1-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cedd1-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="cedd1-109">[in] Nazwa metody dla obiektu, w których klasa będąca właścicielem jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="cedd1-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="cedd1-110">[out] Uzyskuje nazwę klasy, która jest właścicielem metody.</span><span class="sxs-lookup"><span data-stu-id="cedd1-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="cedd1-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cedd1-111">Return value</span></span>

<span data-ttu-id="cedd1-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="cedd1-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cedd1-113">Stała</span><span class="sxs-lookup"><span data-stu-id="cedd1-113">Constant</span></span>  |<span data-ttu-id="cedd1-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="cedd1-114">Value</span></span>  |<span data-ttu-id="cedd1-115">Opis</span><span class="sxs-lookup"><span data-stu-id="cedd1-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="cedd1-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="cedd1-116">0x80041002</span></span> | <span data-ttu-id="cedd1-117">Nie można odnaleźć określonej metody.</span><span class="sxs-lookup"><span data-stu-id="cedd1-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="cedd1-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="cedd1-118">0x80041008</span></span> | <span data-ttu-id="cedd1-119">Jeden lub więcej parametrów nie są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="cedd1-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="cedd1-120">0</span><span class="sxs-lookup"><span data-stu-id="cedd1-120">0</span></span> | <span data-ttu-id="cedd1-121">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cedd1-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="cedd1-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cedd1-122">Remarks</span></span>

<span data-ttu-id="cedd1-123">Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="cedd1-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="cedd1-124">Ponieważ klasy mogą dziedziczyć metody co najmniej jednej klasy podstawowej, deweloperzy często chcą określić klasę, w którym jest zdefiniowany danej metody.</span><span class="sxs-lookup"><span data-stu-id="cedd1-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="cedd1-125">`pstrClassName` Parametru nie musi wskazywać na prawidłową `BSTR` przed wywołaniem funkcji, ponieważ jest to `out` parametru; ten wskaźnik nie cofnięciu przydziału po funkcja zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="cedd1-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="cedd1-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cedd1-126">Requirements</span></span>  
<span data-ttu-id="cedd1-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cedd1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cedd1-128">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cedd1-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cedd1-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cedd1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cedd1-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cedd1-130">See also</span></span>  
[<span data-ttu-id="cedd1-131">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="cedd1-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
