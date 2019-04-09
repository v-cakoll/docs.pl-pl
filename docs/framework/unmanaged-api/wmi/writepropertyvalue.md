---
title: Funkcja WritePropertyValue (niezarządzany wykaz interfejsów API)
description: Funkcja WritePropertyValue zapisuje bajty do właściwości.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a98103367f497b18f9b8fbd61a37abf9816b8356
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107942"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="4c557-103">WritePropertyValue — funkcja</span><span class="sxs-lookup"><span data-stu-id="4c557-103">WritePropertyValue function</span></span>
<span data-ttu-id="4c557-104">Zapisuje określoną liczbę bajtów z właściwością identyfikowane przez dojście właściwości.</span><span class="sxs-lookup"><span data-stu-id="4c557-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4c557-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c557-105">Syntax</span></span>  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="4c557-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c557-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4c557-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="4c557-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4c557-108">[in] Wskaźnik do [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4c557-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="4c557-109">[in] Liczba całkowita, która zawiera uchwyt, który identyfikuje tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="4c557-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="4c557-110">Uchwyt może być pobierany przez wywołanie [GetPropertyHandle](getpropertyhandle.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="4c557-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="4c557-111">[in] Liczba bajtów zapisywanych do właściwości.</span><span class="sxs-lookup"><span data-stu-id="4c557-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="4c557-112">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="4c557-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="4c557-113">[out] Wskaźnik do tablicy typu byte, który zawiera dane.</span><span class="sxs-lookup"><span data-stu-id="4c557-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c557-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4c557-114">Return value</span></span>

<span data-ttu-id="4c557-115">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="4c557-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4c557-116">Stała</span><span class="sxs-lookup"><span data-stu-id="4c557-116">Constant</span></span>  |<span data-ttu-id="4c557-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c557-117">Value</span></span>  |<span data-ttu-id="4c557-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4c557-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4c557-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4c557-119">0x80041008</span></span> | <span data-ttu-id="4c557-120">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="4c557-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="4c557-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="4c557-121">0x80041005</span></span> | <span data-ttu-id="4c557-122">Wystąpiła niezgodność typów.</span><span class="sxs-lookup"><span data-stu-id="4c557-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4c557-123">0</span><span class="sxs-lookup"><span data-stu-id="4c557-123">0</span></span> | <span data-ttu-id="4c557-124">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4c557-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4c557-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c557-125">Remarks</span></span>

<span data-ttu-id="4c557-126">Ta funkcja zawija wywołanie do [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) metody.</span><span class="sxs-lookup"><span data-stu-id="4c557-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="4c557-127">Ta funkcja służy do ciągu i wszystkie inne non -`DWORD` lub -`QWORD` danych.</span><span class="sxs-lookup"><span data-stu-id="4c557-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="4c557-128">W przypadku wartości właściwości typu `lNumBytes` musi być prawidłowe dane rozmiar określony typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="4c557-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="4c557-129">Wartości właściwości ciągu `lNumBytes` musi mieć długość określonego ciągu w bajtach i ciągu musi być nawet długości w bajtach wraz z występować znak zakończenia o wartości null.</span><span class="sxs-lookup"><span data-stu-id="4c557-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c557-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c557-130">Requirements</span></span>  
<span data-ttu-id="4c557-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c557-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c557-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4c557-132">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="4c557-133">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4c557-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4c557-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c557-134">See also</span></span>

- [<span data-ttu-id="4c557-135">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="4c557-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
