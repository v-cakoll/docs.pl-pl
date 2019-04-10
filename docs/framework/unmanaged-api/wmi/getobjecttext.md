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
ms.openlocfilehash: d34cb399ac0e8780c442eeb2e95cebfd0a22ca02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208322"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="37f10-103">GetObjectText, funkcja</span><span class="sxs-lookup"><span data-stu-id="37f10-103">GetObjectText function</span></span>
<span data-ttu-id="37f10-104">Zwraca tekstową renderowanie obiektu w składni Managed Object Format (MOF).</span><span class="sxs-lookup"><span data-stu-id="37f10-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="37f10-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="37f10-105">Syntax</span></span>  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="37f10-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="37f10-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="37f10-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="37f10-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="37f10-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="37f10-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="37f10-109">[in] Zazwyczaj 0.</span><span class="sxs-lookup"><span data-stu-id="37f10-109">[in] Normally 0.</span></span> <span data-ttu-id="37f10-110">Jeśli `WBEM_FLAG_NO_FLAVORS` (lub 0x1) jest określony, kwalifikatory to wiąże się z nim informacje propagację lub wersja.</span><span class="sxs-lookup"><span data-stu-id="37f10-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="37f10-111">[out] Wskaźnik do `null` przy uruchamianiu.</span><span class="sxs-lookup"><span data-stu-id="37f10-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="37f10-112">Wróć na, nowo przydzielonego `BSTR` zawierający renderowanie składnią MOF obiektu.</span><span class="sxs-lookup"><span data-stu-id="37f10-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="37f10-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="37f10-113">Return value</span></span>

<span data-ttu-id="37f10-114">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="37f10-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="37f10-115">Stała</span><span class="sxs-lookup"><span data-stu-id="37f10-115">Constant</span></span>  |<span data-ttu-id="37f10-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="37f10-116">Value</span></span>  |<span data-ttu-id="37f10-117">Opis</span><span class="sxs-lookup"><span data-stu-id="37f10-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="37f10-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="37f10-118">0x80041001</span></span> | <span data-ttu-id="37f10-119">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="37f10-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="37f10-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="37f10-120">0x80041008</span></span> | <span data-ttu-id="37f10-121">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="37f10-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="37f10-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="37f10-122">0x80041006</span></span> | <span data-ttu-id="37f10-123">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="37f10-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="37f10-124">0</span><span class="sxs-lookup"><span data-stu-id="37f10-124">0</span></span> | <span data-ttu-id="37f10-125">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="37f10-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="37f10-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37f10-126">Remarks</span></span>

<span data-ttu-id="37f10-127">Ta funkcja zawija wywołanie do [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) metody.</span><span class="sxs-lookup"><span data-stu-id="37f10-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="37f10-128">Tekst MOF zwracany nie zawiera wszystkich informacji o obiekcie, ale tylko za mało informacji dla kompilatora MOF można było odtworzyć oryginalnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="37f10-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="37f10-129">Na przykład nie propagowany kwalifikatory ani właściwości klasy nadrzędnej, są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="37f10-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="37f10-130">Następującego algorytmu jest używana do rekonstrukcji tekst parametry metody:</span><span class="sxs-lookup"><span data-stu-id="37f10-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="37f10-131">Z ponownie parametry określoną kolejnością zgodnie z kolejnością ich wartości identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="37f10-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="37f10-132">Parametry, które są określone jako `[in]` i `[out]` są łączone w pojedynczy parametr.</span><span class="sxs-lookup"><span data-stu-id="37f10-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
`pstrObjectText` <span data-ttu-id="37f10-133">musi być wskaźnikiem do `null` gdy wywoływana jest funkcja; nie musi wskazywać na ciąg, który jest prawidłowy, przed wywołaniem metody, ponieważ wskaźnik będzie nie można cofnąć alokacji.</span><span class="sxs-lookup"><span data-stu-id="37f10-133">must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="37f10-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37f10-134">Requirements</span></span>  
<span data-ttu-id="37f10-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37f10-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37f10-136">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="37f10-136">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="37f10-137">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="37f10-137">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="37f10-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37f10-138">See also</span></span>

- [<span data-ttu-id="37f10-139">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="37f10-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
