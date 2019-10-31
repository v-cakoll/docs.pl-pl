---
title: GetObjectText — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetObjectText zwraca renderowanie tekstu obiektu w składni MOF.
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
ms.openlocfilehash: 412e1ad503fa0e0b4f813298c0ac96ae80098c06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102453"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="85507-103">GetObjectText, funkcja</span><span class="sxs-lookup"><span data-stu-id="85507-103">GetObjectText function</span></span>
<span data-ttu-id="85507-104">Zwraca renderowanie tekstowe obiektu w składni Managed Object Format (MOF).</span><span class="sxs-lookup"><span data-stu-id="85507-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="85507-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="85507-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="85507-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="85507-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="85507-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="85507-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="85507-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="85507-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="85507-109">podczas Zwykle 0.</span><span class="sxs-lookup"><span data-stu-id="85507-109">[in] Normally 0.</span></span> <span data-ttu-id="85507-110">Jeśli określono `WBEM_FLAG_NO_FLAVORS` (lub 0x1), kwalifikatory są uwzględniane bez informacji o propagacji lub wersji.</span><span class="sxs-lookup"><span data-stu-id="85507-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="85507-111">określoną Wskaźnik do `null` przy wpisie.</span><span class="sxs-lookup"><span data-stu-id="85507-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="85507-112">W przypadku powrotu, nowo przydzieloną `BSTR`, która zawiera wyrenderowanie obiektu przez składnię MOF.</span><span class="sxs-lookup"><span data-stu-id="85507-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="85507-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="85507-113">Return value</span></span>

<span data-ttu-id="85507-114">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="85507-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="85507-115">Stała</span><span class="sxs-lookup"><span data-stu-id="85507-115">Constant</span></span>  |<span data-ttu-id="85507-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="85507-116">Value</span></span>  |<span data-ttu-id="85507-117">Opis</span><span class="sxs-lookup"><span data-stu-id="85507-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="85507-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="85507-118">0x80041001</span></span> | <span data-ttu-id="85507-119">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="85507-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="85507-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="85507-120">0x80041008</span></span> | <span data-ttu-id="85507-121">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="85507-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="85507-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="85507-122">0x80041006</span></span> | <span data-ttu-id="85507-123">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="85507-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="85507-124">0</span><span class="sxs-lookup"><span data-stu-id="85507-124">0</span></span> | <span data-ttu-id="85507-125">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="85507-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="85507-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85507-126">Remarks</span></span>

<span data-ttu-id="85507-127">Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) .</span><span class="sxs-lookup"><span data-stu-id="85507-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="85507-128">Zwrócony tekst MOF nie zawiera wszystkich informacji o obiekcie, ale tylko wystarczające informacje dla kompilatora MOF, aby można było odtworzyć oryginalny obiekt.</span><span class="sxs-lookup"><span data-stu-id="85507-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="85507-129">Na przykład nie są uwzględniane żadne kwalifikatory propagowane ani właściwości klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="85507-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="85507-130">Następujący algorytm służy do rekonstruowania tekstu parametrów metody:</span><span class="sxs-lookup"><span data-stu-id="85507-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="85507-131">Parametry są ponownie sekwencjonowane w kolejności ich wartości identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="85507-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="85507-132">Parametry, które są określone jako `[in]` i `[out]`, są łączone w jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="85507-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="85507-133">`pstrObjectText` musi być wskaźnikiem do `null`, gdy funkcja jest wywoływana; nie może wskazywać ciągu, który jest prawidłowy przed wywołaniem metody, ponieważ wskaźnik nie zostanie cofnięty.</span><span class="sxs-lookup"><span data-stu-id="85507-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="85507-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85507-134">Requirements</span></span>  
<span data-ttu-id="85507-135">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85507-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85507-136">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="85507-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="85507-137">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="85507-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85507-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85507-138">See also</span></span>

- [<span data-ttu-id="85507-139">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="85507-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
