---
title: QualifierSet_Delete — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_Delete usuwa kwalifikator według nazwy.
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
ms.openlocfilehash: 4bc26a16650a5beecc17898e0421e79536713deb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798337"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="124cf-103">QualifierSet_Delete, funkcja</span><span class="sxs-lookup"><span data-stu-id="124cf-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="124cf-104">Usuwa określony kwalifikator według nazwy.</span><span class="sxs-lookup"><span data-stu-id="124cf-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="124cf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="124cf-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="124cf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="124cf-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="124cf-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="124cf-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="124cf-108">podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="124cf-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="124cf-109">podczas Nazwa kwalifikatora do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="124cf-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="124cf-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="124cf-110">Return value</span></span>

<span data-ttu-id="124cf-111">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="124cf-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="124cf-112">Stała</span><span class="sxs-lookup"><span data-stu-id="124cf-112">Constant</span></span>  |<span data-ttu-id="124cf-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="124cf-113">Value</span></span>  |<span data-ttu-id="124cf-114">Opis</span><span class="sxs-lookup"><span data-stu-id="124cf-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="124cf-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="124cf-115">0x80041008</span></span> | <span data-ttu-id="124cf-116">`wszName` Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="124cf-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="124cf-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="124cf-117">0x80041016</span></span> | <span data-ttu-id="124cf-118">Usuwanie tego kwalifikatora jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="124cf-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="124cf-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="124cf-119">0x80041002</span></span> | <span data-ttu-id="124cf-120">Nie znaleziono określonego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="124cf-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="124cf-121">0</span><span class="sxs-lookup"><span data-stu-id="124cf-121">0</span></span> | <span data-ttu-id="124cf-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="124cf-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="124cf-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="124cf-123">0x40002</span></span> | <span data-ttu-id="124cf-124">Zastępowanie lokalne zostało usunięte, a oryginalny kwalifikator z obiektu nadrzędnego został wznowiony.</span><span class="sxs-lookup"><span data-stu-id="124cf-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="124cf-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="124cf-125">Remarks</span></span>

<span data-ttu-id="124cf-126">Ta funkcja otacza wywołanie metody [IWbemQualifierSet::D Usuń](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) .</span><span class="sxs-lookup"><span data-stu-id="124cf-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="124cf-127">Ze względu na reguły propagacji kwalifikatora, określony kwalifikator może być Dziedziczony z innego obiektu i jedynie zastępowany w bieżącej klasie lub wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="124cf-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="124cf-128">W takim przypadku `QualifierSet_Delete` metoda resetuje kwalifikator do pierwotnej dziedziczonej wartości.</span><span class="sxs-lookup"><span data-stu-id="124cf-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="124cf-129">Funkcja w tym przypadku zwraca kod `WBEM_S_RESET_TO_DEFAULT`stanu.</span><span class="sxs-lookup"><span data-stu-id="124cf-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="124cf-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="124cf-130">Requirements</span></span>  
 <span data-ttu-id="124cf-131">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="124cf-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="124cf-132">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="124cf-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="124cf-133">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="124cf-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="124cf-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="124cf-134">See also</span></span>

- [<span data-ttu-id="124cf-135">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="124cf-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
