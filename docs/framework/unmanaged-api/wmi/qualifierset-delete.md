---
title: "Funkcja QualifierSet_Delete (niezarządzany wykaz interfejsów API)"
description: "Funkcja QualifierSet_Delete usuwa kwalifikatora według nazwy."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Delete
helpviewer_keywords: QualifierSet_Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e7b5650a0b47fd8d9b64bb9d0fff3511afe2d43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="75611-103">Funkcja QualifierSet_Delete</span><span class="sxs-lookup"><span data-stu-id="75611-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="75611-104">Usuwa określony kwalifikatora według nazwy.</span><span class="sxs-lookup"><span data-stu-id="75611-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="75611-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="75611-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="75611-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="75611-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="75611-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="75611-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="75611-108">[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="75611-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="75611-109">[in] Nazwa kwalifikatora do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="75611-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="75611-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75611-110">Return value</span></span>

<span data-ttu-id="75611-111">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="75611-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="75611-112">Stała</span><span class="sxs-lookup"><span data-stu-id="75611-112">Constant</span></span>  |<span data-ttu-id="75611-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="75611-113">Value</span></span>  |<span data-ttu-id="75611-114">Opis</span><span class="sxs-lookup"><span data-stu-id="75611-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="75611-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="75611-115">0x80041008</span></span> | <span data-ttu-id="75611-116">`wszName` Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="75611-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="75611-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="75611-117">0x80041016</span></span> | <span data-ttu-id="75611-118">Usunięcie tego kwalifikatora jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="75611-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="75611-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="75611-119">0x80041002</span></span> | <span data-ttu-id="75611-120">Nie można odnaleźć określonego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="75611-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="75611-121">0</span><span class="sxs-lookup"><span data-stu-id="75611-121">0</span></span> | <span data-ttu-id="75611-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="75611-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="75611-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="75611-123">0x40002</span></span> | <span data-ttu-id="75611-124">Zastąpienie lokalnej został usunięty, i oryginalnego kwalifikator z obiektu nadrzędnego wznowił zakresu.</span><span class="sxs-lookup"><span data-stu-id="75611-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="75611-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75611-125">Remarks</span></span>

<span data-ttu-id="75611-126">Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="75611-126">This function wraps a call to the [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="75611-127">Ze względu na zasady propagacji kwalifikator kwalifikator określonego może zostały odziedziczone z innym obiektem i jedynie zastąpione w bieżącej klasy lub wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="75611-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="75611-128">W takim przypadku `QualifierSet_Delete` metoda powoduje zresetowanie kwalifikator to oryginalnej wartości dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="75611-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="75611-129">W takim przypadku funkcja kod stanu `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="75611-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="75611-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75611-130">Requirements</span></span>  
 <span data-ttu-id="75611-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75611-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75611-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="75611-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="75611-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="75611-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75611-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75611-134">See also</span></span>  
[<span data-ttu-id="75611-135">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="75611-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
