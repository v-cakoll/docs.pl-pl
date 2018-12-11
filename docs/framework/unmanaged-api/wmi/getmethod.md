---
title: Funkcja GetMethod (niezarządzany wykaz interfejsów API)
description: Funkcja getmethod — pobiera informacje dotyczące metody.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 133e056663b208f2a0d12f05f31daaca95676dc5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152321"
---
# <a name="getmethod-function"></a><span data-ttu-id="f0667-103">Funkcja GetMethod</span><span class="sxs-lookup"><span data-stu-id="f0667-103">GetMethod function</span></span>
<span data-ttu-id="f0667-104">Pobiera informacje o określonej metody.</span><span class="sxs-lookup"><span data-stu-id="f0667-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f0667-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0667-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="f0667-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0667-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f0667-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="f0667-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f0667-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f0667-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="f0667-109">[in] Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="f0667-109">[in] The method name.</span></span> <span data-ttu-id="f0667-110">Ten parametr nie może być `null` i musi się odnosić do prawidłowego `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="f0667-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="f0667-111">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="f0667-111">[in] Reserved.</span></span> <span data-ttu-id="f0667-112">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="f0667-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="f0667-113">[out] Wskaźnik na adres [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienie, które opisano w paramteers do metody.</span><span class="sxs-lookup"><span data-stu-id="f0667-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="f0667-114">Ten parametr jest ignorowany, jeśli jest równa `null`.</span><span class="sxs-lookup"><span data-stu-id="f0667-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="f0667-115">[out] Wskaźnik na adres [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienie, które opisuje poza parametrów do metody.</span><span class="sxs-lookup"><span data-stu-id="f0667-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="f0667-116">Ten parametr jest ignorowany, jeśli jest równa `null`.</span><span class="sxs-lookup"><span data-stu-id="f0667-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="f0667-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f0667-117">Return value</span></span>

<span data-ttu-id="f0667-118">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="f0667-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f0667-119">Stała</span><span class="sxs-lookup"><span data-stu-id="f0667-119">Constant</span></span>  |<span data-ttu-id="f0667-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="f0667-120">Value</span></span>  |<span data-ttu-id="f0667-121">Opis</span><span class="sxs-lookup"><span data-stu-id="f0667-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="f0667-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f0667-122">0x80041002</span></span> | <span data-ttu-id="f0667-123">Nie znaleziono określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="f0667-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f0667-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f0667-124">0x80041006</span></span> | <span data-ttu-id="f0667-125">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="f0667-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f0667-126">0</span><span class="sxs-lookup"><span data-stu-id="f0667-126">0</span></span> | <span data-ttu-id="f0667-127">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f0667-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f0667-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0667-128">Remarks</span></span>

<span data-ttu-id="f0667-129">Ta funkcja zawija wywołanie do [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="f0667-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="f0667-130">Windows Management można ustawić [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźnik do `null` Jeśli metoda nie ma w parametrów.</span><span class="sxs-lookup"><span data-stu-id="f0667-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="f0667-131">W `ppInSignature` i `ppOutSignature` opisano parametry, wejściowe i wyjściowe odpowiednio właściwości w `IWbemClassObject` wystąpienia klasy systemu [_Parameters](/windows/desktop/WmiSdk/--parameters).</span><span class="sxs-lookup"><span data-stu-id="f0667-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="f0667-132">Właściwości w `ppInsignature` noszą `Param` *n*, gdzie *n* to pozycja parametru w podpisie metody (takie jak `Param1`, `Param2`itp.).</span><span class="sxs-lookup"><span data-stu-id="f0667-132">The properties in `ppInsignature` are named `Param`*n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="f0667-133">Właściwości w `ppOutSignature` są również nazywane `Param` *n*, i wartość zwracaną nosi nazwę `ReturnValue`.</span><span class="sxs-lookup"><span data-stu-id="f0667-133">The properties in `ppOutSignature` are also named `Param`*n*, and the return value is named `ReturnValue`.</span></span> <span data-ttu-id="f0667-134">Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [metoda IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="f0667-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="f0667-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0667-135">Requirements</span></span>  
<span data-ttu-id="f0667-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0667-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0667-137">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f0667-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f0667-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f0667-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0667-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0667-139">See also</span></span>  
[<span data-ttu-id="f0667-140">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="f0667-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
