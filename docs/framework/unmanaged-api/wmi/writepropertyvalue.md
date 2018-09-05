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
ms.openlocfilehash: f2a4eb444967390492be33b25866de8a93a1698c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518296"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="e7d42-103">WritePropertyValue — funkcja</span><span class="sxs-lookup"><span data-stu-id="e7d42-103">WritePropertyValue function</span></span>
<span data-ttu-id="e7d42-104">Zapisuje określoną liczbę bajtów z właściwością identyfikowane przez dojście właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7d42-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e7d42-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7d42-105">Syntax</span></span>  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="e7d42-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7d42-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e7d42-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="e7d42-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e7d42-108">[in] Wskaźnik do [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7d42-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="e7d42-109">[in] Liczba całkowita, która zawiera uchwyt, który identyfikuje tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="e7d42-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="e7d42-110">Uchwyt może być pobierany przez wywołanie [GetPropertyHandle](getpropertyhandle.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="e7d42-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="e7d42-111">[in] Liczba bajtów zapisywanych do właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7d42-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="e7d42-112">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="e7d42-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="e7d42-113">[out] Wskaźnik do tablicy typu byte, który zawiera dane.</span><span class="sxs-lookup"><span data-stu-id="e7d42-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="e7d42-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e7d42-114">Return value</span></span>

<span data-ttu-id="e7d42-115">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="e7d42-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e7d42-116">Stała</span><span class="sxs-lookup"><span data-stu-id="e7d42-116">Constant</span></span>  |<span data-ttu-id="e7d42-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="e7d42-117">Value</span></span>  |<span data-ttu-id="e7d42-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e7d42-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e7d42-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e7d42-119">0x80041008</span></span> | <span data-ttu-id="e7d42-120">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e7d42-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="e7d42-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="e7d42-121">0x80041005</span></span> | <span data-ttu-id="e7d42-122">Wystąpiła niezgodność typów.</span><span class="sxs-lookup"><span data-stu-id="e7d42-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e7d42-123">0</span><span class="sxs-lookup"><span data-stu-id="e7d42-123">0</span></span> | <span data-ttu-id="e7d42-124">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e7d42-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e7d42-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7d42-125">Remarks</span></span>

<span data-ttu-id="e7d42-126">Ta funkcja zawija wywołanie do [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) metody.</span><span class="sxs-lookup"><span data-stu-id="e7d42-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="e7d42-127">Ta funkcja służy do ciągu i wszystkie inne non -`DWORD` lub -`QWORD` danych.</span><span class="sxs-lookup"><span data-stu-id="e7d42-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="e7d42-128">W przypadku wartości właściwości typu `lNumBytes` musi być prawidłowe dane rozmiar określony typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7d42-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="e7d42-129">Wartości właściwości ciągu `lNumBytes` musi mieć długość określonego ciągu w bajtach i ciągu musi być nawet długości w bajtach wraz z występować znak zakończenia o wartości null.</span><span class="sxs-lookup"><span data-stu-id="e7d42-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7d42-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7d42-130">Requirements</span></span>  
<span data-ttu-id="e7d42-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d42-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d42-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e7d42-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e7d42-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d42-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d42-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7d42-134">See also</span></span>  
[<span data-ttu-id="e7d42-135">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="e7d42-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
