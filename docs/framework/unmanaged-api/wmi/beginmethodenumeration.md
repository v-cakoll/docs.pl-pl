---
title: "Funkcja BeginMethodEnumeration (niezarządzany wykaz interfejsów API)"
description: Funkcja BeginMethodEnumeration rozpoczyna wyliczenie metody obiektu
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginMethodEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginMethodEnumeration
helpviewer_keywords: BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e44c432f9503f96ad4dab9e25b78e6dd148f94c
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="beginenumeration-function"></a><span data-ttu-id="88b8f-103">Funkcja Beingenumeration</span><span class="sxs-lookup"><span data-stu-id="88b8f-103">BeginEnumeration function</span></span>
<span data-ttu-id="88b8f-104">Rozpoczyna się wyliczenia metod dla obiekt.</span><span class="sxs-lookup"><span data-stu-id="88b8f-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="88b8f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="88b8f-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="88b8f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="88b8f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="88b8f-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="88b8f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="88b8f-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="88b8f-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="88b8f-109">[in] Wartość zero (0) dla wszystkich metod lub flaga, która określa zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="88b8f-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="88b8f-110">Następujące flagi są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="88b8f-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="88b8f-111">Stała</span><span class="sxs-lookup"><span data-stu-id="88b8f-111">Constant</span></span>  |<span data-ttu-id="88b8f-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="88b8f-112">Value</span></span>  |<span data-ttu-id="88b8f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="88b8f-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="88b8f-114">0x10</span><span class="sxs-lookup"><span data-stu-id="88b8f-114">0x10</span></span> | <span data-ttu-id="88b8f-115">Ogranicz wyliczenia metod, które są zdefiniowane w samej klasy.</span><span class="sxs-lookup"><span data-stu-id="88b8f-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="88b8f-116">0x20</span><span class="sxs-lookup"><span data-stu-id="88b8f-116">0x20</span></span> | <span data-ttu-id="88b8f-117">Ogranicz wyliczenia właściwości, które są dziedziczone z klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="88b8f-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="88b8f-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="88b8f-118">Return value</span></span>

<span data-ttu-id="88b8f-119">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="88b8f-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="88b8f-120">Stała</span><span class="sxs-lookup"><span data-stu-id="88b8f-120">Constant</span></span>  |<span data-ttu-id="88b8f-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="88b8f-121">Value</span></span>  |<span data-ttu-id="88b8f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="88b8f-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="88b8f-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="88b8f-123">0x80041008</span></span> | <span data-ttu-id="88b8f-124">`lEnnumFlags`jest różna od zera i nie jest jednym z określonych flag.</span><span class="sxs-lookup"><span data-stu-id="88b8f-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="88b8f-125">0</span><span class="sxs-lookup"><span data-stu-id="88b8f-125">0</span></span> | <span data-ttu-id="88b8f-126">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="88b8f-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="88b8f-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88b8f-127">Remarks</span></span>

<span data-ttu-id="88b8f-128">Ta funkcja jest zawijana wywołanie [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="88b8f-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="88b8f-129">Wywołanie tej metody jest obsługiwana tylko, jeśli bieżący obiekt jest definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="88b8f-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="88b8f-130">Metoda manipulowania nie jest dostępna z [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wskaźników, które wskazują wystąpień.</span><span class="sxs-lookup"><span data-stu-id="88b8f-130">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to instances.</span></span> <span data-ttu-id="88b8f-131">Kolejność, w którym są wyliczane metody gwarantuje to niezmiennej dla danego wystąpienia [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="88b8f-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="88b8f-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88b8f-132">Requirements</span></span>  
 <span data-ttu-id="88b8f-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88b8f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88b8f-134">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="88b8f-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="88b8f-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="88b8f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88b8f-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88b8f-136">See also</span></span>  
[<span data-ttu-id="88b8f-137">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="88b8f-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
