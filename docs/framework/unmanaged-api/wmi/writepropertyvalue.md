---
title: WritePropertyValue — funkcja (niezarządzana dokumentacja interfejsu API)
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
ms.openlocfilehash: f02fb3877d55e9f47384b281573202712c29c606
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107289"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="1cc2a-103">WritePropertyValue, funkcja</span><span class="sxs-lookup"><span data-stu-id="1cc2a-103">WritePropertyValue function</span></span>
<span data-ttu-id="1cc2a-104">Zapisuje określoną liczbę bajtów do właściwości identyfikowanej przez uchwyt właściwości.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="1cc2a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1cc2a-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="1cc2a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cc2a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1cc2a-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1cc2a-108">podczas Wskaźnik do wystąpienia [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .</span><span class="sxs-lookup"><span data-stu-id="1cc2a-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="1cc2a-109">podczas Liczba całkowita, która zawiera uchwyt, który identyfikuje tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="1cc2a-110">Dojście można pobrać, wywołując funkcję [GetPropertyHandle](getpropertyhandle.md) .</span><span class="sxs-lookup"><span data-stu-id="1cc2a-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="1cc2a-111">podczas Liczba bajtów zapisywanych w właściwości.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="1cc2a-112">Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="1cc2a-113">określoną Wskaźnik do tablicy bajtów zawierającej dane.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="1cc2a-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1cc2a-114">Return value</span></span>

<span data-ttu-id="1cc2a-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="1cc2a-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1cc2a-116">Stała</span><span class="sxs-lookup"><span data-stu-id="1cc2a-116">Constant</span></span>  |<span data-ttu-id="1cc2a-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="1cc2a-117">Value</span></span>  |<span data-ttu-id="1cc2a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="1cc2a-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1cc2a-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1cc2a-119">0x80041008</span></span> | <span data-ttu-id="1cc2a-120">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="1cc2a-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="1cc2a-121">0x80041005</span></span> | <span data-ttu-id="1cc2a-122">Wystąpił niezgodność typów.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1cc2a-123">0</span><span class="sxs-lookup"><span data-stu-id="1cc2a-123">0</span></span> | <span data-ttu-id="1cc2a-124">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1cc2a-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1cc2a-125">Remarks</span></span>

<span data-ttu-id="1cc2a-126">Ta funkcja otacza wywołanie metody [IWbemClassObject:: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) .</span><span class="sxs-lookup"><span data-stu-id="1cc2a-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="1cc2a-127">Użyj tej funkcji, aby ustawić ciąg i wszystkie inne`DWORD` lub nie`QWORD` dane.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="1cc2a-128">W przypadku wartości właściwości niebędących ciągami `lNumBytes` musi być prawidłowym rozmiarem danych określonego typu właściwości.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="1cc2a-129">W przypadku wartości właściwości ciągu `lNumBytes` musi być długością określonego ciągu w bajtach, a sam ciąg musi mieć długość w bajtach i mieć znak zakończenia o wartości null.</span><span class="sxs-lookup"><span data-stu-id="1cc2a-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="1cc2a-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1cc2a-130">Requirements</span></span>  
<span data-ttu-id="1cc2a-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cc2a-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cc2a-132">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="1cc2a-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1cc2a-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1cc2a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc2a-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cc2a-134">See also</span></span>

- [<span data-ttu-id="1cc2a-135">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="1cc2a-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
