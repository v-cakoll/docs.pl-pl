---
title: Funkcja QualifierSet_BeginEnumeration (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_BeginEnumeration resetuje moduł wyliczający kwalifikatory obiektu.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d20701237501834c611c4e498c39597cf275176
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518689"
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="e9176-103">QualifierSet_BeginEnumeration — funkcja</span><span class="sxs-lookup"><span data-stu-id="e9176-103">QualifierSet_BeginEnumeration function</span></span>
<span data-ttu-id="e9176-104">Resetuje moduł wyliczający kwalifikatory obiektu na początku tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e9176-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e9176-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9176-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="e9176-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9176-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="e9176-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="e9176-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="e9176-108">[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e9176-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="e9176-109">[in] Bitowa kombinacja wartości opisanych w lub flag [uwagi](#remarks) sekcja, która określa kwalifikatory do uwzględnienia w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="e9176-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="e9176-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e9176-110">Return value</span></span>

<span data-ttu-id="e9176-111">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="e9176-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e9176-112">Stała</span><span class="sxs-lookup"><span data-stu-id="e9176-112">Constant</span></span>  |<span data-ttu-id="e9176-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="e9176-113">Value</span></span>  |<span data-ttu-id="e9176-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e9176-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e9176-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e9176-115">0x80041008</span></span> | <span data-ttu-id="e9176-116">`lFlags` Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e9176-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="e9176-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="e9176-117">0x8004101d</span></span> | <span data-ttu-id="e9176-118">Drugie wywołanie `QualifierSet_BeginEnumeration` został utworzony bez interwencyjnego wywołania [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e9176-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e9176-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e9176-119">0x80041006</span></span> | <span data-ttu-id="e9176-120">Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="e9176-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e9176-121">0</span><span class="sxs-lookup"><span data-stu-id="e9176-121">0</span></span> | <span data-ttu-id="e9176-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e9176-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e9176-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9176-123">Remarks</span></span>

<span data-ttu-id="e9176-124">Ta funkcja zawija wywołanie do [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) metody.</span><span class="sxs-lookup"><span data-stu-id="e9176-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="e9176-125">Wyliczono wszystkie kwalifikatory dla obiektu, ta metoda musi zostać wywołana przed pierwszym wywołaniu [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="e9176-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="e9176-126">Kolejność, w którym są wyliczane kwalifikatory może być inwariantny dla danego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e9176-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="e9176-127">Flagi, które mogą być przekazywane jako `lEnumFlags` argument są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e9176-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>   

|<span data-ttu-id="e9176-128">Stała</span><span class="sxs-lookup"><span data-stu-id="e9176-128">Constant</span></span>  |<span data-ttu-id="e9176-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="e9176-129">Value</span></span>  |<span data-ttu-id="e9176-130">Opis</span><span class="sxs-lookup"><span data-stu-id="e9176-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="e9176-131">0</span><span class="sxs-lookup"><span data-stu-id="e9176-131">0</span></span> | <span data-ttu-id="e9176-132">Zwraca nazwy wszystkich kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="e9176-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="e9176-133">0x10</span><span class="sxs-lookup"><span data-stu-id="e9176-133">0x10</span></span> | <span data-ttu-id="e9176-134">Zwróć tylko nazwy kwalifikatory określonych do bieżącej właściwości lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="e9176-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="e9176-135">Dla właściwości: zwracać tylko kwalifikatory określonych właściwości (w tym zastąpień), a nie te kwalifikatory propagowane z poziomu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="e9176-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="e9176-136">W przypadku wystąpienia: zwracać tylko nazwy kwalifikator danego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e9176-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="e9176-137">Dla klasy: przywrócenie tylko kwalifikatory określonych beiong klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e9176-137">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="e9176-138">0x20</span><span class="sxs-lookup"><span data-stu-id="e9176-138">0x20</span></span> | <span data-ttu-id="e9176-139">Zwróć tylko nazwy kwalifikatory propagowane z innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e9176-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="e9176-140">Dla właściwości: Zwróć tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="e9176-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="e9176-141">W przypadku wystąpienia: zwrócenia tylko tych kwalifikatory propagowane z poziomu definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="e9176-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="e9176-142">Dla klasy: zwrócenia tylko nazwy kwalifikator dziedziczone z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e9176-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="e9176-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9176-143">Requirements</span></span>  
 <span data-ttu-id="e9176-144">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9176-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9176-145">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e9176-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e9176-146">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e9176-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9176-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9176-147">See also</span></span>  
[<span data-ttu-id="e9176-148">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="e9176-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
