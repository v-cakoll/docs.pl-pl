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
ms.workload: dotnet
ms.openlocfilehash: 93ba4e59dda4806931ba085f8c63b63a1d8bd797
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="ffea5-103">Funkcja QualifierSet_Get</span><span class="sxs-lookup"><span data-stu-id="ffea5-103">QualifierSet_Get function</span></span>
<span data-ttu-id="ffea5-104">Pobiera określony nazwany kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="ffea5-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ffea5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffea5-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="ffea5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffea5-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="ffea5-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="ffea5-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="ffea5-108">[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ffea5-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="ffea5-109">[in] Nazwa kwalifikatora, którego wartość jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="ffea5-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="ffea5-110">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="ffea5-110">[in] Reserved.</span></span> <span data-ttu-id="ffea5-111">Ten parametr musi wynosić 0.</span><span class="sxs-lookup"><span data-stu-id="ffea5-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="ffea5-112">[out] Gdy to się powiedzie, niepoprawny typ i wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="ffea5-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="ffea5-113">W przypadku niepowodzenia funkcji `VARIANT` wskazywana przez `pVal` nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="ffea5-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="ffea5-114">Jeśli ten parametr ma `null`, parametr będzie ignorowany.</span><span class="sxs-lookup"><span data-stu-id="ffea5-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="ffea5-115">[out] Wskaźnik do DŁUGI odbierająca bitów podtyp kwalifikator dla żądanego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="ffea5-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="ffea5-116">Jeśli informacje o wersji nie jest wymagana, ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="ffea5-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="ffea5-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ffea5-117">Return value</span></span>

<span data-ttu-id="ffea5-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="ffea5-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ffea5-119">Stała</span><span class="sxs-lookup"><span data-stu-id="ffea5-119">Constant</span></span>  |<span data-ttu-id="ffea5-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="ffea5-120">Value</span></span>  |<span data-ttu-id="ffea5-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ffea5-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ffea5-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ffea5-122">0x80041008</span></span> | <span data-ttu-id="ffea5-123">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ffea5-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="ffea5-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ffea5-124">0x80041002</span></span> | <span data-ttu-id="ffea5-125">Określony kwalifikatora nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="ffea5-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ffea5-126">0</span><span class="sxs-lookup"><span data-stu-id="ffea5-126">0</span></span> | <span data-ttu-id="ffea5-127">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ffea5-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ffea5-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffea5-128">Remarks</span></span>

<span data-ttu-id="ffea5-129">Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="ffea5-129">This function wraps a call to the [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ffea5-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffea5-130">Requirements</span></span>  
 <span data-ttu-id="ffea5-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffea5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffea5-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ffea5-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ffea5-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ffea5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffea5-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffea5-134">See also</span></span>  
[<span data-ttu-id="ffea5-135">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="ffea5-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
