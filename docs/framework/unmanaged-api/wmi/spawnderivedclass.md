---
title: SpawnDerivedClass — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja SpawnDerivedClass tworzy nowy obiekt, który pochodzi od obiektu.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c213f311f1af1e56d0ce24eba3b76f33be541323
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798229"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="df923-103">SpawnDerivedClass, funkcja</span><span class="sxs-lookup"><span data-stu-id="df923-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="df923-104">Tworzy nowo pochodny obiekt klasy na podstawie określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="df923-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="df923-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="df923-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="df923-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="df923-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="df923-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="df923-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="df923-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="df923-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="df923-109">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="df923-109">[in] Reserved.</span></span> <span data-ttu-id="df923-110">Ten parametr musi być równy 0.</span><span class="sxs-lookup"><span data-stu-id="df923-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="df923-111">określoną Odbiera wskaźnik do nowego obiektu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="df923-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="df923-112">Jeśli wystąpi błąd, nowy obiekt nie jest zwracany i `ppNewClass` pozostaje niemodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="df923-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="df923-113">Wartość nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="df923-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="df923-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="df923-114">Return value</span></span>

<span data-ttu-id="df923-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="df923-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="df923-116">Stała</span><span class="sxs-lookup"><span data-stu-id="df923-116">Constant</span></span>  |<span data-ttu-id="df923-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="df923-117">Value</span></span>  |<span data-ttu-id="df923-118">Opis</span><span class="sxs-lookup"><span data-stu-id="df923-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="df923-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="df923-119">0x80041001</span></span> | <span data-ttu-id="df923-120">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="df923-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="df923-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="df923-121">0x80041016</span></span> | <span data-ttu-id="df923-122">Zażądano nieprawidłowej operacji, takiej jak duplikowanie klasy z wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="df923-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="df923-123">Klasa źródłowa nie została całkowicie zdefiniowana lub zarejestrowana w usłudze zarządzania systemem Windows, więc nowa klasa pochodna jest niedozwolona.</span><span class="sxs-lookup"><span data-stu-id="df923-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="df923-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="df923-124">0x80041006</span></span> | <span data-ttu-id="df923-125">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="df923-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="df923-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="df923-126">0x80041008</span></span> | <span data-ttu-id="df923-127">`ppNewClass`jest `null`.</span><span class="sxs-lookup"><span data-stu-id="df923-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="df923-128">0</span><span class="sxs-lookup"><span data-stu-id="df923-128">0</span></span> | <span data-ttu-id="df923-129">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="df923-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="df923-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df923-130">Remarks</span></span>

<span data-ttu-id="df923-131">Ta funkcja otacza wywołanie metody [IWbemClassObject:: SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="df923-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="df923-132">`ptr`musi być definicją klasy, która jest klasą nadrzędną podanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="df923-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="df923-133">Zwrócony obiekt zostanie podklasą bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="df923-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="df923-134">Nowy obiekt zwrócony w programie `ppNewClass` automatycznie zostanie podklasą bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="df923-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="df923-135">Tego zachowania nie można zastąpić.</span><span class="sxs-lookup"><span data-stu-id="df923-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="df923-136">Nie istnieje inna metoda, za pomocą której można tworzyć podklasy (klasy pochodne).</span><span class="sxs-lookup"><span data-stu-id="df923-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="df923-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df923-137">Requirements</span></span>  
 <span data-ttu-id="df923-138">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df923-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df923-139">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="df923-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="df923-140">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="df923-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df923-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df923-141">See also</span></span>

- [<span data-ttu-id="df923-142">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="df923-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
