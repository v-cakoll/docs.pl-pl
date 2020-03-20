---
title: GetMethodOrigin, funkcja (odwołanie do niezarządzanego interfejsu API)
description: Funkcja GetMethodOrigin określa klasę, w której zadeklarowana jest metoda.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b4609b6649be875aea7dfcf52ba36b1e98ab7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176802"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="7aafe-103">GetMethodOrigin, funkcja</span><span class="sxs-lookup"><span data-stu-id="7aafe-103">GetMethodOrigin function</span></span>
<span data-ttu-id="7aafe-104">Określa klasę, w której metoda jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="7aafe-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="7aafe-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7aafe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a><span data-ttu-id="7aafe-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7aafe-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7aafe-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="7aafe-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7aafe-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="7aafe-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="7aafe-109">[w] Nazwa metody dla obiektu, którego klasa będąca właścicielem jest żądana.</span><span class="sxs-lookup"><span data-stu-id="7aafe-109">[in] The name of the method for the object whose owning class is being requested.</span></span>

`pstrClassName`  
<span data-ttu-id="7aafe-110">[na zewnątrz] Odbiera nazwę klasy, która jest właścicielem metody.</span><span class="sxs-lookup"><span data-stu-id="7aafe-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="7aafe-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7aafe-111">Return value</span></span>

<span data-ttu-id="7aafe-112">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="7aafe-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7aafe-113">Stały</span><span class="sxs-lookup"><span data-stu-id="7aafe-113">Constant</span></span>  |<span data-ttu-id="7aafe-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="7aafe-114">Value</span></span>  |<span data-ttu-id="7aafe-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7aafe-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="7aafe-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="7aafe-116">0x80041002</span></span> | <span data-ttu-id="7aafe-117">Nie znaleziono określonej metody.</span><span class="sxs-lookup"><span data-stu-id="7aafe-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7aafe-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7aafe-118">0x80041008</span></span> | <span data-ttu-id="7aafe-119">Co najmniej jeden parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="7aafe-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7aafe-120">0</span><span class="sxs-lookup"><span data-stu-id="7aafe-120">0</span></span> | <span data-ttu-id="7aafe-121">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7aafe-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="7aafe-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7aafe-122">Remarks</span></span>

<span data-ttu-id="7aafe-123">Ta funkcja zawija wywołanie [metody IWbemClassObject::GetMethodOrigin.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)</span><span class="sxs-lookup"><span data-stu-id="7aafe-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="7aafe-124">Ponieważ klasa może dziedziczyć metody z jednej lub więcej klas podstawowych, deweloperzy często chcą określić klasę, w której zdefiniowano daną metodę.</span><span class="sxs-lookup"><span data-stu-id="7aafe-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="7aafe-125">Parametr `pstrClassName` nie może wskazywać `BSTR` prawidłowe przed wywołane funkcji, ponieważ jest to `out` parametr; ten wskaźnik nie jest cofnięty po powrocie funkcji.</span><span class="sxs-lookup"><span data-stu-id="7aafe-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="7aafe-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7aafe-126">Requirements</span></span>  
<span data-ttu-id="7aafe-127">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aafe-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aafe-128">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7aafe-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7aafe-129">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7aafe-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aafe-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7aafe-130">See also</span></span>

- [<span data-ttu-id="7aafe-131">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="7aafe-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
