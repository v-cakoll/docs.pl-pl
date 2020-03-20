---
title: funkcja QualifierSet_Delete (odwołanie do interfejsu API niezarządzanego)
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
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174904"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="ab0f4-103">QualifierSet_Delete funkcja</span><span class="sxs-lookup"><span data-stu-id="ab0f4-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="ab0f4-104">Usuwa określony kwalifikator według nazwy.</span><span class="sxs-lookup"><span data-stu-id="ab0f4-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ab0f4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab0f4-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="ab0f4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab0f4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ab0f4-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="ab0f4-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="ab0f4-108">`ptr`[w] Wskaźnik do [wystąpienia IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="ab0f4-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="ab0f4-109">`wszName`[w] Nazwa kwalifikatora do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="ab0f4-109">`wszName` [in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="ab0f4-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ab0f4-110">Return value</span></span>

<span data-ttu-id="ab0f4-111">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="ab0f4-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ab0f4-112">Stały</span><span class="sxs-lookup"><span data-stu-id="ab0f4-112">Constant</span></span>  |<span data-ttu-id="ab0f4-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="ab0f4-113">Value</span></span>  |<span data-ttu-id="ab0f4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ab0f4-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ab0f4-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ab0f4-115">0x80041008</span></span> | <span data-ttu-id="ab0f4-116">Parametr `wszName` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ab0f4-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="ab0f4-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="ab0f4-117">0x80041016</span></span> | <span data-ttu-id="ab0f4-118">Usunięcie tego kwalifikatora jest niezgodne z prawem.</span><span class="sxs-lookup"><span data-stu-id="ab0f4-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="ab0f4-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ab0f4-119">0x80041002</span></span> | <span data-ttu-id="ab0f4-120">Nie znaleziono określonego kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="ab0f4-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ab0f4-121">0</span><span class="sxs-lookup"><span data-stu-id="ab0f4-121">0</span></span> | <span data-ttu-id="ab0f4-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ab0f4-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="ab0f4-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="ab0f4-123">0x40002</span></span> | <span data-ttu-id="ab0f4-124">Lokalne zastąpienie zostało usunięte, a oryginalny kwalifikator z obiektu nadrzędnego został wznowiony zakres.</span><span class="sxs-lookup"><span data-stu-id="ab0f4-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ab0f4-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab0f4-125">Remarks</span></span>

<span data-ttu-id="ab0f4-126">Ta funkcja zawija wywołanie [metody IWbemQualifierSet::Delete.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)</span><span class="sxs-lookup"><span data-stu-id="ab0f4-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="ab0f4-127">Ze względu na reguły propagacji kwalifikatora określonego kwalifikatora mogły być dziedziczone z innego obiektu i jedynie zastąpione w bieżącej klasie lub wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="ab0f4-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="ab0f4-128">W takim przypadku `QualifierSet_Delete` metoda resetuje kwalifikator do oryginalnej wartości dziedziczonej.</span><span class="sxs-lookup"><span data-stu-id="ab0f4-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="ab0f4-129">Funkcja w tym przypadku zwraca `WBEM_S_RESET_TO_DEFAULT`kod stanu .</span><span class="sxs-lookup"><span data-stu-id="ab0f4-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab0f4-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab0f4-130">Requirements</span></span>  
 <span data-ttu-id="ab0f4-131">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab0f4-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab0f4-132">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ab0f4-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ab0f4-133">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ab0f4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab0f4-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab0f4-134">See also</span></span>

- [<span data-ttu-id="ab0f4-135">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="ab0f4-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
