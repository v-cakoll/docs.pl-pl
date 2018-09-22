---
title: Usuwanie funkcji (niezarządzany wykaz interfejsów API)
description: Funkcja usuwania usuwa określonej właściwości i wszystkich jego kwalifikatory z definicji klasy modelu wspólnych informacji.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 791e75aa60fd651dde1555339e31664a3523e1eb
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46578921"
---
# <a name="delete-function"></a><span data-ttu-id="5a506-103">Usuwanie funkcji</span><span class="sxs-lookup"><span data-stu-id="5a506-103">Delete function</span></span>
<span data-ttu-id="5a506-104">Usuwa określoną właściwość i wszystkich jego kwalifikatory z definicji klasy modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="5a506-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="5a506-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a506-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="5a506-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a506-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5a506-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="5a506-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5a506-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5a506-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="5a506-109">[in] Nazwa właściwości do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="5a506-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="5a506-110">`wszName` musi być wskaźnikiem do prawidłowego `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="5a506-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="5a506-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5a506-111">Return value</span></span>

<span data-ttu-id="5a506-112">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="5a506-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5a506-113">Stała</span><span class="sxs-lookup"><span data-stu-id="5a506-113">Constant</span></span>  |<span data-ttu-id="5a506-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="5a506-114">Value</span></span>  |<span data-ttu-id="5a506-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5a506-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="5a506-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5a506-116">0x80041001</span></span> | <span data-ttu-id="5a506-117">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="5a506-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="5a506-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="5a506-118">0x80041016</span></span> | <span data-ttu-id="5a506-119">Nie można usunąć właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a506-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5a506-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5a506-120">0x80041008</span></span> | <span data-ttu-id="5a506-121">`wszzName` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="5a506-121">`wszzName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="5a506-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="5a506-122">0x80041002</span></span> | <span data-ttu-id="5a506-123">Określona właściwość nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="5a506-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5a506-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5a506-124">0x80041006</span></span> | <span data-ttu-id="5a506-125">Nie ma wystarczającej ilości pamięci do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="5a506-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="5a506-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="5a506-126">0x8004101c</span></span> | <span data-ttu-id="5a506-127">Właściwość jest dziedziczona z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="5a506-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="5a506-128">Właściwość jest właściwością systemu.</span><span class="sxs-lookup"><span data-stu-id="5a506-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5a506-129">0</span><span class="sxs-lookup"><span data-stu-id="5a506-129">0</span></span> | <span data-ttu-id="5a506-130">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5a506-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="5a506-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="5a506-131">0x80041030</span></span> | <span data-ttu-id="5a506-132">Funkcja usunięte wartość domyślną zastępowania bieżącej klasy.</span><span class="sxs-lookup"><span data-stu-id="5a506-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="5a506-133">Wartość domyślna tej właściwości w klasie nadrzędnej została reactiviated.</span><span class="sxs-lookup"><span data-stu-id="5a506-133">The default value for this property in the parent class has been reactiviated.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="5a506-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a506-134">Remarks</span></span>

<span data-ttu-id="5a506-135">Ta funkcja zawija wywołanie do [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) metody.</span><span class="sxs-lookup"><span data-stu-id="5a506-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a506-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a506-136">Requirements</span></span>  
 <span data-ttu-id="5a506-137">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a506-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a506-138">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5a506-138">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5a506-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5a506-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a506-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a506-140">See also</span></span>  
[<span data-ttu-id="5a506-141">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="5a506-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
