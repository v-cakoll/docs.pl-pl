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
ms.openlocfilehash: 75bf52fbf9552dc464d9c646f0a2b1bc01cf89c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193099"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="b29a0-103">GetQualifierSet — funkcja</span><span class="sxs-lookup"><span data-stu-id="b29a0-103">GetQualifierSet function</span></span>
<span data-ttu-id="b29a0-104">Pobiera kwalifikator ustawione dla wystąpienia klasy lub definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="b29a0-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b29a0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b29a0-105">Syntax</span></span>  
  
```  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="b29a0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b29a0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b29a0-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="b29a0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b29a0-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b29a0-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="b29a0-109">[out] Otrzymuje wskaźnik interfejsu, który umożliwia dostęp do kwalifikatory obiektu klasy.</span><span class="sxs-lookup"><span data-stu-id="b29a0-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="b29a0-110">`ppQualSet` nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="b29a0-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="b29a0-111">Jeśli wystąpi błąd, nowy obiekt nie jest zwracana i wskaźnik pozostanie niezmieniona.</span><span class="sxs-lookup"><span data-stu-id="b29a0-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="b29a0-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b29a0-112">Return value</span></span>

<span data-ttu-id="b29a0-113">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="b29a0-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b29a0-114">Stała</span><span class="sxs-lookup"><span data-stu-id="b29a0-114">Constant</span></span>  |<span data-ttu-id="b29a0-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="b29a0-115">Value</span></span>  |<span data-ttu-id="b29a0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b29a0-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="b29a0-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b29a0-117">0x80041001</span></span> | <span data-ttu-id="b29a0-118">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="b29a0-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="b29a0-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="b29a0-119">0x80041002</span></span> | <span data-ttu-id="b29a0-120">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="b29a0-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b29a0-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b29a0-121">0x80041006</span></span> | <span data-ttu-id="b29a0-122">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="b29a0-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b29a0-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b29a0-123">0x80041008</span></span> | <span data-ttu-id="b29a0-124">Parametr jest `null`.</span><span class="sxs-lookup"><span data-stu-id="b29a0-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b29a0-125">0</span><span class="sxs-lookup"><span data-stu-id="b29a0-125">0</span></span> | <span data-ttu-id="b29a0-126">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b29a0-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b29a0-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b29a0-127">Remarks</span></span>

<span data-ttu-id="b29a0-128">Ta funkcja zawija wywołanie do [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) metody.</span><span class="sxs-lookup"><span data-stu-id="b29a0-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span> 

<span data-ttu-id="b29a0-129">[Wskaźnik IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umożliwia obiekt wywołujący, dodawać, edytować lub usuwać kwalifikatory.</span><span class="sxs-lookup"><span data-stu-id="b29a0-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="b29a0-130">Takie kwalifikatory dodano, edytowany lub usuniętych mają zastosowanie do całego wystąpienia lub definicję klasy.</span><span class="sxs-lookup"><span data-stu-id="b29a0-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="b29a0-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b29a0-131">Requirements</span></span>  
<span data-ttu-id="b29a0-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b29a0-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b29a0-133">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b29a0-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b29a0-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b29a0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29a0-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b29a0-135">See also</span></span>

- [<span data-ttu-id="b29a0-136">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="b29a0-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
