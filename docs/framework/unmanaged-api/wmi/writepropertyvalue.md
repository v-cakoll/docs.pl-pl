---
title: "Funkcja WritePropertyValue (niezarządzany wykaz interfejsów API)"
description: "Funkcja WritePropertyValue zapisuje bajty w właściwości."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: WritePropertyValue
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: WritePropertyValue
helpviewer_keywords: WritePropertyValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26337a13ab9840b79c253d4af2d84a10e70877c5
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="68d1c-103">Funkcja WritePropertyValue</span><span class="sxs-lookup"><span data-stu-id="68d1c-103">WritePropertyValue function</span></span>
<span data-ttu-id="68d1c-104">Zapisuje określoną liczbę bajtów do właściwości identyfikowany przez dojście właściwości.</span><span class="sxs-lookup"><span data-stu-id="68d1c-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="68d1c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="68d1c-105">Syntax</span></span>  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="68d1c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="68d1c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="68d1c-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="68d1c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="68d1c-108">[in] Wskaźnik do [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="68d1c-108">[in] A pointer to an [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span></span>

`lHandle`  
<span data-ttu-id="68d1c-109">[in] Liczba całkowita, która zawiera dojście, która identyfikuje tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="68d1c-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="68d1c-110">Dojście można pobranej poprzez wywołanie [GetPropertyHandle](getpropertyhandle.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="68d1c-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="68d1c-111">[in] Liczba bajtów zapisywanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="68d1c-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="68d1c-112">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="68d1c-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="68d1c-113">[out] Wskaźnik do tablicy typu byte, który zawiera dane.</span><span class="sxs-lookup"><span data-stu-id="68d1c-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="68d1c-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="68d1c-114">Return value</span></span>

<span data-ttu-id="68d1c-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="68d1c-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="68d1c-116">Stała</span><span class="sxs-lookup"><span data-stu-id="68d1c-116">Constant</span></span>  |<span data-ttu-id="68d1c-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="68d1c-117">Value</span></span>  |<span data-ttu-id="68d1c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="68d1c-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="68d1c-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="68d1c-119">0x80041008</span></span> | <span data-ttu-id="68d1c-120">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="68d1c-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="68d1c-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="68d1c-121">0x80041005</span></span> | <span data-ttu-id="68d1c-122">Wystąpiła niezgodność typów.</span><span class="sxs-lookup"><span data-stu-id="68d1c-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="68d1c-123">0</span><span class="sxs-lookup"><span data-stu-id="68d1c-123">0</span></span> | <span data-ttu-id="68d1c-124">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="68d1c-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="68d1c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68d1c-125">Remarks</span></span>

<span data-ttu-id="68d1c-126">Ta funkcja jest zawijana wywołanie [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="68d1c-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="68d1c-127">Użyj tej funkcji, aby ustawić parametry i wszystkich innych firm innych niż firma`DWORD` lub z systemem innym niż-`QWORD` danych.</span><span class="sxs-lookup"><span data-stu-id="68d1c-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="68d1c-128">Dla typu wartości właściwości `lNumBytes` musi być prawidłowe dane rozmiar określony typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="68d1c-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="68d1c-129">Wartości właściwości ciągu `lNumBytes` musi mieć długość określonego ciągu w bajtach i ciągu musi być parzysta długości w bajtach i znajdować się znakiem null zakończenia.</span><span class="sxs-lookup"><span data-stu-id="68d1c-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="68d1c-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68d1c-130">Requirements</span></span>  
<span data-ttu-id="68d1c-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68d1c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68d1c-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="68d1c-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="68d1c-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="68d1c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d1c-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68d1c-134">See also</span></span>  
[<span data-ttu-id="68d1c-135">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="68d1c-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
