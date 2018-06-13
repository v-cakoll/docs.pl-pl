---
title: Funkcja Beingenumeration (niezarządzany wykaz interfejsów API)
description: Funkcja Beingenumeration resetuje moduł wyliczający na początku wyliczenia
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
ms.openlocfilehash: 9699f0cfc4e9fdb989337681b164cc1e703c1e60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461263"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="d1f42-103">Funkcja Beingenumeration</span><span class="sxs-lookup"><span data-stu-id="d1f42-103">BeginEnumeration function</span></span>
<span data-ttu-id="d1f42-104">Moduł wyliczający resetuje do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d1f42-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d1f42-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1f42-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="d1f42-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1f42-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d1f42-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="d1f42-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="d1f42-108">`ptr` [in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d1f42-108">`ptr` [in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="d1f42-109">[in] Bitowe połączenie flagi lub wartości opisanych w [uwagi](#remarks) sekcji, która kontroluje właściwości zawarte w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="d1f42-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="d1f42-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1f42-110">Return value</span></span>

<span data-ttu-id="d1f42-111">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d1f42-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d1f42-112">Stała</span><span class="sxs-lookup"><span data-stu-id="d1f42-112">Constant</span></span>  |<span data-ttu-id="d1f42-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="d1f42-113">Value</span></span>  |<span data-ttu-id="d1f42-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d1f42-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d1f42-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d1f42-115">0x80041008</span></span> | <span data-ttu-id="d1f42-116">Kombinacja flag w `lEnumFlags` jest nieprawidłowy lub nieprawidłowy argument został określony.</span><span class="sxs-lookup"><span data-stu-id="d1f42-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="d1f42-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="d1f42-117">0x8004101d</span></span> | <span data-ttu-id="d1f42-118">Drugie wywołanie `BeginEnumeration` został utworzony bez wywołania pośredniczące [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="d1f42-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d1f42-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d1f42-119">0x80041006</span></span> | <span data-ttu-id="d1f42-120">Można rozpocząć nowego wyliczenia jest za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="d1f42-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d1f42-121">0</span><span class="sxs-lookup"><span data-stu-id="d1f42-121">0</span></span> | <span data-ttu-id="d1f42-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d1f42-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d1f42-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1f42-123">Remarks</span></span>

<span data-ttu-id="d1f42-124">Ta funkcja jest zawijana wywołanie [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="d1f42-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="d1f42-125">Flagi, które mogą być przekazywane jako `lEnumFlags` argumentu są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d1f42-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="d1f42-126">Możesz łączyć jedną flagę z każdej grupy z flagą dowolnego z innej grupy.</span><span class="sxs-lookup"><span data-stu-id="d1f42-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="d1f42-127">Jednak flagi z tej samej grupy wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="d1f42-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="d1f42-128">**Grupa 1**</span><span class="sxs-lookup"><span data-stu-id="d1f42-128">**Group 1**</span></span>

|<span data-ttu-id="d1f42-129">Stała</span><span class="sxs-lookup"><span data-stu-id="d1f42-129">Constant</span></span>  |<span data-ttu-id="d1f42-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="d1f42-130">Value</span></span>  |<span data-ttu-id="d1f42-131">Opis</span><span class="sxs-lookup"><span data-stu-id="d1f42-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="d1f42-132">0x4</span><span class="sxs-lookup"><span data-stu-id="d1f42-132">0x4</span></span> | <span data-ttu-id="d1f42-133">Zawierają właściwości, które tworzą tylko klucz.</span><span class="sxs-lookup"><span data-stu-id="d1f42-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="d1f42-134">0x8</span><span class="sxs-lookup"><span data-stu-id="d1f42-134">0x8</span></span> | <span data-ttu-id="d1f42-135">Zawierają właściwości, które są tylko odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="d1f42-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="d1f42-136">**Grupa 2**</span><span class="sxs-lookup"><span data-stu-id="d1f42-136">**Group 2**</span></span>

<span data-ttu-id="d1f42-137">Stała</span><span class="sxs-lookup"><span data-stu-id="d1f42-137">Constant</span></span>  |<span data-ttu-id="d1f42-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="d1f42-138">Value</span></span>  |<span data-ttu-id="d1f42-139">Opis</span><span class="sxs-lookup"><span data-stu-id="d1f42-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="d1f42-140">0x30</span><span class="sxs-lookup"><span data-stu-id="d1f42-140">0x30</span></span> | <span data-ttu-id="d1f42-141">Ogranicz wyliczenie tylko właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="d1f42-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="d1f42-142">0x40</span><span class="sxs-lookup"><span data-stu-id="d1f42-142">0x40</span></span> | <span data-ttu-id="d1f42-143">Dołącz lokalnych i propagowany właściwości, z wyłączeniem właściwości systemu z wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d1f42-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="d1f42-144">Dla klas:</span><span class="sxs-lookup"><span data-stu-id="d1f42-144">For classes:</span></span>

<span data-ttu-id="d1f42-145">Stała</span><span class="sxs-lookup"><span data-stu-id="d1f42-145">Constant</span></span>  |<span data-ttu-id="d1f42-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="d1f42-146">Value</span></span>  |<span data-ttu-id="d1f42-147">Opis</span><span class="sxs-lookup"><span data-stu-id="d1f42-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="d1f42-148">0x100</span><span class="sxs-lookup"><span data-stu-id="d1f42-148">0x100</span></span> | <span data-ttu-id="d1f42-149">Ogranicz wyliczenia właściwości zastąpione w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="d1f42-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="d1f42-150">0x100</span><span class="sxs-lookup"><span data-stu-id="d1f42-150">0x100</span></span> | <span data-ttu-id="d1f42-151">Ogranicz wyliczenia właściwości zastąpione w bieżącej definicji klas i nowe właściwości zdefiniowane w klasie.</span><span class="sxs-lookup"><span data-stu-id="d1f42-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="d1f42-152">0x300</span><span class="sxs-lookup"><span data-stu-id="d1f42-152">0x300</span></span> | <span data-ttu-id="d1f42-153">A zamaskować (zamiast flagę) do zastosowania wobec `lEnumFlags` wartość, aby sprawdzić, czy albo `WBEM_FLAG_CLASS_OVERRIDES_ONLY` lub `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="d1f42-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="d1f42-154">0x10</span><span class="sxs-lookup"><span data-stu-id="d1f42-154">0x10</span></span> | <span data-ttu-id="d1f42-155">Ogranicz wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy.</span><span class="sxs-lookup"><span data-stu-id="d1f42-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="d1f42-156">0x20</span><span class="sxs-lookup"><span data-stu-id="d1f42-156">0x20</span></span> | <span data-ttu-id="d1f42-157">Ogranicz wyliczenia właściwości, które są dziedziczone z klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="d1f42-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="d1f42-158">Dla wystąpień:</span><span class="sxs-lookup"><span data-stu-id="d1f42-158">For instances:</span></span>

<span data-ttu-id="d1f42-159">Stała</span><span class="sxs-lookup"><span data-stu-id="d1f42-159">Constant</span></span>  |<span data-ttu-id="d1f42-160">Wartość</span><span class="sxs-lookup"><span data-stu-id="d1f42-160">Value</span></span>  |<span data-ttu-id="d1f42-161">Opis</span><span class="sxs-lookup"><span data-stu-id="d1f42-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="d1f42-162">0x10</span><span class="sxs-lookup"><span data-stu-id="d1f42-162">0x10</span></span> | <span data-ttu-id="d1f42-163">Ogranicz wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy.</span><span class="sxs-lookup"><span data-stu-id="d1f42-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="d1f42-164">0x20</span><span class="sxs-lookup"><span data-stu-id="d1f42-164">0x20</span></span> | <span data-ttu-id="d1f42-165">Ogranicz wyliczenia właściwości, które są dziedziczone z klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="d1f42-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |


## <a name="requirements"></a><span data-ttu-id="d1f42-166">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1f42-166">Requirements</span></span>  
 <span data-ttu-id="d1f42-167">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1f42-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1f42-168">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d1f42-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d1f42-169">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d1f42-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1f42-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1f42-170">See also</span></span>  
[<span data-ttu-id="d1f42-171">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="d1f42-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
