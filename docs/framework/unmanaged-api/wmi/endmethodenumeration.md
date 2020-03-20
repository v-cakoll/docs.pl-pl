---
title: EndMethodEnumeration, funkcja (odwołanie do interfejsu API niezarządzanego)
description: EndMethodEnumeration Funkcja kończy sekwencję wyliczenia metody.
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 63667d0668f905ded2aedd961be0d1831faf838c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175008"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="73a4f-103">EndMethodEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="73a4f-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="73a4f-104">Kończy sekwencję wyliczenia rozpoczętą wywołaniem [funkcji BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="73a4f-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="73a4f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="73a4f-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="73a4f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="73a4f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="73a4f-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="73a4f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="73a4f-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="73a4f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="73a4f-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73a4f-109">Return value</span></span>

<span data-ttu-id="73a4f-110">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="73a4f-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="73a4f-111">Stały</span><span class="sxs-lookup"><span data-stu-id="73a4f-111">Constant</span></span>  |<span data-ttu-id="73a4f-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="73a4f-112">Value</span></span>  |<span data-ttu-id="73a4f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="73a4f-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="73a4f-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="73a4f-114">0x8004101d</span></span> | <span data-ttu-id="73a4f-115">Wystąpił błąd wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="73a4f-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="73a4f-116">0</span><span class="sxs-lookup"><span data-stu-id="73a4f-116">0</span></span> | <span data-ttu-id="73a4f-117">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="73a4f-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="73a4f-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73a4f-118">Remarks</span></span>

<span data-ttu-id="73a4f-119">Ta funkcja zawija wywołanie [metody IWbemClassObject::EndMethodEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration)</span><span class="sxs-lookup"><span data-stu-id="73a4f-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="73a4f-120">Wywołujący rozpoczyna sekwencję wyliczenia za pomocą [funkcji BeginMethodEnumeration](beginmethodenumeration.md), a następnie `WBEM_S_NO_MORE_DATA`wywołuje funkcję [NextMethod,](nextmethod.md )dopóki metoda nie zwróci .</span><span class="sxs-lookup"><span data-stu-id="73a4f-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="73a4f-121">Wywołujący opcjonalnie kończy sekwencję `EndMethodEnumeration`przez wywołanie .</span><span class="sxs-lookup"><span data-stu-id="73a4f-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="73a4f-122">Wywołujący może zakończyć wyliczenie wcześnie, wywołując `EndMethodEnumeration` w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="73a4f-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="73a4f-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73a4f-123">Requirements</span></span>  
 <span data-ttu-id="73a4f-124">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73a4f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73a4f-125">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="73a4f-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="73a4f-126">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="73a4f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a4f-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73a4f-127">See also</span></span>

- [<span data-ttu-id="73a4f-128">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="73a4f-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
