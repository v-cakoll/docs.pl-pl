---
title: NextMethod, funkcja (odwołanie do interfejsu API niezarządzanego)
description: NextMethod Funkcja pobiera następną metodę w wyliczenia.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 36acd6135110a8865bd8efdda628c352c01b4f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174930"
---
# <a name="nextmethod-function"></a><span data-ttu-id="6acb1-103">NextMetoda, funkcja</span><span class="sxs-lookup"><span data-stu-id="6acb1-103">NextMethod function</span></span>
<span data-ttu-id="6acb1-104">Pobiera następną metodę w wyliczeniu, która rozpoczyna się od wywołania [BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6acb1-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6acb1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6acb1-105">Syntax</span></span>  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```  

## <a name="parameters"></a><span data-ttu-id="6acb1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6acb1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6acb1-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="6acb1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6acb1-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="6acb1-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="6acb1-109">[w] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="6acb1-109">[in] Reserved.</span></span> <span data-ttu-id="6acb1-110">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="6acb1-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="6acb1-111">[na zewnątrz] Wskaźnik wskazujący `null` przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="6acb1-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="6acb1-112">Gdy funkcja zwraca, adres nowego, `BSTR` który zawiera nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="6acb1-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span>

`ppSignatureIn`  
<span data-ttu-id="6acb1-113">[na zewnątrz] Wskaźnik, który odbiera wskaźnik do [IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) który zawiera `in` parametry dla metody.</span><span class="sxs-lookup"><span data-stu-id="6acb1-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span>

`ppSignatureOut`  
<span data-ttu-id="6acb1-114">[na zewnątrz] Wskaźnik, który odbiera wskaźnik do [IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) który zawiera `out` parametry dla metody.</span><span class="sxs-lookup"><span data-stu-id="6acb1-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="6acb1-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6acb1-115">Return value</span></span>

<span data-ttu-id="6acb1-116">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="6acb1-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6acb1-117">Stały</span><span class="sxs-lookup"><span data-stu-id="6acb1-117">Constant</span></span>  |<span data-ttu-id="6acb1-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="6acb1-118">Value</span></span>  |<span data-ttu-id="6acb1-119">Opis</span><span class="sxs-lookup"><span data-stu-id="6acb1-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="6acb1-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="6acb1-120">0x8004101d</span></span> | <span data-ttu-id="6acb1-121">Nie było żadnego [`BeginEnumeration`](beginenumeration.md) wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="6acb1-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="6acb1-122">0</span><span class="sxs-lookup"><span data-stu-id="6acb1-122">0</span></span> | <span data-ttu-id="6acb1-123">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6acb1-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="6acb1-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="6acb1-124">0x40005</span></span> | <span data-ttu-id="6acb1-125">Nie ma więcej właściwości w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="6acb1-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="6acb1-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6acb1-126">Remarks</span></span>

<span data-ttu-id="6acb1-127">Ta funkcja zawija wywołanie [metody IWbemClassObject::NextMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)</span><span class="sxs-lookup"><span data-stu-id="6acb1-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="6acb1-128">Wywołujący rozpoczyna sekwencję wyliczenia, wywołując [BeginMethodEnumeration,](beginmethodenumeration.md) a następnie wywołuje funkcję [NextMethod], aż funkcja powróci `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="6acb1-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="6acb1-129">Opcjonalnie wywołujący kończy sekwencję, wywołując [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6acb1-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="6acb1-130">Wywołujący może zakończyć wyliczenie wcześnie wywołując [EndMethodEnumeration](endmethodenumeration.md) w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="6acb1-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="6acb1-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="6acb1-131">Example</span></span>

<span data-ttu-id="6acb1-132">Przykład C++ można znaleźć w metodzie [IWbemClassObject::NextMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)</span><span class="sxs-lookup"><span data-stu-id="6acb1-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6acb1-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6acb1-133">Requirements</span></span>  
 <span data-ttu-id="6acb1-134">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6acb1-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6acb1-135">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6acb1-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6acb1-136">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6acb1-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6acb1-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6acb1-137">See also</span></span>

- [<span data-ttu-id="6acb1-138">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="6acb1-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
