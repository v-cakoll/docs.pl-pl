---
title: "Funkcja SpawnInstance (niezarządzany wykaz interfejsów API)"
description: "Funkcja SpawnInstance tworzy nowe wystąpienie klasy."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 68508f3000e7f4ac481f940ef4c715366c37125c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="spawninstance-function"></a><span data-ttu-id="55608-103">Funkcja SpawnInstance</span><span class="sxs-lookup"><span data-stu-id="55608-103">SpawnInstance function</span></span>
<span data-ttu-id="55608-104">Tworzy nowe wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="55608-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="55608-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="55608-105">Syntax</span></span>  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="55608-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="55608-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="55608-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="55608-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="55608-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="55608-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="55608-109">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="55608-109">[in] Reserved.</span></span> <span data-ttu-id="55608-110">Ten parametr musi wynosić 0.</span><span class="sxs-lookup"><span data-stu-id="55608-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="55608-111">[out] Uzyskuje wskaźnik do nowego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="55608-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="55608-112">Jeśli wystąpi błąd, nowy obiekt nie jest zwracany, i `ppNewInstance` jest lewej nie mają być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="55608-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="55608-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="55608-113">Return value</span></span>

<span data-ttu-id="55608-114">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="55608-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="55608-115">Stała</span><span class="sxs-lookup"><span data-stu-id="55608-115">Constant</span></span>  |<span data-ttu-id="55608-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="55608-116">Value</span></span>  |<span data-ttu-id="55608-117">Opis</span><span class="sxs-lookup"><span data-stu-id="55608-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="55608-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="55608-118">0x80041020</span></span> | <span data-ttu-id="55608-119">`ptr`nie jest prawidłową definicją klasy i nie można zduplikować nowych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="55608-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="55608-120">Jest on niepełny lub go nie został zarejestrowany z zarządzania systemu Windows przez wywołanie metody [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="55608-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="55608-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="55608-121">0x80041006</span></span> | <span data-ttu-id="55608-122">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="55608-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="55608-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="55608-123">0x80041008</span></span> | <span data-ttu-id="55608-124">`ppNewClass`jest `null`.</span><span class="sxs-lookup"><span data-stu-id="55608-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="55608-125">0</span><span class="sxs-lookup"><span data-stu-id="55608-125">0</span></span> | <span data-ttu-id="55608-126">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="55608-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="55608-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55608-127">Remarks</span></span>

<span data-ttu-id="55608-128">Ta funkcja jest zawijana wywołanie [klasy IWbemClassObject::SpawnInstance](https://msdn.microsoft.com/library/aa391458(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="55608-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](https://msdn.microsoft.com/library/aa391458(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="55608-129">`ptr`musi być definicją klasy uzyskana z zarządzania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="55608-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="55608-130">(Należy pamiętać, że duplikowanie wystąpienia z wystąpienia jest obsługiwana, ale zwrócone wystąpienie jest pusta). Następnie możesz użyć tej definicji klasy, aby utworzyć nowe wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="55608-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="55608-131">Wywołanie [PutInstanceWmi](putinstancewmi.md) funkcja jest wymagana, jeśli zamierzasz zapisać wystąpienie do zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="55608-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>




<span data-ttu-id="55608-132">Nowy obiekt zwracane w `ppNewClass` automatycznie staje się podklasą bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="55608-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="55608-133">Nie można zastąpić to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="55608-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="55608-134">Brak żadnej innej metody, za pomocą którego można utworzyć podklasy (klasy pochodne).</span><span class="sxs-lookup"><span data-stu-id="55608-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="55608-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55608-135">Requirements</span></span>  
 <span data-ttu-id="55608-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55608-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55608-137">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="55608-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="55608-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="55608-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55608-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55608-139">See also</span></span>  
[<span data-ttu-id="55608-140">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="55608-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
