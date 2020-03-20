---
title: BeginMethodEnumeration, funkcja (odwołanie do interfejsu API niezarządzanego)
description: BeginMethodEnumeration Funkcja rozpoczyna wyliczenie metod obiektu
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 876f5810fffab7fa98cd4d46715e13569ab95f6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175047"
---
# <a name="beginmethodenumeration-function"></a><span data-ttu-id="c503b-103">BeginMethodEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="c503b-103">BeginMethodEnumeration function</span></span>
<span data-ttu-id="c503b-104">Rozpoczyna wyliczenie metod dostępnych dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="c503b-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="c503b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c503b-105">Syntax</span></span>  
  
```cpp
HRESULT BeginMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="c503b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c503b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c503b-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="c503b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="c503b-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="c503b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="c503b-109">[w] Zero (0) dla wszystkich metod lub flaga, która określa zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c503b-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="c503b-110">Następujące flagi są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="c503b-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="c503b-111">Stały</span><span class="sxs-lookup"><span data-stu-id="c503b-111">Constant</span></span>  |<span data-ttu-id="c503b-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="c503b-112">Value</span></span>  |<span data-ttu-id="c503b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c503b-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="c503b-114">0x10</span><span class="sxs-lookup"><span data-stu-id="c503b-114">0x10</span></span> | <span data-ttu-id="c503b-115">Ogranicz wyliczenie do metod, które są zdefiniowane w samej klasie.</span><span class="sxs-lookup"><span data-stu-id="c503b-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="c503b-116">0x20</span><span class="sxs-lookup"><span data-stu-id="c503b-116">0x20</span></span> | <span data-ttu-id="c503b-117">Ogranicz wyliczenie do właściwości, które są dziedziczone z klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="c503b-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="c503b-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c503b-118">Return value</span></span>

<span data-ttu-id="c503b-119">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="c503b-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c503b-120">Stały</span><span class="sxs-lookup"><span data-stu-id="c503b-120">Constant</span></span>  |<span data-ttu-id="c503b-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="c503b-121">Value</span></span>  |<span data-ttu-id="c503b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c503b-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c503b-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c503b-123">0x80041008</span></span> | <span data-ttu-id="c503b-124">`lEnnumFlags`jest niezerowy i nie jest jedną z określonych flag.</span><span class="sxs-lookup"><span data-stu-id="c503b-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c503b-125">0</span><span class="sxs-lookup"><span data-stu-id="c503b-125">0</span></span> | <span data-ttu-id="c503b-126">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c503b-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c503b-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c503b-127">Remarks</span></span>

<span data-ttu-id="c503b-128">Ta funkcja zawija wywołanie [metody IWbemClassObject::BeginMethodEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration)</span><span class="sxs-lookup"><span data-stu-id="c503b-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="c503b-129">To wywołanie metody jest obsługiwane tylko wtedy, gdy bieżący obiekt jest definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="c503b-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="c503b-130">Manipulacja metodą nie jest dostępna w wskaźnikach [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazujących na wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c503b-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="c503b-131">Kolejność, w jakiej metody są wyliczone, jest gwarantowana jako niezmienna dla danego wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="c503b-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="c503b-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c503b-132">Requirements</span></span>  
 <span data-ttu-id="c503b-133">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c503b-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c503b-134">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c503b-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c503b-135">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c503b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c503b-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c503b-136">See also</span></span>

- [<span data-ttu-id="c503b-137">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="c503b-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
