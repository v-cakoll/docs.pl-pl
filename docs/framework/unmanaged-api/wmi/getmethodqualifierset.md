---
title: "Funkcja GetMethodQualifierSet (niezarządzany wykaz interfejsów API)"
description: Funkcja GetMethodQualifierSet pobiera metody kwalifikatora zestawu.
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodQualifierSet
helpviewer_keywords: GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79a19d3bb40dd4d435bd7cf97eb0b4071020648e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="84c5b-103">Funkcja GetMethodQualifierSet</span><span class="sxs-lookup"><span data-stu-id="84c5b-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="84c5b-104">Pobiera kwalifikator ustawić dla określonej metody.</span><span class="sxs-lookup"><span data-stu-id="84c5b-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="84c5b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="84c5b-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="84c5b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="84c5b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="84c5b-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="84c5b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="84c5b-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="84c5b-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="84c5b-109">[in] Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="84c5b-109">[in] The method  name.</span></span> <span data-ttu-id="84c5b-110">`wszMethod`musi wskazywać prawidłowe `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="84c5b-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="84c5b-111">[out] Uzyskuje wskaźnik interfejsu, który zezwala na dostęp do kwalifikatory metody.</span><span class="sxs-lookup"><span data-stu-id="84c5b-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="84c5b-112">`ppQualSet`nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="84c5b-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="84c5b-113">Jeśli wystąpi błąd, nowego obiektu nie są zwracane, a wskaźnik ma ustawioną wartość wskaż `null`.</span><span class="sxs-lookup"><span data-stu-id="84c5b-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="84c5b-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="84c5b-114">Return value</span></span>

<span data-ttu-id="84c5b-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="84c5b-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="84c5b-116">Stała</span><span class="sxs-lookup"><span data-stu-id="84c5b-116">Constant</span></span>  |<span data-ttu-id="84c5b-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="84c5b-117">Value</span></span>  |<span data-ttu-id="84c5b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="84c5b-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="84c5b-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="84c5b-119">0x80041002</span></span> | <span data-ttu-id="84c5b-120">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="84c5b-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="84c5b-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="84c5b-121">0x80041008</span></span> | <span data-ttu-id="84c5b-122">Parametr jest `null`.</span><span class="sxs-lookup"><span data-stu-id="84c5b-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="84c5b-123">0</span><span class="sxs-lookup"><span data-stu-id="84c5b-123">0</span></span> | <span data-ttu-id="84c5b-124">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="84c5b-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="84c5b-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84c5b-125">Remarks</span></span>

<span data-ttu-id="84c5b-126">Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="84c5b-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="84c5b-127">Wywołanie tej funkcji jest obsługiwana tylko wtedy, gdy bieżący obiekt jest definicję klasy modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="84c5b-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="84c5b-128">Metoda manipulowania nie jest dostępna dla [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters wskazujące wystąpienia modelu CIM.</span><span class="sxs-lookup"><span data-stu-id="84c5b-128">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="84c5b-129">Ponieważ każda metoda może mieć własną kwalifikatory [wskaźnika IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) umożliwia wywołującego dodać, edytować lub usunąć kwalifikatory.</span><span class="sxs-lookup"><span data-stu-id="84c5b-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="84c5b-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84c5b-130">Requirements</span></span>  
<span data-ttu-id="84c5b-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84c5b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84c5b-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="84c5b-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="84c5b-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="84c5b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c5b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84c5b-134">See also</span></span>  
[<span data-ttu-id="84c5b-135">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="84c5b-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
