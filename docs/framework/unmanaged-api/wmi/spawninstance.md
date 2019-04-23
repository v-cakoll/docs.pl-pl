---
title: Funkcja SpawnInstance (niezarządzany wykaz interfejsów API)
description: Funkcja SpawnInstance tworzy nowe wystąpienie klasy.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8056ef18089f56f1f9b6717d505fa3d058957541
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074420"
---
# <a name="spawninstance-function"></a><span data-ttu-id="5061b-103">SpawnInstance — funkcja</span><span class="sxs-lookup"><span data-stu-id="5061b-103">SpawnInstance function</span></span>
<span data-ttu-id="5061b-104">Tworzy nowe wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="5061b-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5061b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5061b-105">Syntax</span></span>  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="5061b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5061b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5061b-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="5061b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5061b-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5061b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="5061b-109">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="5061b-109">[in] Reserved.</span></span> <span data-ttu-id="5061b-110">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="5061b-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="5061b-111">[out] Otrzymuje wskaźnik do nowego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="5061b-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="5061b-112">Jeśli wystąpi błąd, nowy obiekt nie jest zwracana, i `ppNewInstance` się po lewej stronie w niezmienionej postaci.</span><span class="sxs-lookup"><span data-stu-id="5061b-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="5061b-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5061b-113">Return value</span></span>

<span data-ttu-id="5061b-114">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="5061b-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5061b-115">Stała</span><span class="sxs-lookup"><span data-stu-id="5061b-115">Constant</span></span>  |<span data-ttu-id="5061b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="5061b-116">Value</span></span>  |<span data-ttu-id="5061b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5061b-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="5061b-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="5061b-118">0x80041020</span></span> | <span data-ttu-id="5061b-119">`ptr` nie jest prawidłową definicją klasy i nie można zduplikować nowych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="5061b-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="5061b-120">Jest on niepełny lub go nie został zarejestrowany za pomocą funkcji zarządzania Windows, wywołując [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="5061b-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5061b-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5061b-121">0x80041006</span></span> | <span data-ttu-id="5061b-122">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="5061b-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5061b-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5061b-123">0x80041008</span></span> | <span data-ttu-id="5061b-124">`ppNewClass` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="5061b-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5061b-125">0</span><span class="sxs-lookup"><span data-stu-id="5061b-125">0</span></span> | <span data-ttu-id="5061b-126">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5061b-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5061b-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5061b-127">Remarks</span></span>

<span data-ttu-id="5061b-128">Ta funkcja zawija wywołanie do [klasy IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) metody.</span><span class="sxs-lookup"><span data-stu-id="5061b-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="5061b-129">`ptr` musi być definicją klasy uzyskana z zarządzania Windows.</span><span class="sxs-lookup"><span data-stu-id="5061b-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="5061b-130">(Należy pamiętać, że podczas duplikowania wystąpienie z wystąpienia usługi jest obsługiwany, ale zwracane wystąpienie jest puste). Następnie możesz użyć tej definicji klasy, do tworzenia nowych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="5061b-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="5061b-131">Wywołanie [PutInstanceWmi](putinstancewmi.md) funkcja jest wymagana, jeśli zamierzasz zapisać wystąpienie zarządzania Windows.</span><span class="sxs-lookup"><span data-stu-id="5061b-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="5061b-132">Nowy obiekt zwrócony w `ppNewClass` automatycznie wybrana zostaje pierwsza podklasę bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5061b-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="5061b-133">Nie można zastąpić to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="5061b-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="5061b-134">Nie ma żadnej innej metody, za pomocą którego można utworzyć podklasy (klas pochodnych).</span><span class="sxs-lookup"><span data-stu-id="5061b-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="5061b-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5061b-135">Requirements</span></span>  
 <span data-ttu-id="5061b-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5061b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5061b-137">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5061b-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5061b-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5061b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5061b-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5061b-139">See also</span></span>

- [<span data-ttu-id="5061b-140">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="5061b-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
