---
title: Funkcja GetQualifierSet (niezarządzany wykaz interfejsów API)
description: Funkcja GetQualifierSet pobiera kwalifikator dla klasy lub wystąpienia.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b50befa4346e17048598afd3d018dbde2fe8572
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458565"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="19c88-103">Funkcja GetQualifierSet</span><span class="sxs-lookup"><span data-stu-id="19c88-103">GetQualifierSet function</span></span>
<span data-ttu-id="19c88-104">Pobiera kwalifikator dla wystąpienia klasy lub definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="19c88-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="19c88-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="19c88-105">Syntax</span></span>  
  
```  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="19c88-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="19c88-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="19c88-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="19c88-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="19c88-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="19c88-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="19c88-109">[out] Uzyskuje wskaźnik interfejsu, który zezwala na dostęp do kwalifikatory klasy obiektu.</span><span class="sxs-lookup"><span data-stu-id="19c88-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="19c88-110">`ppQualSet` nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="19c88-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="19c88-111">Jeśli wystąpi błąd, nowego obiektu nie są zwracane, a wskaźnik myszy pozostanie niezmieniona.</span><span class="sxs-lookup"><span data-stu-id="19c88-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="19c88-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="19c88-112">Return value</span></span>

<span data-ttu-id="19c88-113">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="19c88-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="19c88-114">Stała</span><span class="sxs-lookup"><span data-stu-id="19c88-114">Constant</span></span>  |<span data-ttu-id="19c88-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="19c88-115">Value</span></span>  |<span data-ttu-id="19c88-116">Opis</span><span class="sxs-lookup"><span data-stu-id="19c88-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="19c88-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="19c88-117">0x80041001</span></span> | <span data-ttu-id="19c88-118">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="19c88-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="19c88-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="19c88-119">0x80041002</span></span> | <span data-ttu-id="19c88-120">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="19c88-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="19c88-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="19c88-121">0x80041006</span></span> | <span data-ttu-id="19c88-122">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="19c88-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="19c88-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="19c88-123">0x80041008</span></span> | <span data-ttu-id="19c88-124">Parametr jest `null`.</span><span class="sxs-lookup"><span data-stu-id="19c88-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="19c88-125">0</span><span class="sxs-lookup"><span data-stu-id="19c88-125">0</span></span> | <span data-ttu-id="19c88-126">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="19c88-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="19c88-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19c88-127">Remarks</span></span>

<span data-ttu-id="19c88-128">Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetQualifierSet](https://msdn.microsoft.com/library/aa391451(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="19c88-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](https://msdn.microsoft.com/library/aa391451(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="19c88-129">[Wskaźnika IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) umożliwia wywołującego dodać, edytować lub usunąć kwalifikatory.</span><span class="sxs-lookup"><span data-stu-id="19c88-129">The [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="19c88-130">Takie kwalifikatory dodany, edycji lub usunięty mają zastosowanie do całego wystąpienia lub definicję klasy.</span><span class="sxs-lookup"><span data-stu-id="19c88-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="19c88-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19c88-131">Requirements</span></span>  
<span data-ttu-id="19c88-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19c88-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19c88-133">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="19c88-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="19c88-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="19c88-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c88-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19c88-135">See also</span></span>  
[<span data-ttu-id="19c88-136">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="19c88-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
