---
title: BeginEnumeration, funkcja (odwołanie do niezarządzanego interfejsu API)
description: Funkcja BeginEnumeration resetuje wyliczenia do początku wyliczenia
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
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176880"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="38f8b-103">BeingEnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="38f8b-103">BeginEnumeration function</span></span>
<span data-ttu-id="38f8b-104">Resetuje wyliczenia z powrotem do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="38f8b-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="38f8b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="38f8b-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="38f8b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="38f8b-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="38f8b-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="38f8b-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="38f8b-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="38f8b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="38f8b-109">[w] Bitowe połączenie flag lub wartości [opisanych](#remarks) w uwagi sekcji, która kontroluje właściwości zawarte w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="38f8b-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="38f8b-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="38f8b-110">Return value</span></span>

<span data-ttu-id="38f8b-111">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="38f8b-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="38f8b-112">Stały</span><span class="sxs-lookup"><span data-stu-id="38f8b-112">Constant</span></span>  |<span data-ttu-id="38f8b-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="38f8b-113">Value</span></span>  |<span data-ttu-id="38f8b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="38f8b-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="38f8b-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="38f8b-115">0x80041008</span></span> | <span data-ttu-id="38f8b-116">Kombinacja flag `lEnumFlags` jest nieprawidłowa lub określono nieprawidłowy argument.</span><span class="sxs-lookup"><span data-stu-id="38f8b-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="38f8b-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="38f8b-117">0x8004101d</span></span> | <span data-ttu-id="38f8b-118">Drugie wezwanie `BeginEnumeration` zostało wykonane bez interwencji [`EndEnumeration`](endenumeration.md)połączenia do .</span><span class="sxs-lookup"><span data-stu-id="38f8b-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="38f8b-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="38f8b-119">0x80041006</span></span> | <span data-ttu-id="38f8b-120">Za mało pamięci jest dostępna, aby rozpocząć nowe wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="38f8b-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="38f8b-121">0</span><span class="sxs-lookup"><span data-stu-id="38f8b-121">0</span></span> | <span data-ttu-id="38f8b-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="38f8b-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="38f8b-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38f8b-123">Remarks</span></span>

<span data-ttu-id="38f8b-124">Ta funkcja zawija wywołanie metody [IWbemClassObject::BeginEnumeration.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="38f8b-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="38f8b-125">Flagi, które mogą być `lEnumFlags` przekazywane jako argument są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="38f8b-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="38f8b-126">Można połączyć jedną flagę z każdej grupy z dowolną flagą z dowolnej innej grupy.</span><span class="sxs-lookup"><span data-stu-id="38f8b-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="38f8b-127">Jednak flagi z tej samej grupy wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="38f8b-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="38f8b-128">**Grupa 1**</span><span class="sxs-lookup"><span data-stu-id="38f8b-128">**Group 1**</span></span>

|<span data-ttu-id="38f8b-129">Stały</span><span class="sxs-lookup"><span data-stu-id="38f8b-129">Constant</span></span>  |<span data-ttu-id="38f8b-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="38f8b-130">Value</span></span>  |<span data-ttu-id="38f8b-131">Opis</span><span class="sxs-lookup"><span data-stu-id="38f8b-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="38f8b-132">0x4</span><span class="sxs-lookup"><span data-stu-id="38f8b-132">0x4</span></span> | <span data-ttu-id="38f8b-133">Uwzględnij właściwości, które stanowią tylko klucz.</span><span class="sxs-lookup"><span data-stu-id="38f8b-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="38f8b-134">0x8</span><span class="sxs-lookup"><span data-stu-id="38f8b-134">0x8</span></span> | <span data-ttu-id="38f8b-135">Uwzględnij właściwości, które są tylko odwołaniami do obiektów.</span><span class="sxs-lookup"><span data-stu-id="38f8b-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="38f8b-136">**Grupa 2**</span><span class="sxs-lookup"><span data-stu-id="38f8b-136">**Group 2**</span></span>

<span data-ttu-id="38f8b-137">Stały</span><span class="sxs-lookup"><span data-stu-id="38f8b-137">Constant</span></span>  |<span data-ttu-id="38f8b-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="38f8b-138">Value</span></span>  |<span data-ttu-id="38f8b-139">Opis</span><span class="sxs-lookup"><span data-stu-id="38f8b-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="38f8b-140">0x30</span><span class="sxs-lookup"><span data-stu-id="38f8b-140">0x30</span></span> | <span data-ttu-id="38f8b-141">Ogranicz wyliczenie tylko do właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="38f8b-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="38f8b-142">0x40</span><span class="sxs-lookup"><span data-stu-id="38f8b-142">0x40</span></span> | <span data-ttu-id="38f8b-143">Uwzględnij właściwości lokalne i propagowane, ale wyklucz właściwości systemu z wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="38f8b-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="38f8b-144">Dla klas:</span><span class="sxs-lookup"><span data-stu-id="38f8b-144">For classes:</span></span>

<span data-ttu-id="38f8b-145">Stały</span><span class="sxs-lookup"><span data-stu-id="38f8b-145">Constant</span></span>  |<span data-ttu-id="38f8b-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="38f8b-146">Value</span></span>  |<span data-ttu-id="38f8b-147">Opis</span><span class="sxs-lookup"><span data-stu-id="38f8b-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="38f8b-148">0x100</span><span class="sxs-lookup"><span data-stu-id="38f8b-148">0x100</span></span> | <span data-ttu-id="38f8b-149">Ogranicz wyliczenie do właściwości zastąpionych w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="38f8b-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="38f8b-150">0x100</span><span class="sxs-lookup"><span data-stu-id="38f8b-150">0x100</span></span> | <span data-ttu-id="38f8b-151">Ogranicz wyliczenie do właściwości nadpisywać w bieżącej definicji klasy i do nowych właściwości zdefiniowanych w klasie.</span><span class="sxs-lookup"><span data-stu-id="38f8b-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="38f8b-152">0x300</span><span class="sxs-lookup"><span data-stu-id="38f8b-152">0x300</span></span> | <span data-ttu-id="38f8b-153">Maska (a nie flaga), `lEnumFlags` aby zastosować względem `WBEM_FLAG_CLASS_OVERRIDES_ONLY` wartości, aby sprawdzić, czy albo `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="38f8b-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="38f8b-154">0x10</span><span class="sxs-lookup"><span data-stu-id="38f8b-154">0x10</span></span> | <span data-ttu-id="38f8b-155">Ogranicz wyliczenie do właściwości, które są zdefiniowane lub zmodyfikowane w samej klasie.</span><span class="sxs-lookup"><span data-stu-id="38f8b-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="38f8b-156">0x20</span><span class="sxs-lookup"><span data-stu-id="38f8b-156">0x20</span></span> | <span data-ttu-id="38f8b-157">Ogranicz wyliczenie do właściwości, które są dziedziczone z klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="38f8b-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="38f8b-158">W przypadku:</span><span class="sxs-lookup"><span data-stu-id="38f8b-158">For instances:</span></span>

<span data-ttu-id="38f8b-159">Stały</span><span class="sxs-lookup"><span data-stu-id="38f8b-159">Constant</span></span>  |<span data-ttu-id="38f8b-160">Wartość</span><span class="sxs-lookup"><span data-stu-id="38f8b-160">Value</span></span>  |<span data-ttu-id="38f8b-161">Opis</span><span class="sxs-lookup"><span data-stu-id="38f8b-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="38f8b-162">0x10</span><span class="sxs-lookup"><span data-stu-id="38f8b-162">0x10</span></span> | <span data-ttu-id="38f8b-163">Ogranicz wyliczenie do właściwości, które są zdefiniowane lub zmodyfikowane w samej klasie.</span><span class="sxs-lookup"><span data-stu-id="38f8b-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="38f8b-164">0x20</span><span class="sxs-lookup"><span data-stu-id="38f8b-164">0x20</span></span> | <span data-ttu-id="38f8b-165">Ogranicz wyliczenie do właściwości, które są dziedziczone z klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="38f8b-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="38f8b-166">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38f8b-166">Requirements</span></span>  
 <span data-ttu-id="38f8b-167">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38f8b-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38f8b-168">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="38f8b-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="38f8b-169">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="38f8b-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f8b-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38f8b-170">See also</span></span>

- [<span data-ttu-id="38f8b-171">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="38f8b-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
