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
ms.openlocfilehash: f62ea692c055b0537394ad5e16501d4162faef12
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746832"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="f6d80-103">EndMethodEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="f6d80-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="f6d80-104">Kończy sekwencji wyliczenie pracę z wywołaniem [funkcja BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f6d80-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f6d80-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6d80-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="f6d80-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6d80-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f6d80-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="f6d80-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f6d80-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f6d80-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="f6d80-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f6d80-109">Return value</span></span>

<span data-ttu-id="f6d80-110">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="f6d80-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f6d80-111">Stała</span><span class="sxs-lookup"><span data-stu-id="f6d80-111">Constant</span></span>  |<span data-ttu-id="f6d80-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="f6d80-112">Value</span></span>  |<span data-ttu-id="f6d80-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f6d80-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="f6d80-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="f6d80-114">0x8004101d</span></span> | <span data-ttu-id="f6d80-115">Wystąpił błąd wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="f6d80-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f6d80-116">0</span><span class="sxs-lookup"><span data-stu-id="f6d80-116">0</span></span> | <span data-ttu-id="f6d80-117">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6d80-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f6d80-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6d80-118">Remarks</span></span>

<span data-ttu-id="f6d80-119">Ta funkcja zawija wywołanie do [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) metody.</span><span class="sxs-lookup"><span data-stu-id="f6d80-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="f6d80-120">Obiekt wywołujący, który rozpoczyna się przy użyciu sekwencji wyliczenie [funkcja BeginMethodEnumeration](beginmethodenumeration.md), a następnie wywołuje [NextMethod — funkcja](nextmethod.md )dopóki metoda zwraca `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="f6d80-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="f6d80-121">Obiekt wywołujący opcjonalnie zakończy się sekwencję przez wywołanie metody `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="f6d80-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="f6d80-122">Obiekt wywołujący może rozwiązać niniejszą wyliczenia wcześnie, wywołując `EndMethodEnumeration` w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="f6d80-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="f6d80-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6d80-123">Requirements</span></span>  
 <span data-ttu-id="f6d80-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6d80-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6d80-125">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f6d80-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f6d80-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f6d80-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d80-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6d80-127">See also</span></span>

- [<span data-ttu-id="f6d80-128">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="f6d80-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
