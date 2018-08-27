---
title: Funkcja klonowania (niezarządzany wykaz interfejsów API)
description: Funkcja klonowania zwraca nowy obiekt, który jest kompletny klonowania bieżący proces.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cd87cb619ef2dc1e0548c7553585b7e51e94c4f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924778"
---
# <a name="clone-function"></a><span data-ttu-id="514cd-103">Funkcja clone</span><span class="sxs-lookup"><span data-stu-id="514cd-103">Clone function</span></span>
<span data-ttu-id="514cd-104">Zwraca nowy obiekt, który jest kompletny klonowania bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="514cd-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="514cd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="514cd-105">Syntax</span></span>  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="514cd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="514cd-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="514cd-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="514cd-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="514cd-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="514cd-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="514cd-109">[out] Nowy obiekt, który jest kompletna pojedynczy z `ptr`.</span><span class="sxs-lookup"><span data-stu-id="514cd-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="514cd-110">Ten argument nie może być `null` jeżeli otrzyma kopię bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="514cd-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="514cd-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="514cd-111">Return value</span></span>

<span data-ttu-id="514cd-112">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="514cd-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="514cd-113">Stała</span><span class="sxs-lookup"><span data-stu-id="514cd-113">Constant</span></span>  |<span data-ttu-id="514cd-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="514cd-114">Value</span></span>  |<span data-ttu-id="514cd-115">Opis</span><span class="sxs-lookup"><span data-stu-id="514cd-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="514cd-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="514cd-116">0x80041001</span></span> | <span data-ttu-id="514cd-117">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="514cd-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="514cd-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="514cd-118">0x80041008</span></span> | <span data-ttu-id="514cd-119">`null` został określony jako parametr, a nie jest dozwolone w tym użycie.</span><span class="sxs-lookup"><span data-stu-id="514cd-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="514cd-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="514cd-120">0x80041006</span></span> | <span data-ttu-id="514cd-121">Nie ma wystarczającej ilości pamięci jest dostępny w celu sklonowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="514cd-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="514cd-122">0</span><span class="sxs-lookup"><span data-stu-id="514cd-122">0</span></span> | <span data-ttu-id="514cd-123">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="514cd-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="514cd-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="514cd-124">Remarks</span></span>

<span data-ttu-id="514cd-125">Ta funkcja zawija wywołanie do [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) metody.</span><span class="sxs-lookup"><span data-stu-id="514cd-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="514cd-126">Sklonowany obiekt jest obiektem COM, który ma liczebności referencyjnej równej 1.</span><span class="sxs-lookup"><span data-stu-id="514cd-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="514cd-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="514cd-127">Requirements</span></span>  
 <span data-ttu-id="514cd-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="514cd-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="514cd-129">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="514cd-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="514cd-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="514cd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="514cd-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="514cd-131">See also</span></span>  
[<span data-ttu-id="514cd-132">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="514cd-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
