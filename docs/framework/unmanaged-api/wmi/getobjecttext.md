---
title: "Funkcja GetObjectText (niezarządzany wykaz interfejsów API)"
description: "Funkcja GetObjectText zwraca wartość tekstową renderowanie obiektu składnią MOF."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetObjectText
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetObjectText
helpviewer_keywords: GetObjectText function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 27e25a7ab7131f5b1c995c9367de6fe5a6fae592
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="getobjecttext-function"></a><span data-ttu-id="73f88-103">Funkcja GetObjectText</span><span class="sxs-lookup"><span data-stu-id="73f88-103">GetObjectText function</span></span>
<span data-ttu-id="73f88-104">Zwraca tekstową renderowanie obiektu w składni Managed Object Format (MOF).</span><span class="sxs-lookup"><span data-stu-id="73f88-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="73f88-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="73f88-105">Syntax</span></span>  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="73f88-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="73f88-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="73f88-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="73f88-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="73f88-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="73f88-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="73f88-109">[in] Zazwyczaj 0.</span><span class="sxs-lookup"><span data-stu-id="73f88-109">[in] Normally 0.</span></span> <span data-ttu-id="73f88-110">Jeśli `WBEM_FLAG_NO_FLAVORS` (lub 0x1) określono kwalifikatorów są uwzględniane bez informacji o propagację lub wersji.</span><span class="sxs-lookup"><span data-stu-id="73f88-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="73f88-111">[out] Wskaźnik do `null` zapisu.</span><span class="sxs-lookup"><span data-stu-id="73f88-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="73f88-112">Zwraca na, nowo przydzielone `BSTR` zawierający renderowania składnią MOF obiektu.</span><span class="sxs-lookup"><span data-stu-id="73f88-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="73f88-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73f88-113">Return value</span></span>

<span data-ttu-id="73f88-114">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="73f88-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="73f88-115">Stała</span><span class="sxs-lookup"><span data-stu-id="73f88-115">Constant</span></span>  |<span data-ttu-id="73f88-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="73f88-116">Value</span></span>  |<span data-ttu-id="73f88-117">Opis</span><span class="sxs-lookup"><span data-stu-id="73f88-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="73f88-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="73f88-118">0x80041001</span></span> | <span data-ttu-id="73f88-119">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="73f88-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="73f88-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="73f88-120">0x80041008</span></span> | <span data-ttu-id="73f88-121">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="73f88-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="73f88-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="73f88-122">0x80041006</span></span> | <span data-ttu-id="73f88-123">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="73f88-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="73f88-124">0</span><span class="sxs-lookup"><span data-stu-id="73f88-124">0</span></span> | <span data-ttu-id="73f88-125">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="73f88-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="73f88-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73f88-126">Remarks</span></span>

<span data-ttu-id="73f88-127">Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="73f88-127">This function wraps a call to the [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="73f88-128">Tekst MOF zwrócił nie zawiera wszystkich informacji o obiekcie, ale tylko tych informacji dla kompilatora MOF można było ponownie utworzyć obiekt oryginalnego.</span><span class="sxs-lookup"><span data-stu-id="73f88-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="73f88-129">Na przykład nie propagowany kwalifikatory lub właściwości klasy nadrzędnej są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="73f88-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="73f88-130">Następujący algorytm służy do rekonstrukcji tekst parametry metody:</span><span class="sxs-lookup"><span data-stu-id="73f88-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="73f88-131">Parametry są z ponownie określoną kolejnością według ich wartości identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="73f88-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="73f88-132">Parametry, które są określone jako `[in]` i `[out]` są połączone w jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="73f88-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="73f88-133">`pstrObjectText`musi być wskaźnikiem do `null` po wywołaniu funkcji; nie musi wskazywać na ciąg, który jest prawidłowy przed wywołaniem metody, ponieważ wskaźnik myszy zostanie nie można cofnąć alokacji.</span><span class="sxs-lookup"><span data-stu-id="73f88-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="73f88-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73f88-134">Requirements</span></span>  
<span data-ttu-id="73f88-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73f88-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73f88-136">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="73f88-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="73f88-137">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="73f88-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f88-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73f88-138">See also</span></span>  
[<span data-ttu-id="73f88-139">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="73f88-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
