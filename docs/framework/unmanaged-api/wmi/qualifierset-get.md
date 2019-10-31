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
ms.openlocfilehash: dc09cd30c43647fa00cccc1dc00da4f8de367e84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127279"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="2a85b-103">QualifierSet_Get, funkcja</span><span class="sxs-lookup"><span data-stu-id="2a85b-103">QualifierSet_Get function</span></span>
<span data-ttu-id="2a85b-104">Pobiera określony kwalifikator nazwany.</span><span class="sxs-lookup"><span data-stu-id="2a85b-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2a85b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a85b-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="2a85b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a85b-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="2a85b-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="2a85b-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="2a85b-108">podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="2a85b-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="2a85b-109">podczas Nazwa kwalifikatora, którego żądano wartości.</span><span class="sxs-lookup"><span data-stu-id="2a85b-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="2a85b-110">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="2a85b-110">[in] Reserved.</span></span> <span data-ttu-id="2a85b-111">Ten parametr musi być równy 0.</span><span class="sxs-lookup"><span data-stu-id="2a85b-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="2a85b-112">określoną Po pomyślnym wykonaniu prawidłowy typ i wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="2a85b-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="2a85b-113">Jeśli funkcja się nie powiedzie, `VARIANT` wskazywane przez `pVal` nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="2a85b-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="2a85b-114">Jeśli ten parametr jest `null`, parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="2a85b-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="2a85b-115">określoną Wskaźnik do LONG, który odbiera bity wersji kwalifikatora dla żądanego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="2a85b-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="2a85b-116">Jeśli informacje o wersji nie są potrzebne, ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="2a85b-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="2a85b-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2a85b-117">Return value</span></span>

<span data-ttu-id="2a85b-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="2a85b-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2a85b-119">Stała</span><span class="sxs-lookup"><span data-stu-id="2a85b-119">Constant</span></span>  |<span data-ttu-id="2a85b-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="2a85b-120">Value</span></span>  |<span data-ttu-id="2a85b-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2a85b-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2a85b-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2a85b-122">0x80041008</span></span> | <span data-ttu-id="2a85b-123">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2a85b-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="2a85b-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="2a85b-124">0x80041002</span></span> | <span data-ttu-id="2a85b-125">Określony kwalifikator nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="2a85b-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2a85b-126">0</span><span class="sxs-lookup"><span data-stu-id="2a85b-126">0</span></span> | <span data-ttu-id="2a85b-127">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2a85b-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2a85b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a85b-128">Remarks</span></span>

<span data-ttu-id="2a85b-129">Ta funkcja otacza wywołanie metody [IWbemQualifierSet:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) .</span><span class="sxs-lookup"><span data-stu-id="2a85b-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2a85b-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a85b-130">Requirements</span></span>  
 <span data-ttu-id="2a85b-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a85b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a85b-132">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="2a85b-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2a85b-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2a85b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a85b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a85b-134">See also</span></span>

- [<span data-ttu-id="2a85b-135">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="2a85b-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
