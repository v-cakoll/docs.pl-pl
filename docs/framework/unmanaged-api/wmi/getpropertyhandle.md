---
title: "Funkcja GetPropertyHandle (niezarządzany wykaz interfejsów API)"
description: "Funkcja GetPropertyHandle zwraca uchwyt unikatowy tej właściwości tożsamości."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3af852fb4b9899a7937f288ffb65d8ca84e4aef1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="e3c53-103">Funkcja GetPropertyHandle</span><span class="sxs-lookup"><span data-stu-id="e3c53-103">GetPropertyHandle function</span></span>
<span data-ttu-id="e3c53-104">Zwraca unikatowy dojścia identyfikujący właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3c53-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e3c53-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3c53-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a><span data-ttu-id="e3c53-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3c53-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e3c53-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="e3c53-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e3c53-108">[in] Wskaźnik do [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e3c53-108">[in] A pointer to an [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span></span>

`wszPropertyName`  
<span data-ttu-id="e3c53-109">[in] Zerem ciąg kodowany w formacie UTF16 characaters, który zawiera nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3c53-109">[in] A null-terminated string of UTF16-encoded characaters that contains the property name.</span></span>   

`pType`  
<span data-ttu-id="e3c53-110">[out] Wskaźnik do [ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) element członkowski wyliczenia, który reprezentuje typ CIM właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3c53-110">[out] A pointer to a [`CIMTYPE`](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`   
<span data-ttu-id="e3c53-111">[out] Wskaźnik do liczba całkowita, która zawiera dojście właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3c53-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="e3c53-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3c53-112">Return value</span></span>

<span data-ttu-id="e3c53-113">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="e3c53-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e3c53-114">Stała</span><span class="sxs-lookup"><span data-stu-id="e3c53-114">Constant</span></span>  |<span data-ttu-id="e3c53-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="e3c53-115">Value</span></span>  |<span data-ttu-id="e3c53-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e3c53-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e3c53-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e3c53-117">0x80041002</span></span> | <span data-ttu-id="e3c53-118">Określona nazwa właściwości nie został znaleziony.</span><span class="sxs-lookup"><span data-stu-id="e3c53-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e3c53-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e3c53-119">0x80041008</span></span> | <span data-ttu-id="e3c53-120">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e3c53-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="e3c53-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="e3c53-121">0x8004100c</span></span> | <span data-ttu-id="e3c53-122">Żądana właściwość jest typu są `CIM_OBJECT` lub `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="e3c53-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e3c53-123">0</span><span class="sxs-lookup"><span data-stu-id="e3c53-123">0</span></span> | <span data-ttu-id="e3c53-124">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e3c53-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e3c53-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3c53-125">Remarks</span></span>

<span data-ttu-id="e3c53-126">Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="e3c53-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="e3c53-127">Przy użyciu tego uchwytu do identyfikowania właściwości, korzystając z [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) metod do odczytu lub zapisu wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3c53-127">You can use this handle to identify properties when using  [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) methods to read or write property values.</span></span>

<span data-ttu-id="e3c53-128">Uchwyty można pobrać właściwości wszystkich typów danych innych niż `CIM_OBJECT` i `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="e3c53-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="e3c53-129">Zwracane pracy uchwytów we wszystkich wystąpieniach klasy.</span><span class="sxs-lookup"><span data-stu-id="e3c53-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3c53-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3c53-130">Requirements</span></span>  
<span data-ttu-id="e3c53-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c53-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c53-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e3c53-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e3c53-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e3c53-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c53-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3c53-134">See also</span></span>  
[<span data-ttu-id="e3c53-135">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="e3c53-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
