---
title: "Funkcja klonowania (niezarządzany wykaz interfejsów API)"
description: "Funkcja klonowania zwraca nowy obiekt, która jest klonem pełne obecną."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Clone
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Clone
helpviewer_keywords: Clone function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 270150bb674ee7f9a71cf28008c663e3b833600d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="clone-function"></a><span data-ttu-id="a75fb-103">Clone — funkcja</span><span class="sxs-lookup"><span data-stu-id="a75fb-103">Clone function</span></span>
<span data-ttu-id="a75fb-104">Zwraca nowy obiekt, który jest pełny klonowania bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a75fb-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a75fb-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a75fb-105">Syntax</span></span>  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="a75fb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a75fb-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a75fb-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="a75fb-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a75fb-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a75fb-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`ppCopy`  
<span data-ttu-id="a75fb-109">[out] Nowy obiekt, który jest kompletna pojedynczy z `ptr`.</span><span class="sxs-lookup"><span data-stu-id="a75fb-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="a75fb-110">Ten argument nie może być `null` po otrzymaniu kopię bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a75fb-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="a75fb-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a75fb-111">Return value</span></span>

<span data-ttu-id="a75fb-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="a75fb-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a75fb-113">Stała</span><span class="sxs-lookup"><span data-stu-id="a75fb-113">Constant</span></span>  |<span data-ttu-id="a75fb-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="a75fb-114">Value</span></span>  |<span data-ttu-id="a75fb-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a75fb-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="a75fb-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a75fb-116">0x80041001</span></span> | <span data-ttu-id="a75fb-117">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="a75fb-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a75fb-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a75fb-118">0x80041008</span></span> | <span data-ttu-id="a75fb-119">`null`został określony jako parametru, a nie jest dozwolone w ten sposób użycia.</span><span class="sxs-lookup"><span data-stu-id="a75fb-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a75fb-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a75fb-120">0x80041006</span></span> | <span data-ttu-id="a75fb-121">Za mało pamięci jest dostępna w celu sklonowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="a75fb-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a75fb-122">0</span><span class="sxs-lookup"><span data-stu-id="a75fb-122">0</span></span> | <span data-ttu-id="a75fb-123">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a75fb-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a75fb-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a75fb-124">Remarks</span></span>

<span data-ttu-id="a75fb-125">Ta funkcja jest zawijana wywołanie [IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="a75fb-125">This function wraps a call to the [IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="a75fb-126">Sklonowany obiekt to obiekt COM, który ma liczebności referencyjnej równej 1.</span><span class="sxs-lookup"><span data-stu-id="a75fb-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="a75fb-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a75fb-127">Requirements</span></span>  
 <span data-ttu-id="a75fb-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a75fb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a75fb-129">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a75fb-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a75fb-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a75fb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75fb-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a75fb-131">See also</span></span>  
[<span data-ttu-id="a75fb-132">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="a75fb-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
