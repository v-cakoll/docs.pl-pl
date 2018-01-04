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
ms.workload: dotnet
ms.openlocfilehash: 0dce964829399e6761152a8ff424671b47cc6eb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="d1554-103">Funkcja InheritsFrom</span><span class="sxs-lookup"><span data-stu-id="d1554-103">InheritsFrom function</span></span>
<span data-ttu-id="d1554-104">Określa, czy bieżącej klasy lub wystąpienia jest pochodną klasy określonego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d1554-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d1554-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1554-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="d1554-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1554-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d1554-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="d1554-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d1554-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d1554-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="d1554-109">[in] Nazwa klasy.</span><span class="sxs-lookup"><span data-stu-id="d1554-109">[in] The name of the class.</span></span> <span data-ttu-id="d1554-110">`wszAncestor`musi wskazywać prawidłowe `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="d1554-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d1554-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1554-111">Return value</span></span>

<span data-ttu-id="d1554-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d1554-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d1554-113">Stała</span><span class="sxs-lookup"><span data-stu-id="d1554-113">Constant</span></span>  |<span data-ttu-id="d1554-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="d1554-114">Value</span></span>  |<span data-ttu-id="d1554-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d1554-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="d1554-116">0</span><span class="sxs-lookup"><span data-stu-id="d1554-116">0</span></span> | <span data-ttu-id="d1554-117">Bieżący obiekt dziedziczy `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="d1554-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="d1554-118">1</span><span class="sxs-lookup"><span data-stu-id="d1554-118">1</span></span> | <span data-ttu-id="d1554-119">Bieżący obiekt nie dziedziczy `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="d1554-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d1554-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d1554-120">0x80041008</span></span> | <span data-ttu-id="d1554-121">`wszAncestor`jest `null`.</span><span class="sxs-lookup"><span data-stu-id="d1554-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d1554-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1554-122">Remarks</span></span>

<span data-ttu-id="d1554-123">Ta funkcja jest zawijana wywołanie [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="d1554-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1554-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1554-124">Requirements</span></span>  
 <span data-ttu-id="d1554-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1554-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1554-126">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d1554-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d1554-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d1554-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1554-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1554-128">See also</span></span>  
[<span data-ttu-id="d1554-129">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="d1554-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
