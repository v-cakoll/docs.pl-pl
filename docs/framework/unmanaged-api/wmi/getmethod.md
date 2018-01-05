---
title: "GetMethod — funkcja (niezarządzany wykaz interfejsów API)"
description: "Funkcja GetMethod pobiera informacje dotyczące metody."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethod
helpviewer_keywords: GetMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f22a2dfa7aae411cac960cbad2017718df8057e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getmethod-function"></a><span data-ttu-id="4fa80-103">GetMethod — funkcja</span><span class="sxs-lookup"><span data-stu-id="4fa80-103">GetMethod function</span></span>
<span data-ttu-id="4fa80-104">Pobiera informacje o określonej metody.</span><span class="sxs-lookup"><span data-stu-id="4fa80-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4fa80-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fa80-105">Syntax</span></span>  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="4fa80-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fa80-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4fa80-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="4fa80-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4fa80-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4fa80-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="4fa80-109">[in] Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="4fa80-109">[in] The method name.</span></span> <span data-ttu-id="4fa80-110">Ten parametr nie może być `null` i musi wskazywać prawidłowy `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="4fa80-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="4fa80-111">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="4fa80-111">[in] Reserved.</span></span> <span data-ttu-id="4fa80-112">Ten parametr musi wynosić 0.</span><span class="sxs-lookup"><span data-stu-id="4fa80-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="4fa80-113">[out] Wskaźnik do adresu [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienie, które opisano w paramteers do metody.</span><span class="sxs-lookup"><span data-stu-id="4fa80-113">[out] A pointer to the address of an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="4fa80-114">Ten parametr jest ignorowana, jeśli jest ustawiona na `null`.</span><span class="sxs-lookup"><span data-stu-id="4fa80-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="4fa80-115">[out] Wskaźnik do adresu [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienie, które opisano parametry wyjściowe metody.</span><span class="sxs-lookup"><span data-stu-id="4fa80-115">[out] A pointer to the address of an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="4fa80-116">Ten parametr jest ignorowana, jeśli jest ustawiona na `null`.</span><span class="sxs-lookup"><span data-stu-id="4fa80-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="4fa80-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4fa80-117">Return value</span></span>

<span data-ttu-id="4fa80-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="4fa80-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4fa80-119">Stała</span><span class="sxs-lookup"><span data-stu-id="4fa80-119">Constant</span></span>  |<span data-ttu-id="4fa80-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="4fa80-120">Value</span></span>  |<span data-ttu-id="4fa80-121">Opis</span><span class="sxs-lookup"><span data-stu-id="4fa80-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="4fa80-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4fa80-122">0x80041002</span></span> | <span data-ttu-id="4fa80-123">Nie znaleziono określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="4fa80-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4fa80-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4fa80-124">0x80041006</span></span> | <span data-ttu-id="4fa80-125">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="4fa80-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4fa80-126">0</span><span class="sxs-lookup"><span data-stu-id="4fa80-126">0</span></span> | <span data-ttu-id="4fa80-127">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4fa80-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4fa80-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4fa80-128">Remarks</span></span>

<span data-ttu-id="4fa80-129">Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="4fa80-129">This function wraps a call to the [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="4fa80-130">Zarządzanie systemem Windows można ustawić [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wskaźnik do `null` Jeśli metoda nie ma w parametrów.</span><span class="sxs-lookup"><span data-stu-id="4fa80-130">Windows Management can set the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="4fa80-131">W `ppInSignature` i `ppOutSignature` opisano parametry, wejściowe i wyjściowe odpowiednio właściwości w `IWbemClassObject` wystąpienia klasy systemu [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="4fa80-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx).</span></span> <span data-ttu-id="4fa80-132">Właściwości w `ppInsignature` są nazywane **Param***n*, gdzie  *n*  to pozycja parametru w podpisie metody (np. jako `Param1`, `Param2`itp.).</span><span class="sxs-lookup"><span data-stu-id="4fa80-132">The properties in `ppInsignature` are named **Param***n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="4fa80-133">Właściwości w `ppOutSignature` są również nazywane **Param***n*, i nosi nazwę wartości zwracanej **ReturnValue**.</span><span class="sxs-lookup"><span data-stu-id="4fa80-133">The properties in `ppOutSignature` are also named **Param***n*, and the return value is named **ReturnValue**.</span></span> <span data-ttu-id="4fa80-134">Aby uzyskać więcej informacji i przykład zobacz [metody IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="4fa80-134">For more information and an example, see [IWbemClassObject::GetMethod method](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="4fa80-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4fa80-135">Requirements</span></span>  
<span data-ttu-id="4fa80-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fa80-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fa80-137">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4fa80-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4fa80-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4fa80-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa80-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fa80-139">See also</span></span>  
[<span data-ttu-id="4fa80-140">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="4fa80-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
