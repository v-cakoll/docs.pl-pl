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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212300"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="51729-103">BeingEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="51729-103">BeginEnumeration function</span></span>
<span data-ttu-id="51729-104">Resetuje modułu wyliczającego do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="51729-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="51729-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="51729-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="51729-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="51729-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="51729-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="51729-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="51729-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="51729-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="51729-109">[in] Bitowa kombinacja wartości opisanych w lub flag [uwagi](#remarks) sekcji, która kontroluje właściwości zawartych w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="51729-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="51729-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="51729-110">Return value</span></span>

<span data-ttu-id="51729-111">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="51729-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="51729-112">Stała</span><span class="sxs-lookup"><span data-stu-id="51729-112">Constant</span></span>  |<span data-ttu-id="51729-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="51729-113">Value</span></span>  |<span data-ttu-id="51729-114">Opis</span><span class="sxs-lookup"><span data-stu-id="51729-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="51729-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="51729-115">0x80041008</span></span> | <span data-ttu-id="51729-116">Kombinacja flag w `lEnumFlags` jest nieprawidłowy lub nieprawidłowy argument został określony.</span><span class="sxs-lookup"><span data-stu-id="51729-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="51729-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="51729-117">0x8004101d</span></span> | <span data-ttu-id="51729-118">Drugie wywołanie `BeginEnumeration` został utworzony bez interwencyjnego wywołania [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="51729-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="51729-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="51729-119">0x80041006</span></span> | <span data-ttu-id="51729-120">Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="51729-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="51729-121">0</span><span class="sxs-lookup"><span data-stu-id="51729-121">0</span></span> | <span data-ttu-id="51729-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="51729-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="51729-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51729-123">Remarks</span></span>

<span data-ttu-id="51729-124">Ta funkcja zawija wywołanie do [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) metody.</span><span class="sxs-lookup"><span data-stu-id="51729-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="51729-125">Flagi, które mogą być przekazywane jako `lEnumFlags` argument są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="51729-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="51729-126">Można łączyć z jedną flagę z każdej grupy za pomocą jakakolwiek Flaga w żadnej innej grupy.</span><span class="sxs-lookup"><span data-stu-id="51729-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="51729-127">Jednak flagi z tej samej grupy wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="51729-127">However, flags from the same group are mutually exclusive.</span></span> 

**<span data-ttu-id="51729-128">Grupa 1</span><span class="sxs-lookup"><span data-stu-id="51729-128">Group 1</span></span>**

|<span data-ttu-id="51729-129">Stała</span><span class="sxs-lookup"><span data-stu-id="51729-129">Constant</span></span>  |<span data-ttu-id="51729-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="51729-130">Value</span></span>  |<span data-ttu-id="51729-131">Opis</span><span class="sxs-lookup"><span data-stu-id="51729-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="51729-132">0x4</span><span class="sxs-lookup"><span data-stu-id="51729-132">0x4</span></span> | <span data-ttu-id="51729-133">Zawierają właściwości, które stanowią tylko klucz.</span><span class="sxs-lookup"><span data-stu-id="51729-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="51729-134">0x8</span><span class="sxs-lookup"><span data-stu-id="51729-134">0x8</span></span> | <span data-ttu-id="51729-135">Zawierają właściwości, które są tylko odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="51729-135">Include properties that are object references only.</span></span> |

**<span data-ttu-id="51729-136">Grupa 2</span><span class="sxs-lookup"><span data-stu-id="51729-136">Group 2</span></span>**

<span data-ttu-id="51729-137">Stała</span><span class="sxs-lookup"><span data-stu-id="51729-137">Constant</span></span>  |<span data-ttu-id="51729-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="51729-138">Value</span></span>  |<span data-ttu-id="51729-139">Opis</span><span class="sxs-lookup"><span data-stu-id="51729-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="51729-140">0x30</span><span class="sxs-lookup"><span data-stu-id="51729-140">0x30</span></span> | <span data-ttu-id="51729-141">Ograniczenie wyliczenia tylko właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="51729-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="51729-142">0x40</span><span class="sxs-lookup"><span data-stu-id="51729-142">0x40</span></span> | <span data-ttu-id="51729-143">Dołącz właściwości lokalne i propagowany, ale wykluczyć wyliczenia właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="51729-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="51729-144">Dla klas:</span><span class="sxs-lookup"><span data-stu-id="51729-144">For classes:</span></span>

<span data-ttu-id="51729-145">Stała</span><span class="sxs-lookup"><span data-stu-id="51729-145">Constant</span></span>  |<span data-ttu-id="51729-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="51729-146">Value</span></span>  |<span data-ttu-id="51729-147">Opis</span><span class="sxs-lookup"><span data-stu-id="51729-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="51729-148">0x100</span><span class="sxs-lookup"><span data-stu-id="51729-148">0x100</span></span> | <span data-ttu-id="51729-149">Ograniczenie wyliczenia właściwości przesłonięcia w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="51729-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="51729-150">0x100</span><span class="sxs-lookup"><span data-stu-id="51729-150">0x100</span></span> | <span data-ttu-id="51729-151">Ograniczenie wyliczenia właściwości zastąpione w bieżącej definicji klas i nowe właściwości zdefiniowane w klasie.</span><span class="sxs-lookup"><span data-stu-id="51729-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="51729-152">0x300</span><span class="sxs-lookup"><span data-stu-id="51729-152">0x300</span></span> | <span data-ttu-id="51729-153">A maski (zamiast flaga) do zastosowania wobec `lEnumFlags` wartość, aby sprawdzić, czy w obu `WBEM_FLAG_CLASS_OVERRIDES_ONLY` lub `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="51729-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="51729-154">0x10</span><span class="sxs-lookup"><span data-stu-id="51729-154">0x10</span></span> | <span data-ttu-id="51729-155">Ograniczenie wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy.</span><span class="sxs-lookup"><span data-stu-id="51729-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="51729-156">0x20</span><span class="sxs-lookup"><span data-stu-id="51729-156">0x20</span></span> | <span data-ttu-id="51729-157">Ograniczenie wyliczenia właściwości, które są dziedziczone z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="51729-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="51729-158">Dla wystąpień:</span><span class="sxs-lookup"><span data-stu-id="51729-158">For instances:</span></span>

<span data-ttu-id="51729-159">Stała</span><span class="sxs-lookup"><span data-stu-id="51729-159">Constant</span></span>  |<span data-ttu-id="51729-160">Wartość</span><span class="sxs-lookup"><span data-stu-id="51729-160">Value</span></span>  |<span data-ttu-id="51729-161">Opis</span><span class="sxs-lookup"><span data-stu-id="51729-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="51729-162">0x10</span><span class="sxs-lookup"><span data-stu-id="51729-162">0x10</span></span> | <span data-ttu-id="51729-163">Ograniczenie wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy.</span><span class="sxs-lookup"><span data-stu-id="51729-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="51729-164">0x20</span><span class="sxs-lookup"><span data-stu-id="51729-164">0x20</span></span> | <span data-ttu-id="51729-165">Ograniczenie wyliczenia właściwości, które są dziedziczone z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="51729-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="51729-166">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51729-166">Requirements</span></span>  
 <span data-ttu-id="51729-167">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51729-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51729-168">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="51729-168">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="51729-169">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="51729-169">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="51729-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51729-170">See also</span></span>

- [<span data-ttu-id="51729-171">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="51729-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)