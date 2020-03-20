---
title: funkcja QualifierSet_Next (odwołanie do interfejsu API niezarządzanego)
description: Funkcja QualifierSet_Next pobiera następny kwalifikator w wyliczeniu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174878"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="15683-103">QualifierSet_Next funkcja</span><span class="sxs-lookup"><span data-stu-id="15683-103">QualifierSet_Next function</span></span>
<span data-ttu-id="15683-104">Pobiera następny kwalifikator w wyliczeniu, który rozpoczął się od wywołania funkcji [QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="15683-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="15683-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="15683-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a><span data-ttu-id="15683-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="15683-106">Parameters</span></span>

<span data-ttu-id="15683-107">`vFunc`[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="15683-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="15683-108">`ptr`[w] Wskaźnik do [wystąpienia IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="15683-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="15683-109">`lFlags`[w] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="15683-109">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="15683-110">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="15683-110">This parameter must be 0.</span></span>

<span data-ttu-id="15683-111">`pstrName`[na zewnątrz] Nazwa kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="15683-111">`pstrName` [out] The name of the qualifier.</span></span> <span data-ttu-id="15683-112">Jeśli `null`ten parametr jest ignorowany; w `pstrName` przeciwnym razie nie `BSTR` należy wskazywać prawidłowego lub przeciek pamięci występuje.</span><span class="sxs-lookup"><span data-stu-id="15683-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="15683-113">Jeśli nie jest null, funkcja `BSTR` zawsze przydziela `WBEM_S_NO_ERROR`nowy, gdy zwraca .</span><span class="sxs-lookup"><span data-stu-id="15683-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

<span data-ttu-id="15683-114">`pVal`[na zewnątrz] Po pomyślnym, wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="15683-114">`pVal` [out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="15683-115">Jeśli funkcja nie `VARIANT` powiedzie `pVal` się, wskazał przez nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="15683-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="15683-116">Jeśli ten `null`parametr jest , parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="15683-116">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="15683-117">`plFlavor`[na zewnątrz] Wskaźnik do LONG, który otrzymuje smak kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="15683-117">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="15683-118">Jeśli informacje o smaku nie są `null`pożądane, parametr ten może być .</span><span class="sxs-lookup"><span data-stu-id="15683-118">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="15683-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="15683-119">Return value</span></span>

<span data-ttu-id="15683-120">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="15683-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="15683-121">Stały</span><span class="sxs-lookup"><span data-stu-id="15683-121">Constant</span></span>  |<span data-ttu-id="15683-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="15683-122">Value</span></span>  |<span data-ttu-id="15683-123">Opis</span><span class="sxs-lookup"><span data-stu-id="15683-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="15683-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="15683-124">0x80041008</span></span> | <span data-ttu-id="15683-125">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="15683-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="15683-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="15683-126">0x8004101d</span></span> | <span data-ttu-id="15683-127">Dzwoniący nie zadzwonił [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="15683-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="15683-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="15683-128">0x80041006</span></span> | <span data-ttu-id="15683-129">Za mało pamięci jest dostępna, aby rozpocząć nowe wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="15683-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="15683-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="15683-130">0x40005</span></span> | <span data-ttu-id="15683-131">W wyliczeniu nie ma już żadnych kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="15683-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="15683-132">0</span><span class="sxs-lookup"><span data-stu-id="15683-132">0</span></span> | <span data-ttu-id="15683-133">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="15683-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="15683-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15683-134">Remarks</span></span>

<span data-ttu-id="15683-135">Ta funkcja zawija wywołanie [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) metody.</span><span class="sxs-lookup"><span data-stu-id="15683-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="15683-136">Wywołanie `QualifierSet_Next` funkcji wielokrotnie wyliczyć wszystkie kwalifikatory, `WBEM_S_NO_MORE_DATA`aż funkcja powróci .</span><span class="sxs-lookup"><span data-stu-id="15683-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="15683-137">Aby zakończyć wyliczenie wcześniej, należy wywołać funkcję [QualifierSet_EndEnumeration.](qualifierset-endenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="15683-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="15683-138">Kolejność kwalifikatorów zwróconych podczas wyliczenia jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="15683-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="15683-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15683-139">Requirements</span></span>  
 <span data-ttu-id="15683-140">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15683-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15683-141">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="15683-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="15683-142">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="15683-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15683-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15683-143">See also</span></span>

- [<span data-ttu-id="15683-144">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="15683-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
