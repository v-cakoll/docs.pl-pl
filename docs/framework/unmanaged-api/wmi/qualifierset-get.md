---
title: QualifierSet_Get — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_Get pobiera nazwany kwalifikator.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 751694985248346187eff016ef7a4a8054cb1212
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798312"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="901f4-103">QualifierSet_Get, funkcja</span><span class="sxs-lookup"><span data-stu-id="901f4-103">QualifierSet_Get function</span></span>
<span data-ttu-id="901f4-104">Pobiera określony kwalifikator nazwany.</span><span class="sxs-lookup"><span data-stu-id="901f4-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="901f4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="901f4-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="901f4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="901f4-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="901f4-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="901f4-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="901f4-108">podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="901f4-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="901f4-109">podczas Nazwa kwalifikatora, którego żądano wartości.</span><span class="sxs-lookup"><span data-stu-id="901f4-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="901f4-110">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="901f4-110">[in] Reserved.</span></span> <span data-ttu-id="901f4-111">Ten parametr musi być równy 0.</span><span class="sxs-lookup"><span data-stu-id="901f4-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="901f4-112">określoną Po pomyślnym wykonaniu prawidłowy typ i wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="901f4-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="901f4-113">Jeśli funkcja się nie powiedzie `VARIANT` , wskazywane `pVal` przez nie jest modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="901f4-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="901f4-114">Jeśli ten parametr ma `null`wartość, parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="901f4-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="901f4-115">określoną Wskaźnik do LONG, który odbiera bity wersji kwalifikatora dla żądanego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="901f4-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="901f4-116">Jeśli informacje o wersji nie są potrzebne, ten parametr może `null`być.</span><span class="sxs-lookup"><span data-stu-id="901f4-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="901f4-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="901f4-117">Return value</span></span>

<span data-ttu-id="901f4-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="901f4-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="901f4-119">Stała</span><span class="sxs-lookup"><span data-stu-id="901f4-119">Constant</span></span>  |<span data-ttu-id="901f4-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="901f4-120">Value</span></span>  |<span data-ttu-id="901f4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="901f4-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="901f4-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="901f4-122">0x80041008</span></span> | <span data-ttu-id="901f4-123">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="901f4-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="901f4-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="901f4-124">0x80041002</span></span> | <span data-ttu-id="901f4-125">Określony kwalifikator nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="901f4-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="901f4-126">0</span><span class="sxs-lookup"><span data-stu-id="901f4-126">0</span></span> | <span data-ttu-id="901f4-127">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="901f4-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="901f4-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="901f4-128">Remarks</span></span>

<span data-ttu-id="901f4-129">Ta funkcja otacza wywołanie metody [IWbemQualifierSet:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) .</span><span class="sxs-lookup"><span data-stu-id="901f4-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="901f4-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="901f4-130">Requirements</span></span>  
 <span data-ttu-id="901f4-131">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="901f4-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="901f4-132">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="901f4-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="901f4-133">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="901f4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="901f4-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="901f4-134">See also</span></span>

- [<span data-ttu-id="901f4-135">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="901f4-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
