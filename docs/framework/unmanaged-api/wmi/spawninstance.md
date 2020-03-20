---
title: SpawnInstance, funkcja (odwołanie do interfejsu API niezarządzanego)
description: SpawnInstance Funkcja tworzy nowe wystąpienie klasy.
ms.date: 11/06/2017
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
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176724"
---
# <a name="spawninstance-function"></a><span data-ttu-id="2deaa-103">SpawnInstance, funkcja</span><span class="sxs-lookup"><span data-stu-id="2deaa-103">SpawnInstance function</span></span>
<span data-ttu-id="2deaa-104">Tworzy nowe wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="2deaa-104">Creates a new instance of a class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2deaa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2deaa-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a><span data-ttu-id="2deaa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2deaa-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2deaa-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="2deaa-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2deaa-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="2deaa-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="2deaa-109">[w] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="2deaa-109">[in] Reserved.</span></span> <span data-ttu-id="2deaa-110">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="2deaa-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="2deaa-111">[na zewnątrz] Odbiera wskaźnik do nowego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="2deaa-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="2deaa-112">Jeśli wystąpi błąd, nowy obiekt nie `ppNewInstance` jest zwracany i pozostaje niezmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="2deaa-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="2deaa-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2deaa-113">Return value</span></span>

<span data-ttu-id="2deaa-114">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="2deaa-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2deaa-115">Stały</span><span class="sxs-lookup"><span data-stu-id="2deaa-115">Constant</span></span>  |<span data-ttu-id="2deaa-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="2deaa-116">Value</span></span>  |<span data-ttu-id="2deaa-117">Opis</span><span class="sxs-lookup"><span data-stu-id="2deaa-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="2deaa-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="2deaa-118">0x80041020</span></span> | <span data-ttu-id="2deaa-119">`ptr`nie jest prawidłową definicją klasy i nie może zrodzić nowych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="2deaa-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="2deaa-120">Albo jest niekompletny lub nie został zarejestrowany w usłudze Windows Management, wywołując [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="2deaa-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2deaa-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2deaa-121">0x80041006</span></span> | <span data-ttu-id="2deaa-122">Za mało pamięci jest dostępna do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="2deaa-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2deaa-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2deaa-123">0x80041008</span></span> | <span data-ttu-id="2deaa-124">Parametr `ppNewClass` ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="2deaa-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2deaa-125">0</span><span class="sxs-lookup"><span data-stu-id="2deaa-125">0</span></span> | <span data-ttu-id="2deaa-126">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2deaa-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2deaa-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2deaa-127">Remarks</span></span>

<span data-ttu-id="2deaa-128">Ta funkcja zawija wywołanie [metody IWbemClassObject::SpawnInstance.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)</span><span class="sxs-lookup"><span data-stu-id="2deaa-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="2deaa-129">`ptr`musi być definicją klasy uzyskaną z zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="2deaa-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="2deaa-130">(Należy zauważyć, że tarło wystąpienia z wystąpienia jest obsługiwane, ale zwrócone wystąpienie jest puste.) Następnie należy użyć tej definicji klasy do tworzenia nowych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="2deaa-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="2deaa-131">Wywołanie funkcji [PutInstanceWmi](putinstancewmi.md) jest wymagane, jeśli zamierzasz zapisać wystąpienie w usłudze Windows Management.</span><span class="sxs-lookup"><span data-stu-id="2deaa-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="2deaa-132">Nowy obiekt zwracany automatycznie `ppNewClass` staje się podklasą bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="2deaa-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="2deaa-133">Tego zachowania nie można zastąpić.</span><span class="sxs-lookup"><span data-stu-id="2deaa-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="2deaa-134">Nie ma innej metody, za pomocą której można tworzyć podklasy (klasy pochodne).</span><span class="sxs-lookup"><span data-stu-id="2deaa-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="2deaa-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2deaa-135">Requirements</span></span>  
 <span data-ttu-id="2deaa-136">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2deaa-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2deaa-137">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2deaa-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2deaa-138">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2deaa-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2deaa-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2deaa-139">See also</span></span>

- [<span data-ttu-id="2deaa-140">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="2deaa-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
