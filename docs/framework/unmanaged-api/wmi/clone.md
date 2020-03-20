---
title: Funkcja klonowania (odwołanie do niezarządzanego interfejsu API)
description: Funkcja Klonuj zwraca nowy obiekt, który jest kompletnym klonem bieżącego.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: cb4951a1f289417482bfa1287028cc66349a5938
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176854"
---
# <a name="clone-function"></a><span data-ttu-id="98d78-103">Clone, funkcja</span><span class="sxs-lookup"><span data-stu-id="98d78-103">Clone function</span></span>
<span data-ttu-id="98d78-104">Zwraca nowy obiekt, który jest kompletnym klonem bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="98d78-104">Returns a new object that is a complete clone of the current object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="98d78-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="98d78-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [out] IWbemClassObject**  ppCopy
);
```  

## <a name="parameters"></a><span data-ttu-id="98d78-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="98d78-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="98d78-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="98d78-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="98d78-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="98d78-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="98d78-109">[na zewnątrz] Nowy obiekt, który jest `ptr`kompletnym samotnym .</span><span class="sxs-lookup"><span data-stu-id="98d78-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="98d78-110">Ten argument `null` nie może być, jeśli odbiera kopię bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="98d78-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="98d78-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="98d78-111">Return value</span></span>

<span data-ttu-id="98d78-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="98d78-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="98d78-113">Stały</span><span class="sxs-lookup"><span data-stu-id="98d78-113">Constant</span></span>  |<span data-ttu-id="98d78-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="98d78-114">Value</span></span>  |<span data-ttu-id="98d78-115">Opis</span><span class="sxs-lookup"><span data-stu-id="98d78-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="98d78-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="98d78-116">0x80041001</span></span> | <span data-ttu-id="98d78-117">Wystąpiła ogólna porażka.</span><span class="sxs-lookup"><span data-stu-id="98d78-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="98d78-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="98d78-118">0x80041008</span></span> | <span data-ttu-id="98d78-119">`null`został określony jako parametr i nie jest legalne w tym użyciu.</span><span class="sxs-lookup"><span data-stu-id="98d78-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="98d78-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="98d78-120">0x80041006</span></span> | <span data-ttu-id="98d78-121">Za mało pamięci jest dostępna do sklonowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="98d78-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="98d78-122">0</span><span class="sxs-lookup"><span data-stu-id="98d78-122">0</span></span> | <span data-ttu-id="98d78-123">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="98d78-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="98d78-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98d78-124">Remarks</span></span>

<span data-ttu-id="98d78-125">Ta funkcja zawija wywołanie [metody IWbemClassObject::Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)</span><span class="sxs-lookup"><span data-stu-id="98d78-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="98d78-126">Sklonowany obiekt jest obiektem COM, który ma liczbę odwołań 1.</span><span class="sxs-lookup"><span data-stu-id="98d78-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="98d78-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98d78-127">Requirements</span></span>  
 <span data-ttu-id="98d78-128">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98d78-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98d78-129">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="98d78-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="98d78-130">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="98d78-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d78-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98d78-131">See also</span></span>

- [<span data-ttu-id="98d78-132">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="98d78-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
