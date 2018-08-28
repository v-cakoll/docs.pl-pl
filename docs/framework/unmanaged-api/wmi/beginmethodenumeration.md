---
title: Funkcja BeginMethodEnumeration (niezarządzany wykaz interfejsów API)
description: Funkcja BeginMethodEnumeration, rozpoczyna się wyliczenie metod obiektu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e69625184aca7d1ebd4bb0b7dc7c4958596b906a
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000346"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="bded7-103">Funkcja Beingenumeration</span><span class="sxs-lookup"><span data-stu-id="bded7-103">BeginEnumeration function</span></span>
<span data-ttu-id="bded7-104">Rozpoczyna się wyliczenie metody dostępne dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="bded7-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="bded7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bded7-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="bded7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bded7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="bded7-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="bded7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="bded7-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="bded7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="bded7-109">[in] Zero (0) dla wszystkich metod lub flagę, która określa zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bded7-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="bded7-110">Następujące flagi są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="bded7-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="bded7-111">Stała</span><span class="sxs-lookup"><span data-stu-id="bded7-111">Constant</span></span>  |<span data-ttu-id="bded7-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="bded7-112">Value</span></span>  |<span data-ttu-id="bded7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bded7-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="bded7-114">0x10</span><span class="sxs-lookup"><span data-stu-id="bded7-114">0x10</span></span> | <span data-ttu-id="bded7-115">Ograniczenie wyliczenia do metod, które są zdefiniowane w samej klasy.</span><span class="sxs-lookup"><span data-stu-id="bded7-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="bded7-116">0x20</span><span class="sxs-lookup"><span data-stu-id="bded7-116">0x20</span></span> | <span data-ttu-id="bded7-117">Ograniczenie wyliczenia właściwości, które są dziedziczone z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="bded7-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="bded7-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bded7-118">Return value</span></span>

<span data-ttu-id="bded7-119">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="bded7-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bded7-120">Stała</span><span class="sxs-lookup"><span data-stu-id="bded7-120">Constant</span></span>  |<span data-ttu-id="bded7-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="bded7-121">Value</span></span>  |<span data-ttu-id="bded7-122">Opis</span><span class="sxs-lookup"><span data-stu-id="bded7-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bded7-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bded7-123">0x80041008</span></span> | <span data-ttu-id="bded7-124">`lEnnumFlags` jest różna od zera i nie jest jedną z określonych flag.</span><span class="sxs-lookup"><span data-stu-id="bded7-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="bded7-125">0</span><span class="sxs-lookup"><span data-stu-id="bded7-125">0</span></span> | <span data-ttu-id="bded7-126">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bded7-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="bded7-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bded7-127">Remarks</span></span>

<span data-ttu-id="bded7-128">Ta funkcja zawija wywołanie do [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) metody.</span><span class="sxs-lookup"><span data-stu-id="bded7-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="bded7-129">Wywołanie tej metody jest obsługiwana tylko w przypadku, jeśli bieżący obiekt jest definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="bded7-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="bded7-130">Metoda manipulowania nie jest dostępna z [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźniki prowadzące do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="bded7-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="bded7-131">Kolejność, w którym są wyliczane metody może być inwariantny dla danego wystąpienia programu [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="bded7-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="bded7-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bded7-132">Requirements</span></span>  
 <span data-ttu-id="bded7-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bded7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bded7-134">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bded7-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bded7-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bded7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bded7-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bded7-136">See also</span></span>  
[<span data-ttu-id="bded7-137">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="bded7-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
