---
title: Funkcja SpawnDerivedClass (niezarządzany wykaz interfejsów API)
description: Funkcja SpawnDerivedClass tworzy nowy obiekt, który pochodzi z obiektu.
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
ms.openlocfilehash: 81f4d5219865bf7f7c9e6d284d74d0c249729dfc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040537"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="5f344-103">SpawnDerivedClass — funkcja</span><span class="sxs-lookup"><span data-stu-id="5f344-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="5f344-104">Tworzy obiekt klasy pochodnej nowo od określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5f344-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5f344-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f344-105">Syntax</span></span>  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="5f344-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f344-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5f344-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="5f344-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5f344-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5f344-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="5f344-109">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="5f344-109">[in] Reserved.</span></span> <span data-ttu-id="5f344-110">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="5f344-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="5f344-111">[out] Otrzymuje wskaźnik do nowego obiektu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="5f344-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="5f344-112">Jeśli wystąpi błąd, nowy obiekt nie jest zwracana, i `ppNewClass` się po lewej stronie w niezmienionej postaci.</span><span class="sxs-lookup"><span data-stu-id="5f344-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="5f344-113">Jego wartość nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="5f344-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="5f344-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5f344-114">Return value</span></span>

<span data-ttu-id="5f344-115">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="5f344-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5f344-116">Stała</span><span class="sxs-lookup"><span data-stu-id="5f344-116">Constant</span></span>  |<span data-ttu-id="5f344-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="5f344-117">Value</span></span>  |<span data-ttu-id="5f344-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5f344-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="5f344-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5f344-119">0x80041001</span></span> | <span data-ttu-id="5f344-120">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="5f344-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="5f344-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="5f344-121">0x80041016</span></span> | <span data-ttu-id="5f344-122">Zażądano Nieprawidłowa operacja, takiej jak duplikowanie klasy z wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="5f344-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="5f344-123">Klasa źródłowa nie jest całkowicie zdefiniowano lub zarejestrowane w usłudze zarządzania Windows, więc nowej klasy pochodnej nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="5f344-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5f344-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5f344-124">0x80041006</span></span> | <span data-ttu-id="5f344-125">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="5f344-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5f344-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5f344-126">0x80041008</span></span> | <span data-ttu-id="5f344-127">`ppNewClass` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="5f344-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5f344-128">0</span><span class="sxs-lookup"><span data-stu-id="5f344-128">0</span></span> | <span data-ttu-id="5f344-129">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5f344-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5f344-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f344-130">Remarks</span></span>

<span data-ttu-id="5f344-131">Ta funkcja zawija wywołanie do [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) metody.</span><span class="sxs-lookup"><span data-stu-id="5f344-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="5f344-132">`ptr` musi być definicją klasy, która staje się klasy nadrzędnej obiektu zduplikowanych.</span><span class="sxs-lookup"><span data-stu-id="5f344-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="5f344-133">Zwrócony obiekt staje się podklasą bieżący obiekt.</span><span class="sxs-lookup"><span data-stu-id="5f344-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="5f344-134">Nowy obiekt zwrócony w `ppNewClass` automatycznie wybrana zostaje pierwsza podklasę bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5f344-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="5f344-135">Nie można zastąpić to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="5f344-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="5f344-136">Nie ma żadnej innej metody, za pomocą którego można utworzyć podklasy (klas pochodnych).</span><span class="sxs-lookup"><span data-stu-id="5f344-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="5f344-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f344-137">Requirements</span></span>  
 <span data-ttu-id="5f344-138">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f344-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f344-139">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5f344-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5f344-140">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5f344-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f344-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f344-141">See also</span></span>

- [<span data-ttu-id="5f344-142">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="5f344-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
