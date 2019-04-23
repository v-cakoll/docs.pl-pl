---
title: Funkcja Beingenumeration (niezarządzany wykaz interfejsów API)
description: Funkcja Beingenumeration resetuje moduł wyliczający na początku tego wyliczenia
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4221dbea2b5ad98f889e04eb8a9b6d992b59066e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212300"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="03be6-103">BeingEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="03be6-103">BeginEnumeration function</span></span>
<span data-ttu-id="03be6-104">Resetuje modułu wyliczającego do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="03be6-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="03be6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="03be6-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="03be6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="03be6-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="03be6-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="03be6-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="03be6-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="03be6-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="03be6-109">[in] Bitowa kombinacja wartości opisanych w lub flag [uwagi](#remarks) sekcji, która kontroluje właściwości zawartych w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="03be6-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="03be6-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="03be6-110">Return value</span></span>

<span data-ttu-id="03be6-111">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="03be6-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="03be6-112">Stała</span><span class="sxs-lookup"><span data-stu-id="03be6-112">Constant</span></span>  |<span data-ttu-id="03be6-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="03be6-113">Value</span></span>  |<span data-ttu-id="03be6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="03be6-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="03be6-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="03be6-115">0x80041008</span></span> | <span data-ttu-id="03be6-116">Kombinacja flag w `lEnumFlags` jest nieprawidłowy lub nieprawidłowy argument został określony.</span><span class="sxs-lookup"><span data-stu-id="03be6-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="03be6-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="03be6-117">0x8004101d</span></span> | <span data-ttu-id="03be6-118">Drugie wywołanie `BeginEnumeration` został utworzony bez interwencyjnego wywołania [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="03be6-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="03be6-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="03be6-119">0x80041006</span></span> | <span data-ttu-id="03be6-120">Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="03be6-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="03be6-121">0</span><span class="sxs-lookup"><span data-stu-id="03be6-121">0</span></span> | <span data-ttu-id="03be6-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="03be6-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="03be6-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03be6-123">Remarks</span></span>

<span data-ttu-id="03be6-124">Ta funkcja zawija wywołanie do [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) metody.</span><span class="sxs-lookup"><span data-stu-id="03be6-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="03be6-125">Flagi, które mogą być przekazywane jako `lEnumFlags` argument są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="03be6-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="03be6-126">Można łączyć z jedną flagę z każdej grupy za pomocą jakakolwiek Flaga w żadnej innej grupy.</span><span class="sxs-lookup"><span data-stu-id="03be6-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="03be6-127">Jednak flagi z tej samej grupy wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="03be6-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="03be6-128">**Grupa 1**</span><span class="sxs-lookup"><span data-stu-id="03be6-128">**Group 1**</span></span>

|<span data-ttu-id="03be6-129">Stała</span><span class="sxs-lookup"><span data-stu-id="03be6-129">Constant</span></span>  |<span data-ttu-id="03be6-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="03be6-130">Value</span></span>  |<span data-ttu-id="03be6-131">Opis</span><span class="sxs-lookup"><span data-stu-id="03be6-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="03be6-132">0x4</span><span class="sxs-lookup"><span data-stu-id="03be6-132">0x4</span></span> | <span data-ttu-id="03be6-133">Zawierają właściwości, które stanowią tylko klucz.</span><span class="sxs-lookup"><span data-stu-id="03be6-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="03be6-134">0x8</span><span class="sxs-lookup"><span data-stu-id="03be6-134">0x8</span></span> | <span data-ttu-id="03be6-135">Zawierają właściwości, które są tylko odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="03be6-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="03be6-136">**Grupa 2**</span><span class="sxs-lookup"><span data-stu-id="03be6-136">**Group 2**</span></span>

<span data-ttu-id="03be6-137">Stała</span><span class="sxs-lookup"><span data-stu-id="03be6-137">Constant</span></span>  |<span data-ttu-id="03be6-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="03be6-138">Value</span></span>  |<span data-ttu-id="03be6-139">Opis</span><span class="sxs-lookup"><span data-stu-id="03be6-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="03be6-140">0x30</span><span class="sxs-lookup"><span data-stu-id="03be6-140">0x30</span></span> | <span data-ttu-id="03be6-141">Ograniczenie wyliczenia tylko właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="03be6-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="03be6-142">0x40</span><span class="sxs-lookup"><span data-stu-id="03be6-142">0x40</span></span> | <span data-ttu-id="03be6-143">Dołącz właściwości lokalne i propagowany, ale wykluczyć wyliczenia właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="03be6-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="03be6-144">Dla klas:</span><span class="sxs-lookup"><span data-stu-id="03be6-144">For classes:</span></span>

<span data-ttu-id="03be6-145">Stała</span><span class="sxs-lookup"><span data-stu-id="03be6-145">Constant</span></span>  |<span data-ttu-id="03be6-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="03be6-146">Value</span></span>  |<span data-ttu-id="03be6-147">Opis</span><span class="sxs-lookup"><span data-stu-id="03be6-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="03be6-148">0x100</span><span class="sxs-lookup"><span data-stu-id="03be6-148">0x100</span></span> | <span data-ttu-id="03be6-149">Ograniczenie wyliczenia właściwości przesłonięcia w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="03be6-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="03be6-150">0x100</span><span class="sxs-lookup"><span data-stu-id="03be6-150">0x100</span></span> | <span data-ttu-id="03be6-151">Ograniczenie wyliczenia właściwości zastąpione w bieżącej definicji klas i nowe właściwości zdefiniowane w klasie.</span><span class="sxs-lookup"><span data-stu-id="03be6-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="03be6-152">0x300</span><span class="sxs-lookup"><span data-stu-id="03be6-152">0x300</span></span> | <span data-ttu-id="03be6-153">A maski (zamiast flaga) do zastosowania wobec `lEnumFlags` wartość, aby sprawdzić, czy w obu `WBEM_FLAG_CLASS_OVERRIDES_ONLY` lub `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="03be6-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="03be6-154">0x10</span><span class="sxs-lookup"><span data-stu-id="03be6-154">0x10</span></span> | <span data-ttu-id="03be6-155">Ograniczenie wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy.</span><span class="sxs-lookup"><span data-stu-id="03be6-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="03be6-156">0x20</span><span class="sxs-lookup"><span data-stu-id="03be6-156">0x20</span></span> | <span data-ttu-id="03be6-157">Ograniczenie wyliczenia właściwości, które są dziedziczone z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="03be6-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="03be6-158">Dla wystąpień:</span><span class="sxs-lookup"><span data-stu-id="03be6-158">For instances:</span></span>

<span data-ttu-id="03be6-159">Stała</span><span class="sxs-lookup"><span data-stu-id="03be6-159">Constant</span></span>  |<span data-ttu-id="03be6-160">Wartość</span><span class="sxs-lookup"><span data-stu-id="03be6-160">Value</span></span>  |<span data-ttu-id="03be6-161">Opis</span><span class="sxs-lookup"><span data-stu-id="03be6-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="03be6-162">0x10</span><span class="sxs-lookup"><span data-stu-id="03be6-162">0x10</span></span> | <span data-ttu-id="03be6-163">Ograniczenie wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy.</span><span class="sxs-lookup"><span data-stu-id="03be6-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="03be6-164">0x20</span><span class="sxs-lookup"><span data-stu-id="03be6-164">0x20</span></span> | <span data-ttu-id="03be6-165">Ograniczenie wyliczenia właściwości, które są dziedziczone z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="03be6-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="03be6-166">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03be6-166">Requirements</span></span>  
 <span data-ttu-id="03be6-167">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03be6-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03be6-168">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="03be6-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="03be6-169">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="03be6-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03be6-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03be6-170">See also</span></span>

- [<span data-ttu-id="03be6-171">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="03be6-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)