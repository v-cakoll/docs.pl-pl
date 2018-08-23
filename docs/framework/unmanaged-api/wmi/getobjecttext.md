---
title: Funkcja GetObjectText (niezarządzany wykaz interfejsów API)
description: Funkcja GetObjectText zwraca wartość tekstową renderowanie obiektu składnią MOF.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24ba4b37cc8221df4e018d172996c0910ec07f7d
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752261"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="7cb3c-103">Funkcja GetObjectText</span><span class="sxs-lookup"><span data-stu-id="7cb3c-103">GetObjectText function</span></span>
<span data-ttu-id="7cb3c-104">Zwraca tekstową renderowanie obiektu w składni Managed Object Format (MOF).</span><span class="sxs-lookup"><span data-stu-id="7cb3c-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="7cb3c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cb3c-105">Syntax</span></span>  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="7cb3c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cb3c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7cb3c-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7cb3c-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="7cb3c-109">[in] Zazwyczaj 0.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-109">[in] Normally 0.</span></span> <span data-ttu-id="7cb3c-110">Jeśli `WBEM_FLAG_NO_FLAVORS` (lub 0x1) jest określony, kwalifikatory to wiąże się z nim informacje propagację lub wersja.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="7cb3c-111">[out] Wskaźnik do `null` przy uruchamianiu.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="7cb3c-112">Wróć na, nowo przydzielonego `BSTR` zawierający renderowanie składnią MOF obiektu.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="7cb3c-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7cb3c-113">Return value</span></span>

<span data-ttu-id="7cb3c-114">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="7cb3c-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7cb3c-115">Stała</span><span class="sxs-lookup"><span data-stu-id="7cb3c-115">Constant</span></span>  |<span data-ttu-id="7cb3c-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="7cb3c-116">Value</span></span>  |<span data-ttu-id="7cb3c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="7cb3c-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="7cb3c-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="7cb3c-118">0x80041001</span></span> | <span data-ttu-id="7cb3c-119">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7cb3c-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7cb3c-120">0x80041008</span></span> | <span data-ttu-id="7cb3c-121">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="7cb3c-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="7cb3c-122">0x80041006</span></span> | <span data-ttu-id="7cb3c-123">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7cb3c-124">0</span><span class="sxs-lookup"><span data-stu-id="7cb3c-124">0</span></span> | <span data-ttu-id="7cb3c-125">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="7cb3c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cb3c-126">Remarks</span></span>

<span data-ttu-id="7cb3c-127">Ta funkcja zawija wywołanie do [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) metody.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="7cb3c-128">Tekst MOF zwracany nie zawiera wszystkich informacji o obiekcie, ale tylko za mało informacji dla kompilatora MOF można było odtworzyć oryginalnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="7cb3c-129">Na przykład nie propagowany kwalifikatory ani właściwości klasy nadrzędnej, są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="7cb3c-130">Następującego algorytmu jest używana do rekonstrukcji tekst parametry metody:</span><span class="sxs-lookup"><span data-stu-id="7cb3c-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="7cb3c-131">Z ponownie parametry określoną kolejnością zgodnie z kolejnością ich wartości identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="7cb3c-132">Parametry, które są określone jako `[in]` i `[out]` są łączone w pojedynczy parametr.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="7cb3c-133">`pstrObjectText` musi być wskaźnikiem do `null` gdy wywoływana jest funkcja; nie musi wskazywać na ciąg, który jest prawidłowy, przed wywołaniem metody, ponieważ wskaźnik będzie nie można cofnąć alokacji.</span><span class="sxs-lookup"><span data-stu-id="7cb3c-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="7cb3c-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cb3c-134">Requirements</span></span>  
<span data-ttu-id="7cb3c-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cb3c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cb3c-136">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7cb3c-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7cb3c-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7cb3c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb3c-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cb3c-138">See also</span></span>  
[<span data-ttu-id="7cb3c-139">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="7cb3c-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
