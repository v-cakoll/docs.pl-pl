---
title: BeginMethodEnumeration — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja BeginMethodEnumeration rozpoczyna Wyliczenie metod obiektu.
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
ms.openlocfilehash: a27787052757098d4edb2d8516e22d8a03b7009a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138788"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="afe2a-103">BeingEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="afe2a-103">BeginEnumeration function</span></span>
<span data-ttu-id="afe2a-104">Rozpoczyna Wyliczenie metod dostępnych dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="afe2a-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="afe2a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="afe2a-105">Syntax</span></span>  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="afe2a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="afe2a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="afe2a-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="afe2a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="afe2a-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="afe2a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="afe2a-109">podczas Zero (0) dla wszystkich metod lub flagę, która określa zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="afe2a-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="afe2a-110">Poniższe flagi są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="afe2a-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="afe2a-111">Stała</span><span class="sxs-lookup"><span data-stu-id="afe2a-111">Constant</span></span>  |<span data-ttu-id="afe2a-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="afe2a-112">Value</span></span>  |<span data-ttu-id="afe2a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="afe2a-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="afe2a-114">0x10</span><span class="sxs-lookup"><span data-stu-id="afe2a-114">0x10</span></span> | <span data-ttu-id="afe2a-115">Ogranicz Wyliczenie do metod, które są zdefiniowane w samej klasie.</span><span class="sxs-lookup"><span data-stu-id="afe2a-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="afe2a-116">0x20</span><span class="sxs-lookup"><span data-stu-id="afe2a-116">0x20</span></span> | <span data-ttu-id="afe2a-117">Ogranicz Wyliczenie do właściwości, które są dziedziczone z klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="afe2a-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="afe2a-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="afe2a-118">Return value</span></span>

<span data-ttu-id="afe2a-119">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="afe2a-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="afe2a-120">Stała</span><span class="sxs-lookup"><span data-stu-id="afe2a-120">Constant</span></span>  |<span data-ttu-id="afe2a-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="afe2a-121">Value</span></span>  |<span data-ttu-id="afe2a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="afe2a-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="afe2a-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="afe2a-123">0x80041008</span></span> | <span data-ttu-id="afe2a-124">`lEnnumFlags` jest różna od zera i nie jest jedną z określonych flag.</span><span class="sxs-lookup"><span data-stu-id="afe2a-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="afe2a-125">0</span><span class="sxs-lookup"><span data-stu-id="afe2a-125">0</span></span> | <span data-ttu-id="afe2a-126">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="afe2a-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="afe2a-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afe2a-127">Remarks</span></span>

<span data-ttu-id="afe2a-128">Ta funkcja otacza wywołanie metody [IWbemClassObject:: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) .</span><span class="sxs-lookup"><span data-stu-id="afe2a-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="afe2a-129">To wywołanie metody jest obsługiwane tylko wtedy, gdy bieżący obiekt jest definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="afe2a-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="afe2a-130">Manipulowanie metodami nie jest dostępne ze wskaźników [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , które wskazują wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="afe2a-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="afe2a-131">Kolejność, w jakiej metody są wyliczane, gwarantuje, że jest niezmienna dla danego wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="afe2a-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="afe2a-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afe2a-132">Requirements</span></span>  
 <span data-ttu-id="afe2a-133">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afe2a-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afe2a-134">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="afe2a-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="afe2a-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="afe2a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe2a-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afe2a-136">See also</span></span>

- [<span data-ttu-id="afe2a-137">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="afe2a-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
