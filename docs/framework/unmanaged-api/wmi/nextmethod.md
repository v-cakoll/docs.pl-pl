---
title: Funkcja NextMethod (niezarządzany wykaz interfejsów API)
description: Funkcja NextMethod pobiera Następna metoda w wyliczeniu.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a730947b0c962d801975917cdf752136e7221c4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746478"
---
# <a name="nextmethod-function"></a><span data-ttu-id="378ae-103">NextMethod — funkcja</span><span class="sxs-lookup"><span data-stu-id="378ae-103">NextMethod function</span></span>
<span data-ttu-id="378ae-104">Pobiera kolejna metoda wyliczenie, które zaczyna się od wywołania [BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="378ae-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="378ae-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="378ae-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="378ae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="378ae-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="378ae-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="378ae-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="378ae-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="378ae-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="378ae-109">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="378ae-109">[in] Reserved.</span></span> <span data-ttu-id="378ae-110">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="378ae-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="378ae-111">[out] Wskaźnik, który wskazuje na `null` przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="378ae-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="378ae-112">Gdy funkcja zwróci wynik, nowy adres `BSTR` zawierający nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="378ae-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="378ae-113">[out] Wskaźnik, który otrzymuje wskaźnik [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) zawierający `in` parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="378ae-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="378ae-114">[out] Wskaźnik, który otrzymuje wskaźnik [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) zawierający `out` parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="378ae-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="378ae-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="378ae-115">Return value</span></span>

<span data-ttu-id="378ae-116">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="378ae-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="378ae-117">Stała</span><span class="sxs-lookup"><span data-stu-id="378ae-117">Constant</span></span>  |<span data-ttu-id="378ae-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="378ae-118">Value</span></span>  |<span data-ttu-id="378ae-119">Opis</span><span class="sxs-lookup"><span data-stu-id="378ae-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="378ae-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="378ae-120">0x8004101d</span></span> | <span data-ttu-id="378ae-121">Wystąpił brak wywołania [ `BeginEnumeration` ](beginenumeration.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="378ae-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="378ae-122">0</span><span class="sxs-lookup"><span data-stu-id="378ae-122">0</span></span> | <span data-ttu-id="378ae-123">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="378ae-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="378ae-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="378ae-124">0x40005</span></span> | <span data-ttu-id="378ae-125">Nie ma żadnych więcej właściwości w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="378ae-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="378ae-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="378ae-126">Remarks</span></span>

<span data-ttu-id="378ae-127">Ta funkcja zawija wywołanie do [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="378ae-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="378ae-128">Obiekt wywołujący rozpoczyna się sekwencja wyliczenie, wywołując [BeginMethodEnumeration](beginmethodenumeration.md) działać, a następnie wywołuje funkcję [NextMethod], aż funkcja zwróci `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="378ae-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="378ae-129">Opcjonalnie, obiekt wywołujący zakończy sekwencję przez wywołanie metody [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="378ae-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="378ae-130">Obiekt wywołujący może rozwiązać niniejszą wyliczenia wcześnie, wywołując [EndMethodEnumeration](endmethodenumeration.md) w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="378ae-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="378ae-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="378ae-131">Example</span></span>

<span data-ttu-id="378ae-132">Na przykład C++, zobacz [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="378ae-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="378ae-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="378ae-133">Requirements</span></span>  
 <span data-ttu-id="378ae-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="378ae-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="378ae-135">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="378ae-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="378ae-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="378ae-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378ae-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="378ae-137">See also</span></span>

- [<span data-ttu-id="378ae-138">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="378ae-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
