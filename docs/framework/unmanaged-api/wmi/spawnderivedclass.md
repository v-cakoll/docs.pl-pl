---
title: "Funkcja SpawnDerivedClass (niezarządzany wykaz interfejsów API)"
description: "Funkcja SpawnDerivedClass tworzy nowy obiekt, który pochodzi z obiektu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SpawnDerivedClass
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SpawnDerivedClass
helpviewer_keywords: SpawnDerivedClass function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16f9a762c87e1e181202739b70cd978a80864f04
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="4bfd7-103">Funkcja SpawnDerivedClass</span><span class="sxs-lookup"><span data-stu-id="4bfd7-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="4bfd7-104">Tworzy obiekt klasy pochodnej nowo od określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4bfd7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bfd7-105">Syntax</span></span>  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="4bfd7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bfd7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4bfd7-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4bfd7-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="4bfd7-109">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-109">[in] Reserved.</span></span> <span data-ttu-id="4bfd7-110">Ten parametr musi wynosić 0.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="4bfd7-111">[out] Uzyskuje wskaźnik do nowego obiektu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="4bfd7-112">Jeśli wystąpi błąd, nowy obiekt nie jest zwracany, i `ppNewClass` jest lewej nie mają być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="4bfd7-113">Wartość nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="4bfd7-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4bfd7-114">Return value</span></span>

<span data-ttu-id="4bfd7-115">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="4bfd7-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4bfd7-116">Stała</span><span class="sxs-lookup"><span data-stu-id="4bfd7-116">Constant</span></span>  |<span data-ttu-id="4bfd7-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="4bfd7-117">Value</span></span>  |<span data-ttu-id="4bfd7-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4bfd7-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="4bfd7-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="4bfd7-119">0x80041001</span></span> | <span data-ttu-id="4bfd7-120">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="4bfd7-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="4bfd7-121">0x80041016</span></span> | <span data-ttu-id="4bfd7-122">Zażądano nieprawidłową operację, takiej jak duplikowanie klasy z wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="4bfd7-123">Klasa źródłowa całkowicie nie została zdefiniowana lub jest zarejestrowana w usłudze zarządzania systemu Windows, więc nowej klasy pochodnej nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4bfd7-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4bfd7-124">0x80041006</span></span> | <span data-ttu-id="4bfd7-125">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4bfd7-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4bfd7-126">0x80041008</span></span> | <span data-ttu-id="4bfd7-127">`ppNewClass`jest `null`.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="4bfd7-128">0</span><span class="sxs-lookup"><span data-stu-id="4bfd7-128">0</span></span> | <span data-ttu-id="4bfd7-129">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4bfd7-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bfd7-130">Remarks</span></span>

<span data-ttu-id="4bfd7-131">Ta funkcja jest zawijana wywołanie [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="4bfd7-132">`ptr`musi być definicją klasy, która staje się klasy nadrzędnej uruchomionego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="4bfd7-133">Zwrócony obiekt staje się podklasą bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="4bfd7-134">Nowy obiekt zwracane w `ppNewClass` automatycznie staje się podklasą bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="4bfd7-135">Nie można zastąpić to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="4bfd7-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="4bfd7-136">Brak żadnej innej metody, za pomocą którego można utworzyć podklasy (klasy pochodne).</span><span class="sxs-lookup"><span data-stu-id="4bfd7-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="4bfd7-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4bfd7-137">Requirements</span></span>  
 <span data-ttu-id="4bfd7-138">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bfd7-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bfd7-139">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4bfd7-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4bfd7-140">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4bfd7-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bfd7-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bfd7-141">See also</span></span>  
[<span data-ttu-id="4bfd7-142">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="4bfd7-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
