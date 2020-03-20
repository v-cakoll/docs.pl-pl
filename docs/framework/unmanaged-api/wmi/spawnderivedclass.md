---
title: SpawnDerivedClass, funkcja (odwołanie do niezarządzanego interfejsu API)
description: SpawnDerivedClass Funkcja tworzy nowy obiekt, który pochodzi z obiektu.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e9784f8a024c788823dc702794b2b86eea1827bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174852"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="21637-103">SpawnDerivedClass, funkcja</span><span class="sxs-lookup"><span data-stu-id="21637-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="21637-104">Tworzy nowo pochodny obiekt klasy z określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="21637-104">Creates a newly derived class object from a specified object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="21637-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="21637-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a><span data-ttu-id="21637-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="21637-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="21637-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="21637-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="21637-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="21637-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="21637-109">[w] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="21637-109">[in] Reserved.</span></span> <span data-ttu-id="21637-110">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="21637-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="21637-111">[na zewnątrz] Odbiera wskaźnik do nowego obiektu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="21637-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="21637-112">Jeśli wystąpi błąd, nowy obiekt nie `ppNewClass` jest zwracany i pozostaje niezmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="21637-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="21637-113">Jego wartość `null`nie może być .</span><span class="sxs-lookup"><span data-stu-id="21637-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="21637-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="21637-114">Return value</span></span>

<span data-ttu-id="21637-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="21637-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="21637-116">Stały</span><span class="sxs-lookup"><span data-stu-id="21637-116">Constant</span></span>  |<span data-ttu-id="21637-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="21637-117">Value</span></span>  |<span data-ttu-id="21637-118">Opis</span><span class="sxs-lookup"><span data-stu-id="21637-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="21637-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="21637-119">0x80041001</span></span> | <span data-ttu-id="21637-120">Wystąpiła ogólna porażka.</span><span class="sxs-lookup"><span data-stu-id="21637-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="21637-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="21637-121">0x80041016</span></span> | <span data-ttu-id="21637-122">Zażądano nieprawidłowej operacji, takiej jak tarło klasy z wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="21637-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="21637-123">Klasa źródłowsza nie została całkowicie zdefiniowana lub zarejestrowana w programie Windows Management, więc nowa klasa pochodna nie jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="21637-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="21637-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="21637-124">0x80041006</span></span> | <span data-ttu-id="21637-125">Za mało pamięci jest dostępna do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="21637-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="21637-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="21637-126">0x80041008</span></span> | <span data-ttu-id="21637-127">Parametr `ppNewClass` ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="21637-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="21637-128">0</span><span class="sxs-lookup"><span data-stu-id="21637-128">0</span></span> | <span data-ttu-id="21637-129">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="21637-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="21637-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21637-130">Remarks</span></span>

<span data-ttu-id="21637-131">Ta funkcja zawija wywołanie [metody IWbemClassObject::SpawnDerivedClass.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)</span><span class="sxs-lookup"><span data-stu-id="21637-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="21637-132">`ptr`musi być definicją klasy, która staje się klasą nadrzędną obiektu zduplikowanego.</span><span class="sxs-lookup"><span data-stu-id="21637-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="21637-133">Zwrócony obiekt staje się podklasą bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="21637-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="21637-134">Nowy obiekt zwracany automatycznie `ppNewClass` staje się podklasą bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="21637-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="21637-135">Tego zachowania nie można zastąpić.</span><span class="sxs-lookup"><span data-stu-id="21637-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="21637-136">Nie ma innej metody, za pomocą której można tworzyć podklasy (klasy pochodne).</span><span class="sxs-lookup"><span data-stu-id="21637-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="21637-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21637-137">Requirements</span></span>  
 <span data-ttu-id="21637-138">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21637-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21637-139">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="21637-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="21637-140">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="21637-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21637-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21637-141">See also</span></span>

- [<span data-ttu-id="21637-142">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="21637-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
