---
title: "Funkcja InheritsFrom (niezarządzany wykaz interfejsów API)"
description: "Funkcja InheritsFrom Określa, czy klasy lub wystąpienia pochodzi z klasy nadrzędnej określonej."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: InheritsFrom
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: InheritsFrom
helpviewer_keywords: InheritsFrom function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aedeec76f4fabb2f6bd32d7d06eb5a1a5734534e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="b7b5f-103">Funkcja InheritsFrom</span><span class="sxs-lookup"><span data-stu-id="b7b5f-103">InheritsFrom function</span></span>
<span data-ttu-id="b7b5f-104">Określa, czy bieżącej klasy lub wystąpienia jest pochodną klasy określonego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b7b5f-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b7b5f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7b5f-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="b7b5f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7b5f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b7b5f-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="b7b5f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b7b5f-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b7b5f-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="b7b5f-109">[in] Nazwa klasy.</span><span class="sxs-lookup"><span data-stu-id="b7b5f-109">[in] The name of the class.</span></span> <span data-ttu-id="b7b5f-110">`wszAncestor`musi wskazywać prawidłowe `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="b7b5f-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="b7b5f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b7b5f-111">Return value</span></span>

<span data-ttu-id="b7b5f-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="b7b5f-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b7b5f-113">Stała</span><span class="sxs-lookup"><span data-stu-id="b7b5f-113">Constant</span></span>  |<span data-ttu-id="b7b5f-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="b7b5f-114">Value</span></span>  |<span data-ttu-id="b7b5f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b7b5f-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b7b5f-116">0</span><span class="sxs-lookup"><span data-stu-id="b7b5f-116">0</span></span> | <span data-ttu-id="b7b5f-117">Bieżący obiekt dziedziczy `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="b7b5f-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="b7b5f-118">1</span><span class="sxs-lookup"><span data-stu-id="b7b5f-118">1</span></span> | <span data-ttu-id="b7b5f-119">Bieżący obiekt nie dziedziczy `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="b7b5f-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b7b5f-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b7b5f-120">0x80041008</span></span> | <span data-ttu-id="b7b5f-121">`wszAncestor`jest `null`.</span><span class="sxs-lookup"><span data-stu-id="b7b5f-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="b7b5f-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7b5f-122">Remarks</span></span>

<span data-ttu-id="b7b5f-123">Ta funkcja jest zawijana wywołanie [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="b7b5f-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7b5f-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7b5f-124">Requirements</span></span>  
 <span data-ttu-id="b7b5f-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7b5f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7b5f-126">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b7b5f-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b7b5f-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b7b5f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b5f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7b5f-128">See also</span></span>  
[<span data-ttu-id="b7b5f-129">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="b7b5f-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
