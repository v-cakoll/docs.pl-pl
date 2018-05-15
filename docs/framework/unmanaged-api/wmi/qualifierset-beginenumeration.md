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
ms.openlocfilehash: 1fac897f743ca452c38282143cdf822b682df1df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="618df-103">Funkcja QualifierSet_BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="618df-103">QualifierSet_BeginEnumeration function</span></span>
<span data-ttu-id="618df-104">Resetuje moduł wyliczający kwalifikatory obiekt na początek wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="618df-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="618df-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="618df-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="618df-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="618df-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="618df-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="618df-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="618df-108">[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="618df-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="618df-109">[in] Bitowe połączenie flagi lub wartości opisanych w [uwagi](#remarks) sekcja, która określa kwalifikatory do uwzględnienia w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="618df-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="618df-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="618df-110">Return value</span></span>

<span data-ttu-id="618df-111">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="618df-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="618df-112">Stała</span><span class="sxs-lookup"><span data-stu-id="618df-112">Constant</span></span>  |<span data-ttu-id="618df-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="618df-113">Value</span></span>  |<span data-ttu-id="618df-114">Opis</span><span class="sxs-lookup"><span data-stu-id="618df-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="618df-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="618df-115">0x80041008</span></span> | <span data-ttu-id="618df-116">`lFlags` Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="618df-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="618df-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="618df-117">0x8004101d</span></span> | <span data-ttu-id="618df-118">Drugie wywołanie `QualifierSet_BeginEnumeration` został utworzony bez wywołania pośredniczące [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="618df-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="618df-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="618df-119">0x80041006</span></span> | <span data-ttu-id="618df-120">Można rozpocząć nowego wyliczenia jest za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="618df-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="618df-121">0</span><span class="sxs-lookup"><span data-stu-id="618df-121">0</span></span> | <span data-ttu-id="618df-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="618df-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="618df-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="618df-123">Remarks</span></span>

<span data-ttu-id="618df-124">Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="618df-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="618df-125">Aby wyliczyć wszystkie kwalifikatory dla obiekt, ta metoda musi zostać wywołana przed pierwsze wywołanie w celu [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="618df-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="618df-126">Kolejność, w którym są wyliczane kwalifikatory gwarantuje to niezmiennej danego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="618df-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="618df-127">Flagi, które mogą być przekazywane jako `lEnumFlags` argumentu są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="618df-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>   

|<span data-ttu-id="618df-128">Stała</span><span class="sxs-lookup"><span data-stu-id="618df-128">Constant</span></span>  |<span data-ttu-id="618df-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="618df-129">Value</span></span>  |<span data-ttu-id="618df-130">Opis</span><span class="sxs-lookup"><span data-stu-id="618df-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="618df-131">0</span><span class="sxs-lookup"><span data-stu-id="618df-131">0</span></span> | <span data-ttu-id="618df-132">Zwraca nazwy wszystkich kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="618df-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="618df-133">0x10</span><span class="sxs-lookup"><span data-stu-id="618df-133">0x10</span></span> | <span data-ttu-id="618df-134">Zwraca tylko nazwy kwalifikatory określonych bieżącą właściwość lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="618df-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="618df-135">Dla właściwości: zwracać tylko kwalifikatory określonego we właściwości (w tym zastąpień), a nie te kwalifikatory propagowane z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="618df-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="618df-136">Dla wystąpienia obiektu: zwraca tylko nazwy kwalifikator danego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="618df-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="618df-137">Dla klasy: przywrócenie tylko kwalifikatory określonych beiong klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="618df-137">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="618df-138">0x20</span><span class="sxs-lookup"><span data-stu-id="618df-138">0x20</span></span> | <span data-ttu-id="618df-139">Powrót propagowane tylko nazwy kwalifikatory z innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="618df-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="618df-140">Dla właściwości: zwracane tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="618df-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="618df-141">Dla wystąpienia obiektu: Powrót propagowane tylko tych kwalifikatory z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="618df-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="618df-142">Dla klasy: zwracane tylko nazwy kwalifikator odziedziczona z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="618df-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="618df-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="618df-143">Requirements</span></span>  
 <span data-ttu-id="618df-144">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="618df-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="618df-145">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="618df-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="618df-146">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="618df-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="618df-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="618df-147">See also</span></span>  
[<span data-ttu-id="618df-148">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="618df-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
