---
title: Beingenumeration — funkcja (niezarządzana dokumentacja interfejsu API)
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
ms.openlocfilehash: de36650aa2b206b5e9734b38c6067a3a79de610c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798792"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="a2466-103">BeingEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="a2466-103">BeginEnumeration function</span></span>
<span data-ttu-id="a2466-104">Resetuje moduł wyliczający z powrotem do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a2466-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a2466-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2466-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="a2466-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2466-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="a2466-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="a2466-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="a2466-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="a2466-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="a2466-109">podczas Bitowa kombinacja flag lub wartości opisanych w sekcji [uwagi](#remarks) , która kontroluje właściwości zawarte w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="a2466-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a2466-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a2466-110">Return value</span></span>

<span data-ttu-id="a2466-111">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="a2466-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a2466-112">Stała</span><span class="sxs-lookup"><span data-stu-id="a2466-112">Constant</span></span>  |<span data-ttu-id="a2466-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="a2466-113">Value</span></span>  |<span data-ttu-id="a2466-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a2466-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a2466-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a2466-115">0x80041008</span></span> | <span data-ttu-id="a2466-116">Kombinacja flag w `lEnumFlags` jest nieprawidłowa lub określono nieprawidłowy argument.</span><span class="sxs-lookup"><span data-stu-id="a2466-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="a2466-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="a2466-117">0x8004101d</span></span> | <span data-ttu-id="a2466-118">Drugie wywołanie `BeginEnumeration` zostało wykonane bez wywołania wywołującego do [`EndEnumeration`](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a2466-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a2466-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a2466-119">0x80041006</span></span> | <span data-ttu-id="a2466-120">Za mało dostępnej pamięci, aby rozpocząć nowe Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="a2466-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a2466-121">0</span><span class="sxs-lookup"><span data-stu-id="a2466-121">0</span></span> | <span data-ttu-id="a2466-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a2466-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a2466-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2466-123">Remarks</span></span>

<span data-ttu-id="a2466-124">Ta funkcja otacza wywołanie metody [IWbemClassObject:: beingenumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="a2466-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="a2466-125">Flagi, które mogą być przesyłane jako `lEnumFlags` argument, są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a2466-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="a2466-126">Można połączyć jedną flagę z każdej grupy z dowolną flagą z dowolnej innej grupy.</span><span class="sxs-lookup"><span data-stu-id="a2466-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="a2466-127">Jednak flagi z tej samej grupy wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="a2466-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="a2466-128">**Grupa 1**</span><span class="sxs-lookup"><span data-stu-id="a2466-128">**Group 1**</span></span>

|<span data-ttu-id="a2466-129">Stała</span><span class="sxs-lookup"><span data-stu-id="a2466-129">Constant</span></span>  |<span data-ttu-id="a2466-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="a2466-130">Value</span></span>  |<span data-ttu-id="a2466-131">Opis</span><span class="sxs-lookup"><span data-stu-id="a2466-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="a2466-132">0x4</span><span class="sxs-lookup"><span data-stu-id="a2466-132">0x4</span></span> | <span data-ttu-id="a2466-133">Uwzględnij właściwości, które stanowią tylko klucz.</span><span class="sxs-lookup"><span data-stu-id="a2466-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="a2466-134">0x8</span><span class="sxs-lookup"><span data-stu-id="a2466-134">0x8</span></span> | <span data-ttu-id="a2466-135">Dołącz właściwości, które są tylko odwołaniami do obiektów.</span><span class="sxs-lookup"><span data-stu-id="a2466-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="a2466-136">**Grupa 2**</span><span class="sxs-lookup"><span data-stu-id="a2466-136">**Group 2**</span></span>

<span data-ttu-id="a2466-137">Stała</span><span class="sxs-lookup"><span data-stu-id="a2466-137">Constant</span></span>  |<span data-ttu-id="a2466-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="a2466-138">Value</span></span>  |<span data-ttu-id="a2466-139">Opis</span><span class="sxs-lookup"><span data-stu-id="a2466-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="a2466-140">0x30</span><span class="sxs-lookup"><span data-stu-id="a2466-140">0x30</span></span> | <span data-ttu-id="a2466-141">Ogranicz wyliczanie wyłącznie do właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="a2466-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="a2466-142">0x40</span><span class="sxs-lookup"><span data-stu-id="a2466-142">0x40</span></span> | <span data-ttu-id="a2466-143">Uwzględnij właściwości lokalne i propagowane, ale Wyklucz właściwości systemu z wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a2466-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="a2466-144">Dla klas:</span><span class="sxs-lookup"><span data-stu-id="a2466-144">For classes:</span></span>

<span data-ttu-id="a2466-145">Stała</span><span class="sxs-lookup"><span data-stu-id="a2466-145">Constant</span></span>  |<span data-ttu-id="a2466-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="a2466-146">Value</span></span>  |<span data-ttu-id="a2466-147">Opis</span><span class="sxs-lookup"><span data-stu-id="a2466-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="a2466-148">0x100</span><span class="sxs-lookup"><span data-stu-id="a2466-148">0x100</span></span> | <span data-ttu-id="a2466-149">Ogranicz Wyliczenie do właściwości zastąpionych w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="a2466-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="a2466-150">0x100</span><span class="sxs-lookup"><span data-stu-id="a2466-150">0x100</span></span> | <span data-ttu-id="a2466-151">Ogranicz Wyliczenie do właściwości, które zostały zastąpione w bieżącej definicji klasy, i nowe właściwości zdefiniowane w klasie.</span><span class="sxs-lookup"><span data-stu-id="a2466-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="a2466-152">0x300</span><span class="sxs-lookup"><span data-stu-id="a2466-152">0x300</span></span> | <span data-ttu-id="a2466-153">Maska (zamiast flagi) do zastosowania względem `lEnumFlags` wartości, aby sprawdzić `WBEM_FLAG_CLASS_OVERRIDES_ONLY` , czy jest ustawiona albo lub `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` .</span><span class="sxs-lookup"><span data-stu-id="a2466-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="a2466-154">0x10</span><span class="sxs-lookup"><span data-stu-id="a2466-154">0x10</span></span> | <span data-ttu-id="a2466-155">Ogranicz Wyliczenie do właściwości, które są zdefiniowane lub modyfikowane w samej klasie.</span><span class="sxs-lookup"><span data-stu-id="a2466-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="a2466-156">0x20</span><span class="sxs-lookup"><span data-stu-id="a2466-156">0x20</span></span> | <span data-ttu-id="a2466-157">Ogranicz Wyliczenie do właściwości, które są dziedziczone z klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="a2466-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="a2466-158">Dla wystąpień:</span><span class="sxs-lookup"><span data-stu-id="a2466-158">For instances:</span></span>

<span data-ttu-id="a2466-159">Stała</span><span class="sxs-lookup"><span data-stu-id="a2466-159">Constant</span></span>  |<span data-ttu-id="a2466-160">Wartość</span><span class="sxs-lookup"><span data-stu-id="a2466-160">Value</span></span>  |<span data-ttu-id="a2466-161">Opis</span><span class="sxs-lookup"><span data-stu-id="a2466-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="a2466-162">0x10</span><span class="sxs-lookup"><span data-stu-id="a2466-162">0x10</span></span> | <span data-ttu-id="a2466-163">Ogranicz Wyliczenie do właściwości, które są zdefiniowane lub modyfikowane w samej klasie.</span><span class="sxs-lookup"><span data-stu-id="a2466-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="a2466-164">0x20</span><span class="sxs-lookup"><span data-stu-id="a2466-164">0x20</span></span> | <span data-ttu-id="a2466-165">Ogranicz Wyliczenie do właściwości, które są dziedziczone z klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="a2466-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a2466-166">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2466-166">Requirements</span></span>  
 <span data-ttu-id="a2466-167">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2466-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2466-168">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a2466-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a2466-169">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a2466-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2466-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2466-170">See also</span></span>

- [<span data-ttu-id="a2466-171">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="a2466-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
