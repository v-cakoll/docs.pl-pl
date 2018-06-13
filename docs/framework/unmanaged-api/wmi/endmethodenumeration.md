---
title: Funkcja EndMethodEnumeration (niezarządzany wykaz interfejsów API)
description: Funkcja EndMethodEnumeration kończy sekwencji wyliczenie metody.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d09a2ee278dba7e711891bc6d72043bb3a499dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458493"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="6022e-103">Funkcja EndMethodEnumeration</span><span class="sxs-lookup"><span data-stu-id="6022e-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="6022e-104">Kończy sekwencji wyliczenie wprowadzenie wywołanie [funkcja BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6022e-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="6022e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6022e-105">Syntax</span></span>  
  
```  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="6022e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6022e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6022e-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="6022e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6022e-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6022e-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="6022e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6022e-109">Return value</span></span>

<span data-ttu-id="6022e-110">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="6022e-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6022e-111">Stała</span><span class="sxs-lookup"><span data-stu-id="6022e-111">Constant</span></span>  |<span data-ttu-id="6022e-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="6022e-112">Value</span></span>  |<span data-ttu-id="6022e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6022e-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="6022e-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="6022e-114">0x8004101d</span></span> | <span data-ttu-id="6022e-115">Wystąpił błąd wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="6022e-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6022e-116">0</span><span class="sxs-lookup"><span data-stu-id="6022e-116">0</span></span> | <span data-ttu-id="6022e-117">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6022e-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="6022e-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6022e-118">Remarks</span></span>

<span data-ttu-id="6022e-119">Ta funkcja jest zawijana wywołanie [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="6022e-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="6022e-120">Wywołującego rozpoczyna się przy użyciu sekwencji wyliczenie [funkcja BeginMethodEnumeration](beginmethodenumeration.md), a następnie wywołuje [funkcja NextMethod](nextmethod.md )dopóki metoda zwraca `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="6022e-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="6022e-121">Obiekt wywołujący opcjonalnie zakończeniem sekwencji przez wywołanie metody `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="6022e-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="6022e-122">Obiekt wywołujący może zakończyć wyliczenia wcześniej przez wywołanie metody `EndMethodEnumeration` w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="6022e-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="6022e-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6022e-123">Requirements</span></span>  
 <span data-ttu-id="6022e-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6022e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6022e-125">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6022e-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6022e-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6022e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6022e-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6022e-127">See also</span></span>  
[<span data-ttu-id="6022e-128">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="6022e-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
