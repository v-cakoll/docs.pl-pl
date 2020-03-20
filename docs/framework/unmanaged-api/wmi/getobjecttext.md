---
title: GetObjectText, funkcja (odwołanie do niezarządzanego interfejsu API)
description: Funkcja GetObjectText zwraca teksturowane renderowanie obiektu w składni MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6881125760e0f1dc38e6b01917d5829edc95e3ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176789"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="8d69e-103">GetObjectText, funkcja</span><span class="sxs-lookup"><span data-stu-id="8d69e-103">GetObjectText function</span></span>
<span data-ttu-id="8d69e-104">Zwraca teksturowane renderowanie obiektu w składni formatu obiektów zarządzanych (MOF).</span><span class="sxs-lookup"><span data-stu-id="8d69e-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="8d69e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d69e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a><span data-ttu-id="8d69e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d69e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8d69e-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="8d69e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8d69e-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="8d69e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="8d69e-109">[w] Normalnie 0.</span><span class="sxs-lookup"><span data-stu-id="8d69e-109">[in] Normally 0.</span></span> <span data-ttu-id="8d69e-110">Jeśli `WBEM_FLAG_NO_FLAVORS` (lub 0x1) jest określony, kwalifikatory są uwzględniane bez propagacji lub informacji o smaku.</span><span class="sxs-lookup"><span data-stu-id="8d69e-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

<span data-ttu-id="8d69e-111">`pstrObjectText`[na zewnątrz] Wskaźnik do `null` wpisu przy wprowadzaniu.</span><span class="sxs-lookup"><span data-stu-id="8d69e-111">`pstrObjectText` [out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="8d69e-112">Po zwrocie nowo `BSTR` przydzielone, który zawiera renderowania składni MOF obiektu.</span><span class="sxs-lookup"><span data-stu-id="8d69e-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="8d69e-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8d69e-113">Return value</span></span>

<span data-ttu-id="8d69e-114">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="8d69e-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8d69e-115">Stały</span><span class="sxs-lookup"><span data-stu-id="8d69e-115">Constant</span></span>  |<span data-ttu-id="8d69e-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="8d69e-116">Value</span></span>  |<span data-ttu-id="8d69e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8d69e-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="8d69e-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8d69e-118">0x80041001</span></span> | <span data-ttu-id="8d69e-119">Wystąpiła ogólna porażka.</span><span class="sxs-lookup"><span data-stu-id="8d69e-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8d69e-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8d69e-120">0x80041008</span></span> | <span data-ttu-id="8d69e-121">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8d69e-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8d69e-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8d69e-122">0x80041006</span></span> | <span data-ttu-id="8d69e-123">Za mało pamięci jest dostępna do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="8d69e-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8d69e-124">0</span><span class="sxs-lookup"><span data-stu-id="8d69e-124">0</span></span> | <span data-ttu-id="8d69e-125">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8d69e-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8d69e-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d69e-126">Remarks</span></span>

<span data-ttu-id="8d69e-127">Ta funkcja zawija wywołanie [metody IWbemClassObject::GetObjectText.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)</span><span class="sxs-lookup"><span data-stu-id="8d69e-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="8d69e-128">Zwrócony tekst MOF nie zawiera wszystkich informacji o obiekcie, ale tylko wystarczającą ilość informacji dla kompilatora MOF, aby móc odtworzyć oryginalny obiekt.</span><span class="sxs-lookup"><span data-stu-id="8d69e-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="8d69e-129">Na przykład nie propagowane kwalifikatorów lub właściwości klasy nadrzędnej są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="8d69e-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="8d69e-130">Następujący algorytm jest używany do rekonstrukcji tekstu parametrów metody:</span><span class="sxs-lookup"><span data-stu-id="8d69e-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="8d69e-131">Parametry są ponownie sekwencjonowane w kolejności ich wartości identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="8d69e-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="8d69e-132">Parametry, które `[in]` są `[out]` określone jako i są łączone w jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="8d69e-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>

<span data-ttu-id="8d69e-133">`pstrObjectText`musi być wskaźnikiem `null` do, gdy funkcja jest wywoływana; nie może wskazywać na ciąg, który jest prawidłowy przed wywołaniem metody, ponieważ wskaźnik nie zostanie cofnięty.</span><span class="sxs-lookup"><span data-stu-id="8d69e-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d69e-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d69e-134">Requirements</span></span>  
<span data-ttu-id="8d69e-135">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d69e-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d69e-136">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8d69e-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8d69e-137">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8d69e-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d69e-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d69e-138">See also</span></span>

- [<span data-ttu-id="8d69e-139">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="8d69e-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
