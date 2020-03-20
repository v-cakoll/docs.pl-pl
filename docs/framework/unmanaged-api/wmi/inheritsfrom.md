---
title: InheritsFrom, funkcja (odwołanie do interfejsu API niezarządzanego)
description: InheritsFrom Funkcja określa, czy klasa lub wystąpienie pochodzi z określonej klasy nadrzędnej.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c735c01c45beda8a1ba988a5c580e6b04ae46312
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174943"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="78203-103">InheritsFrom, funkcja</span><span class="sxs-lookup"><span data-stu-id="78203-103">InheritsFrom function</span></span>
<span data-ttu-id="78203-104">Określa, czy bieżąca klasa lub wystąpienie pochodzi od określonej klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="78203-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="78203-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="78203-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a><span data-ttu-id="78203-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="78203-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="78203-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="78203-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="78203-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="78203-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="78203-109">[w] Nazwa klasy.</span><span class="sxs-lookup"><span data-stu-id="78203-109">[in] The name of the class.</span></span> <span data-ttu-id="78203-110">`wszAncestor`musi wskazywać prawidłowe `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="78203-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="78203-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="78203-111">Return value</span></span>

<span data-ttu-id="78203-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="78203-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="78203-113">Stały</span><span class="sxs-lookup"><span data-stu-id="78203-113">Constant</span></span>  |<span data-ttu-id="78203-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="78203-114">Value</span></span>  |<span data-ttu-id="78203-115">Opis</span><span class="sxs-lookup"><span data-stu-id="78203-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="78203-116">0</span><span class="sxs-lookup"><span data-stu-id="78203-116">0</span></span> | <span data-ttu-id="78203-117">Bieżący obiekt dziedziczy z pliku `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="78203-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="78203-118">1</span><span class="sxs-lookup"><span data-stu-id="78203-118">1</span></span> | <span data-ttu-id="78203-119">Bieżący obiekt nie `wszAncestor`dziedziczy po pliku .</span><span class="sxs-lookup"><span data-stu-id="78203-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="78203-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="78203-120">0x80041008</span></span> | <span data-ttu-id="78203-121">Parametr `wszAncestor` ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="78203-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="78203-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78203-122">Remarks</span></span>

<span data-ttu-id="78203-123">Ta funkcja zawija wywołanie [metody IWbemClassObject::InheritsFrom.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom)</span><span class="sxs-lookup"><span data-stu-id="78203-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="78203-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78203-124">Requirements</span></span>  
 <span data-ttu-id="78203-125">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78203-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78203-126">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="78203-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="78203-127">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="78203-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78203-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78203-128">See also</span></span>

- [<span data-ttu-id="78203-129">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="78203-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
