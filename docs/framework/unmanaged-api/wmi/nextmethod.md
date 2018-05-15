---
title: Funkcja NextMethod (niezarządzany wykaz interfejsów API)
description: Funkcja NextMethod pobiera następnej metody w wyliczeniu.
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
ms.openlocfilehash: cd4559663194cb845fb0cc040e1f6739e38caa0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nextmethod-function"></a><span data-ttu-id="87d65-103">Funkcja NextMethod</span><span class="sxs-lookup"><span data-stu-id="87d65-103">NextMethod function</span></span>
<span data-ttu-id="87d65-104">Pobiera dalej w wyliczenie zaczyna się od wywołania metody [BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="87d65-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="87d65-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="87d65-105">Syntax</span></span>  
  
```  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a><span data-ttu-id="87d65-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="87d65-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="87d65-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="87d65-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="87d65-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="87d65-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="87d65-109">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="87d65-109">[in] Reserved.</span></span> <span data-ttu-id="87d65-110">Ten parametr musi wynosić 0.</span><span class="sxs-lookup"><span data-stu-id="87d65-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="87d65-111">[out] Wskaźnik, który wskazuje `null` przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="87d65-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="87d65-112">Gdy funkcja zwraca, nowy adres `BSTR` zawierający nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="87d65-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="87d65-113">[out] Wskaźnik, który otrzymuje wskaźnik [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) zawierający `in` parametry metody.</span><span class="sxs-lookup"><span data-stu-id="87d65-113">[out] A pointer that receives a pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="87d65-114">[out] Wskaźnik, który otrzymuje wskaźnik [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) zawierający `out` parametry metody.</span><span class="sxs-lookup"><span data-stu-id="87d65-114">[out] A pointer that receives a pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="87d65-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="87d65-115">Return value</span></span>

<span data-ttu-id="87d65-116">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="87d65-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="87d65-117">Stała</span><span class="sxs-lookup"><span data-stu-id="87d65-117">Constant</span></span>  |<span data-ttu-id="87d65-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="87d65-118">Value</span></span>  |<span data-ttu-id="87d65-119">Opis</span><span class="sxs-lookup"><span data-stu-id="87d65-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="87d65-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="87d65-120">0x8004101d</span></span> | <span data-ttu-id="87d65-121">Nie znaleziono żadnych wywołanie [ `BeginEnumeration` ](beginenumeration.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="87d65-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="87d65-122">0</span><span class="sxs-lookup"><span data-stu-id="87d65-122">0</span></span> | <span data-ttu-id="87d65-123">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="87d65-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="87d65-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="87d65-124">0x40005</span></span> | <span data-ttu-id="87d65-125">Nie ma żadnych więcej właściwości w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="87d65-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="87d65-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87d65-126">Remarks</span></span>

<span data-ttu-id="87d65-127">Ta funkcja jest zawijana wywołanie [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="87d65-127">This function wraps a call to the [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="87d65-128">Obiekt wywołujący rozpoczyna sekwencji wyliczenie przez wywołanie metody [BeginMethodEnumeration](beginmethodenumeration.md) działać, a następnie wywołuje funkcję [NextMethod], dopóki funkcja zwraca `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="87d65-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="87d65-129">Opcjonalnie, wywołujący zakończeniem sekwencji przez wywołanie metody [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="87d65-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="87d65-130">Obiekt wywołujący może zakończyć wyliczenia wcześniej przez wywołanie metody [EndMethodEnumeration](endmethodenumeration.md) w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="87d65-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="87d65-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="87d65-131">Example</span></span>

<span data-ttu-id="87d65-132">Na przykład C++, zobacz [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="87d65-132">For a C++ example, see the [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="87d65-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87d65-133">Requirements</span></span>  
 <span data-ttu-id="87d65-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87d65-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d65-135">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="87d65-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="87d65-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="87d65-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d65-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87d65-137">See also</span></span>  
[<span data-ttu-id="87d65-138">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="87d65-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
