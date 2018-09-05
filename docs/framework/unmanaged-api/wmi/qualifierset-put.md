---
title: Funkcja QualifierSet_Put (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_Put zapisuje kwalifikator nazwanych i jego wartość.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b2e1b08d1091e482c6b02fe015a58219ff80768
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517564"
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="70094-103">QualifierSet_Put — funkcja</span><span class="sxs-lookup"><span data-stu-id="70094-103">QualifierSet_Put function</span></span>
<span data-ttu-id="70094-104">Zapisuje kwalifikator o nazwie i wartości.</span><span class="sxs-lookup"><span data-stu-id="70094-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="70094-105">Nowy kwalifikator zastępuje poprzednią wartość taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="70094-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="70094-106">Jeśli kwalifikatora nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="70094-106">If the qualifier does not exist, it is created.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="70094-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="70094-107">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="70094-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="70094-108">Parameters</span></span>

`vFunc`   
<span data-ttu-id="70094-109">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="70094-109">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="70094-110">[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="70094-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="70094-111">[in] Nazwa kwalifikatora do zapisania.</span><span class="sxs-lookup"><span data-stu-id="70094-111">[in] The name of the qualifier to write.</span></span>

<span data-ttu-id="70094-112">`pVal` [in] Wskaźnik do prawidłowego `VARIANT` zawierający kwalifikator do zapisania.</span><span class="sxs-lookup"><span data-stu-id="70094-112">`pVal` [in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="70094-113">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="70094-113">This parameter cannot be `null`.</span></span>

<span data-ttu-id="70094-114">`lFlavor` [in] Jeden z następujących stałych, które definiuje właściwą kwalifikator odpowiednią dla tego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="70094-114">`lFlavor` [in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="70094-115">Wartość domyślna to `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="70094-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="70094-116">Stała</span><span class="sxs-lookup"><span data-stu-id="70094-116">Constant</span></span>  |<span data-ttu-id="70094-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="70094-117">Value</span></span>  |<span data-ttu-id="70094-118">Opis</span><span class="sxs-lookup"><span data-stu-id="70094-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="70094-119">0</span><span class="sxs-lookup"><span data-stu-id="70094-119">0</span></span> | <span data-ttu-id="70094-120">Kwalifikator może zostać przesłonięta w pochodnej klasy lub wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="70094-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="70094-121">**Jest to wartość domyślna.**</span><span class="sxs-lookup"><span data-stu-id="70094-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="70094-122">1</span><span class="sxs-lookup"><span data-stu-id="70094-122">1</span></span> | <span data-ttu-id="70094-123">Kwalifikator jest propagowana do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="70094-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="70094-124">2</span><span class="sxs-lookup"><span data-stu-id="70094-124">2</span></span> | <span data-ttu-id="70094-125">Kwalifikator jest propagowana do klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="70094-125">The qualifier is propagated to derived classes.</span></span> |
| <span data-ttu-id="70094-126">"WBEM_FLAVOR_NOT_OVERRIDABLE</span><span class="sxs-lookup"><span data-stu-id="70094-126">\`WBEM_FLAVOR_NOT_OVERRIDABLE</span></span> | <span data-ttu-id="70094-127">0x10</span><span class="sxs-lookup"><span data-stu-id="70094-127">0x10</span></span> | <span data-ttu-id="70094-128">Nie można zastąpić kwalifikator w klasie pochodnej lub wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="70094-128">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| <span data-ttu-id="70094-129">"WBEM_FLAVOR_AMENDED</span><span class="sxs-lookup"><span data-stu-id="70094-129">\`WBEM_FLAVOR_AMENDED</span></span> | <span data-ttu-id="70094-130">0x80</span><span class="sxs-lookup"><span data-stu-id="70094-130">0x80</span></span> | <span data-ttu-id="70094-131">Kwalifikator jest zlokalizowana.</span><span class="sxs-lookup"><span data-stu-id="70094-131">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="70094-132">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="70094-132">Return value</span></span>

<span data-ttu-id="70094-133">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="70094-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="70094-134">Stała</span><span class="sxs-lookup"><span data-stu-id="70094-134">Constant</span></span>  |<span data-ttu-id="70094-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="70094-135">Value</span></span>  |<span data-ttu-id="70094-136">Opis</span><span class="sxs-lookup"><span data-stu-id="70094-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="70094-137">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="70094-137">0x8004101f</span></span> | <span data-ttu-id="70094-138">Wystąpił niedozwolona próba określenia **klucz** kwalifikator dla właściwości, która nie może być kluczem.</span><span class="sxs-lookup"><span data-stu-id="70094-138">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="70094-139">Klucze są określone om c; definicji klasy dla obiektu i nie może zostać zmieniona na podstawie poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="70094-139">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="70094-140">0x80041008</span><span class="sxs-lookup"><span data-stu-id="70094-140">0x80041008</span></span> | <span data-ttu-id="70094-141">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="70094-141">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="70094-142">0x80041029</span><span class="sxs-lookup"><span data-stu-id="70094-142">0x80041029</span></span> | <span data-ttu-id="70094-143">`pVal` Parametr nie jest dozwolonym typem kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="70094-143">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="70094-144">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="70094-144">0x8004101a</span></span> | <span data-ttu-id="70094-145">Nie jest możliwe do wywołania `QualifierSet_Put` metody kwalifikator, ponieważ obiekt-właściciel nie zezwala na zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="70094-145">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="70094-146">0</span><span class="sxs-lookup"><span data-stu-id="70094-146">0</span></span> | <span data-ttu-id="70094-147">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="70094-147">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="70094-148">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70094-148">Remarks</span></span>

<span data-ttu-id="70094-149">Ta funkcja zawija wywołanie do [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) metody.</span><span class="sxs-lookup"><span data-stu-id="70094-149">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="70094-150">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70094-150">Requirements</span></span>  
 <span data-ttu-id="70094-151">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70094-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70094-152">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="70094-152">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="70094-153">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="70094-153">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70094-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70094-154">See also</span></span>  
[<span data-ttu-id="70094-155">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="70094-155">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
