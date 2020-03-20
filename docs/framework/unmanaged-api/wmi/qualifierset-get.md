---
title: funkcja QualifierSet_Get (odwołanie do interfejsu API niezarządzanego)
description: Funkcja QualifierSet_Get otrzymuje nazwany kwalifikator.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2f4e2d4518e01f3415b8f17ce5778dd98b2a45c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174891"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="6e326-103">QualifierSet_Get funkcja</span><span class="sxs-lookup"><span data-stu-id="6e326-103">QualifierSet_Get function</span></span>
<span data-ttu-id="6e326-104">Pobiera określony nazwany kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="6e326-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6e326-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e326-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a><span data-ttu-id="6e326-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e326-106">Parameters</span></span>

<span data-ttu-id="6e326-107">`vFunc`[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="6e326-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="6e326-108">`ptr`[w] Wskaźnik do [wystąpienia IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="6e326-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="6e326-109">`wszName`[w] Nazwa kwalifikatora, którego wartość jest żądana.</span><span class="sxs-lookup"><span data-stu-id="6e326-109">`wszName` [in] The name of the qualifier whose value is requested.</span></span>

<span data-ttu-id="6e326-110">`lFlags`[w] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="6e326-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="6e326-111">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="6e326-111">This parameter must be 0.</span></span>

<span data-ttu-id="6e326-112">`pVal`[na zewnątrz] Po pomyślnym, poprawny typ i wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="6e326-112">`pVal` [out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="6e326-113">Jeśli funkcja nie `VARIANT` powiedzie `pVal` się, wskazał przez nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="6e326-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="6e326-114">Jeśli ten `null`parametr jest , parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="6e326-114">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="6e326-115">`plFlavor`[na zewnątrz] Wskaźnik do LONG, który odbiera bity smaku kwalifikatora dla żądanego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="6e326-115">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="6e326-116">Jeśli informacje o smaku nie są `null`pożądane, parametr ten może być .</span><span class="sxs-lookup"><span data-stu-id="6e326-116">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="6e326-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6e326-117">Return value</span></span>

<span data-ttu-id="6e326-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="6e326-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6e326-119">Stały</span><span class="sxs-lookup"><span data-stu-id="6e326-119">Constant</span></span>  |<span data-ttu-id="6e326-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="6e326-120">Value</span></span>  |<span data-ttu-id="6e326-121">Opis</span><span class="sxs-lookup"><span data-stu-id="6e326-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6e326-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6e326-122">0x80041008</span></span> | <span data-ttu-id="6e326-123">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6e326-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="6e326-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="6e326-124">0x80041002</span></span> | <span data-ttu-id="6e326-125">Określony kwalifikator nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="6e326-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6e326-126">0</span><span class="sxs-lookup"><span data-stu-id="6e326-126">0</span></span> | <span data-ttu-id="6e326-127">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6e326-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="6e326-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e326-128">Remarks</span></span>

<span data-ttu-id="6e326-129">Ta funkcja zawija wywołanie [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) metody.</span><span class="sxs-lookup"><span data-stu-id="6e326-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6e326-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e326-130">Requirements</span></span>  
 <span data-ttu-id="6e326-131">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e326-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e326-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6e326-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6e326-133">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6e326-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e326-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e326-134">See also</span></span>

- [<span data-ttu-id="6e326-135">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="6e326-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
