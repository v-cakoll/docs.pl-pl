---
title: Funkcja QualifierSet_Get (niezarządzany wykaz interfejsów API)
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
ms.openlocfilehash: b0dc76a2732bf9c1e4f3a26fa2d045bfbcd837ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181093"
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="37682-103">QualifierSet_Get — funkcja</span><span class="sxs-lookup"><span data-stu-id="37682-103">QualifierSet_Get function</span></span>
<span data-ttu-id="37682-104">Pobiera określonego nazwanego kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="37682-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="37682-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="37682-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="37682-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="37682-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="37682-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="37682-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="37682-108">[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="37682-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="37682-109">[in] Nazwa kwalifikatora, którego wartość jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="37682-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="37682-110">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="37682-110">[in] Reserved.</span></span> <span data-ttu-id="37682-111">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="37682-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="37682-112">[out] Jeśli operacja się powiedzie, poprawny typ i wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="37682-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="37682-113">Jeśli funkcja zawiedzie, `VARIANT` wskazywany przez `pVal` nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="37682-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="37682-114">Jeśli ten parametr jest `null`, parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="37682-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="37682-115">[out] Wskaźnik na wartość typu LONG, odbierająca bitów wersja kwalifikatora dla żądanego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="37682-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="37682-116">Jeśli informacje o wersji nie jest wymagana, ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="37682-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="37682-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="37682-117">Return value</span></span>

<span data-ttu-id="37682-118">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="37682-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="37682-119">Stała</span><span class="sxs-lookup"><span data-stu-id="37682-119">Constant</span></span>  |<span data-ttu-id="37682-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="37682-120">Value</span></span>  |<span data-ttu-id="37682-121">Opis</span><span class="sxs-lookup"><span data-stu-id="37682-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="37682-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="37682-122">0x80041008</span></span> | <span data-ttu-id="37682-123">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="37682-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="37682-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="37682-124">0x80041002</span></span> | <span data-ttu-id="37682-125">Określony kwalifikatora nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="37682-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="37682-126">0</span><span class="sxs-lookup"><span data-stu-id="37682-126">0</span></span> | <span data-ttu-id="37682-127">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="37682-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="37682-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37682-128">Remarks</span></span>

<span data-ttu-id="37682-129">Ta funkcja zawija wywołanie do [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) metody.</span><span class="sxs-lookup"><span data-stu-id="37682-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="37682-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37682-130">Requirements</span></span>  
 <span data-ttu-id="37682-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37682-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37682-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="37682-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="37682-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="37682-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37682-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37682-134">See also</span></span>

- [<span data-ttu-id="37682-135">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="37682-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
