---
title: WritePropertyValue, funkcja (odwołanie do interfejsu API niezarządzanego)
description: WritePropertyValue funkcja zapisuje bajty do właściwości.
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
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174839"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="f244e-103">WritePropertyValue, funkcja</span><span class="sxs-lookup"><span data-stu-id="f244e-103">WritePropertyValue function</span></span>
<span data-ttu-id="f244e-104">Zapisuje określoną liczbę bajtów do właściwości identyfikowanej przez dojście do właściwości.</span><span class="sxs-lookup"><span data-stu-id="f244e-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f244e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f244e-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="f244e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f244e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f244e-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="f244e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f244e-108">[w] Wskaźnik do wystąpienia [IWbemObjectAccess.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)</span><span class="sxs-lookup"><span data-stu-id="f244e-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="f244e-109">[w] Liczba całkowita zawierająca dojście identyfikujące tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="f244e-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="f244e-110">Dojście można pobrać, wywołując [Funkcję GetPropertyHandle.](getpropertyhandle.md)</span><span class="sxs-lookup"><span data-stu-id="f244e-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="f244e-111">[w] Liczba bajtów zapisywanych we właściwości.</span><span class="sxs-lookup"><span data-stu-id="f244e-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="f244e-112">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f244e-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="f244e-113">`pHandle`[na zewnątrz] Wskaźnik do tablicy bajtów, która zawiera dane.</span><span class="sxs-lookup"><span data-stu-id="f244e-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="f244e-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f244e-114">Return value</span></span>

<span data-ttu-id="f244e-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="f244e-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f244e-116">Stały</span><span class="sxs-lookup"><span data-stu-id="f244e-116">Constant</span></span>  |<span data-ttu-id="f244e-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="f244e-117">Value</span></span>  |<span data-ttu-id="f244e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="f244e-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f244e-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f244e-119">0x80041008</span></span> | <span data-ttu-id="f244e-120">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f244e-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="f244e-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="f244e-121">0x80041005</span></span> | <span data-ttu-id="f244e-122">Wystąpił niezgodność typu.</span><span class="sxs-lookup"><span data-stu-id="f244e-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f244e-123">0</span><span class="sxs-lookup"><span data-stu-id="f244e-123">0</span></span> | <span data-ttu-id="f244e-124">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f244e-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f244e-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f244e-125">Remarks</span></span>

<span data-ttu-id="f244e-126">Ta funkcja zawija wywołanie metody [IWbemClassObject::WritePropertyValue.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)</span><span class="sxs-lookup"><span data-stu-id="f244e-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="f244e-127">Ta funkcja służy do ustawiania`DWORD` ciągu i`QWORD` wszystkich innych danych innych niż lub innych.</span><span class="sxs-lookup"><span data-stu-id="f244e-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="f244e-128">Dla wartości właściwości nonstring musi `lNumBytes` być poprawny rozmiar danych określonego typu właściwości.</span><span class="sxs-lookup"><span data-stu-id="f244e-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="f244e-129">Dla wartości właściwości `lNumBytes` ciągu musi być długość określonego ciągu w bajtach, a sam ciąg musi mieć równą długość w bajtach i być następuje ze znakiem zakończenia zerowego.</span><span class="sxs-lookup"><span data-stu-id="f244e-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="f244e-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f244e-130">Requirements</span></span>  
<span data-ttu-id="f244e-131">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f244e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f244e-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f244e-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f244e-133">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f244e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f244e-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f244e-134">See also</span></span>

- [<span data-ttu-id="f244e-135">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="f244e-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
