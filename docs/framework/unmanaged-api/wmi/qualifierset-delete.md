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
ms.openlocfilehash: 543cc63b3e2188c11a6a8bf1eaa846461375be99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180079"
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="a1a87-103">QualifierSet_Delete — funkcja</span><span class="sxs-lookup"><span data-stu-id="a1a87-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="a1a87-104">Usuwa określony kwalifikator według nazwy.</span><span class="sxs-lookup"><span data-stu-id="a1a87-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a1a87-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1a87-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="a1a87-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1a87-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a1a87-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="a1a87-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="a1a87-108">[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1a87-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="a1a87-109">[in] Nazwa kwalifikatora do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="a1a87-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="a1a87-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a1a87-110">Return value</span></span>

<span data-ttu-id="a1a87-111">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="a1a87-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a1a87-112">Stała</span><span class="sxs-lookup"><span data-stu-id="a1a87-112">Constant</span></span>  |<span data-ttu-id="a1a87-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="a1a87-113">Value</span></span>  |<span data-ttu-id="a1a87-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a87-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a1a87-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a1a87-115">0x80041008</span></span> | <span data-ttu-id="a1a87-116">`wszName` Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a1a87-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="a1a87-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="a1a87-117">0x80041016</span></span> | <span data-ttu-id="a1a87-118">Usunięcie tego kwalifikatora jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="a1a87-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="a1a87-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a1a87-119">0x80041002</span></span> | <span data-ttu-id="a1a87-120">Nie można odnaleźć określonego kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="a1a87-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a1a87-121">0</span><span class="sxs-lookup"><span data-stu-id="a1a87-121">0</span></span> | <span data-ttu-id="a1a87-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a1a87-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="a1a87-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="a1a87-123">0x40002</span></span> | <span data-ttu-id="a1a87-124">Zastąpienie lokalnych została usunięta i oryginalny kwalifikator z obiektu nadrzędnego wznowił zakresu.</span><span class="sxs-lookup"><span data-stu-id="a1a87-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a1a87-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1a87-125">Remarks</span></span>

<span data-ttu-id="a1a87-126">Ta funkcja zawija wywołanie do [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) metody.</span><span class="sxs-lookup"><span data-stu-id="a1a87-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="a1a87-127">Ze względu na zasady propagacji kwalifikator kwalifikator określonego może zostały odziedziczone z innym obiektem i jedynie zastąpione w bieżącej klasy lub wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1a87-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="a1a87-128">W tym przypadku `QualifierSet_Delete` metoda powoduje zresetowanie kwalifikator do oryginalnej wartości dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="a1a87-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="a1a87-129">Funkcja w takiej sytuacji zwraca kod stanu `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="a1a87-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="a1a87-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1a87-130">Requirements</span></span>  
 <span data-ttu-id="a1a87-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1a87-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1a87-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a1a87-132">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="a1a87-133">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a1a87-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1a87-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1a87-134">See also</span></span>

- [<span data-ttu-id="a1a87-135">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="a1a87-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
