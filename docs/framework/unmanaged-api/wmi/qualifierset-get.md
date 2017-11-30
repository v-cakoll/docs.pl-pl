---
title: "Funkcja QualifierSet_Get (niezarządzany wykaz interfejsów API)"
description: Funkcja QualifierSet_Get pobiera nazwanego kwalifikatora.
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Get
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Get
helpviewer_keywords: QualifierSet_Get function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aaf5de5b8e16ee2f96c7bc29dbb09f93298dd185
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="e5a5f-103">Funkcja QualifierSet_Get</span><span class="sxs-lookup"><span data-stu-id="e5a5f-103">QualifierSet_Get function</span></span>
<span data-ttu-id="e5a5f-104">Pobiera określony nazwany kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e5a5f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5a5f-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="e5a5f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5a5f-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="e5a5f-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="e5a5f-108">[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="e5a5f-109">[in] Nazwa kwalifikatora, którego wartość jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="e5a5f-110">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-110">[in] Reserved.</span></span> <span data-ttu-id="e5a5f-111">Ten parametr musi wynosić 0.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="e5a5f-112">[out] Gdy to się powiedzie, niepoprawny typ i wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="e5a5f-113">W przypadku niepowodzenia funkcji `VARIANT` wskazywana przez `pVal` nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="e5a5f-114">Jeśli ten parametr ma `null`, parametr będzie ignorowany.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="e5a5f-115">[out] Wskaźnik do DŁUGI odbierająca bitów podtyp kwalifikator dla żądanego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="e5a5f-116">Jeśli informacje o wersji nie jest wymagana, ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e5a5f-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e5a5f-117">Return value</span></span>

<span data-ttu-id="e5a5f-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="e5a5f-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e5a5f-119">Stała</span><span class="sxs-lookup"><span data-stu-id="e5a5f-119">Constant</span></span>  |<span data-ttu-id="e5a5f-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="e5a5f-120">Value</span></span>  |<span data-ttu-id="e5a5f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="e5a5f-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e5a5f-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e5a5f-122">0x80041008</span></span> | <span data-ttu-id="e5a5f-123">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e5a5f-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e5a5f-124">0x80041002</span></span> | <span data-ttu-id="e5a5f-125">Określony kwalifikatora nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e5a5f-126">0</span><span class="sxs-lookup"><span data-stu-id="e5a5f-126">0</span></span> | <span data-ttu-id="e5a5f-127">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e5a5f-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5a5f-128">Remarks</span></span>

<span data-ttu-id="e5a5f-129">Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="e5a5f-129">This function wraps a call to the [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5a5f-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5a5f-130">Requirements</span></span>  
 <span data-ttu-id="e5a5f-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5a5f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5a5f-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e5a5f-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e5a5f-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5a5f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a5f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5a5f-134">See also</span></span>  
[<span data-ttu-id="e5a5f-135">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="e5a5f-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
