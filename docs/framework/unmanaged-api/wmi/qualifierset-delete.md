---
title: Funkcja QualifierSet_Delete (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_Delete powoduje usunięcie kwalifikatorze według nazwy.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca4cc9fb65d1a4bd8713f969bbda5551ce5a2e2
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46325383"
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="38656-103">QualifierSet_Delete — funkcja</span><span class="sxs-lookup"><span data-stu-id="38656-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="38656-104">Usuwa określony kwalifikator według nazwy.</span><span class="sxs-lookup"><span data-stu-id="38656-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="38656-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="38656-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="38656-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="38656-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="38656-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="38656-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="38656-108">[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="38656-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="38656-109">[in] Nazwa kwalifikatora do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="38656-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="38656-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="38656-110">Return value</span></span>

<span data-ttu-id="38656-111">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="38656-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="38656-112">Stała</span><span class="sxs-lookup"><span data-stu-id="38656-112">Constant</span></span>  |<span data-ttu-id="38656-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="38656-113">Value</span></span>  |<span data-ttu-id="38656-114">Opis</span><span class="sxs-lookup"><span data-stu-id="38656-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="38656-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="38656-115">0x80041008</span></span> | <span data-ttu-id="38656-116">`wszName` Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="38656-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="38656-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="38656-117">0x80041016</span></span> | <span data-ttu-id="38656-118">Usunięcie tego kwalifikatora jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="38656-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="38656-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="38656-119">0x80041002</span></span> | <span data-ttu-id="38656-120">Nie można odnaleźć określonego kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="38656-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="38656-121">0</span><span class="sxs-lookup"><span data-stu-id="38656-121">0</span></span> | <span data-ttu-id="38656-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="38656-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="38656-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="38656-123">0x40002</span></span> | <span data-ttu-id="38656-124">Zastąpienie lokalnych została usunięta i oryginalny kwalifikator z obiektu nadrzędnego wznowił zakresu.</span><span class="sxs-lookup"><span data-stu-id="38656-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="38656-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38656-125">Remarks</span></span>

<span data-ttu-id="38656-126">Ta funkcja zawija wywołanie do [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) metody.</span><span class="sxs-lookup"><span data-stu-id="38656-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="38656-127">Ze względu na zasady propagacji kwalifikator kwalifikator określonego może zostały odziedziczone z innym obiektem i jedynie zastąpione w bieżącej klasy lub wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="38656-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="38656-128">W tym przypadku `QualifierSet_Delete` metoda powoduje zresetowanie kwalifikator do oryginalnej wartości dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="38656-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="38656-129">Funkcja w takiej sytuacji zwraca kod stanu `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="38656-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="38656-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38656-130">Requirements</span></span>  
 <span data-ttu-id="38656-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38656-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38656-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="38656-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="38656-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="38656-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38656-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38656-134">See also</span></span>  
[<span data-ttu-id="38656-135">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="38656-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
