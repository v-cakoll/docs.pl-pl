---
title: Funkcja GetQualifierSet (odwołanie do niezarządzanego interfejsu API)
description: Funkcja GetQualifierSet pobiera zestaw kwalifikator dla klasy lub wystąpienia.
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
ms.openlocfilehash: 368f0a13871bd48780fa30b370d37157d2724bb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176776"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="f47b2-103">GetQualifierSet, funkcja</span><span class="sxs-lookup"><span data-stu-id="f47b2-103">GetQualifierSet function</span></span>
<span data-ttu-id="f47b2-104">Pobiera zestaw kwalifikator dla wystąpienia klasy lub definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="f47b2-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f47b2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f47b2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [out] IWbemQualifierSet  **ppQualSet
);
```  

## <a name="parameters"></a><span data-ttu-id="f47b2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f47b2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f47b2-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="f47b2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f47b2-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="f47b2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="f47b2-109">[na zewnątrz] Odbiera wskaźnik interfejsu, który umożliwia dostęp do kwalifikatorów obiektu klasy.</span><span class="sxs-lookup"><span data-stu-id="f47b2-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="f47b2-110">`ppQualSet`nie `null`może być .</span><span class="sxs-lookup"><span data-stu-id="f47b2-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="f47b2-111">Jeśli wystąpi błąd, nowy obiekt nie jest zwracany, a wskaźnik pozostaje niezmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="f47b2-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="f47b2-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f47b2-112">Return value</span></span>

<span data-ttu-id="f47b2-113">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="f47b2-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f47b2-114">Stały</span><span class="sxs-lookup"><span data-stu-id="f47b2-114">Constant</span></span>  |<span data-ttu-id="f47b2-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="f47b2-115">Value</span></span>  |<span data-ttu-id="f47b2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f47b2-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="f47b2-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f47b2-117">0x80041001</span></span> | <span data-ttu-id="f47b2-118">Wystąpiła ogólna porażka.</span><span class="sxs-lookup"><span data-stu-id="f47b2-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="f47b2-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f47b2-119">0x80041002</span></span> | <span data-ttu-id="f47b2-120">Określona metoda nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f47b2-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f47b2-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f47b2-121">0x80041006</span></span> | <span data-ttu-id="f47b2-122">Za mało pamięci jest dostępna do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="f47b2-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f47b2-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f47b2-123">0x80041008</span></span> | <span data-ttu-id="f47b2-124">Parametrem `null`jest .</span><span class="sxs-lookup"><span data-stu-id="f47b2-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f47b2-125">0</span><span class="sxs-lookup"><span data-stu-id="f47b2-125">0</span></span> | <span data-ttu-id="f47b2-126">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f47b2-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f47b2-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f47b2-127">Remarks</span></span>

<span data-ttu-id="f47b2-128">Ta funkcja zawija wywołanie [metody IWbemClassObject::GetQualifierSet.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset)</span><span class="sxs-lookup"><span data-stu-id="f47b2-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span>

<span data-ttu-id="f47b2-129">[Wskaźnik IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umożliwia wywołującemu dodawanie, edytowanie lub usuwanie tych kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="f47b2-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="f47b2-130">Takie dodane, edytowane lub usunięte kwalifikatory mają zastosowanie do całej definicji wystąpienia lub klasy.</span><span class="sxs-lookup"><span data-stu-id="f47b2-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="f47b2-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f47b2-131">Requirements</span></span>  
<span data-ttu-id="f47b2-132">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f47b2-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f47b2-133">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f47b2-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f47b2-134">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f47b2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47b2-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f47b2-135">See also</span></span>

- [<span data-ttu-id="f47b2-136">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="f47b2-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
