---
title: "Funkcja QualifierSet_GetNames (niezarządzany wykaz interfejsów API)"
description: "Funkcja QualifierSet_GetNames pobiera nazwy kwalifikatory z obiektu lub właściwości."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6077b448c2644f68d12679cf208ee921c2af119a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="4ade2-103">Funkcja QualifierSet_GetNames</span><span class="sxs-lookup"><span data-stu-id="4ade2-103">QualifierSet_GetNames function</span></span>
<span data-ttu-id="4ade2-104">Pobiera nazwy wszystkich kwalifikatorów lub niektórych kwalifikatorów, które są dostępne z bieżącego obiektu lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ade2-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4ade2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ade2-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="4ade2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ade2-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="4ade2-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="4ade2-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="4ade2-108">[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4ade2-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="4ade2-109">[in] Jeden z następujących flag lub wartości, które określa nazwy, w których do uwzględnienia w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="4ade2-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="4ade2-110">Stała</span><span class="sxs-lookup"><span data-stu-id="4ade2-110">Constant</span></span>  |<span data-ttu-id="4ade2-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="4ade2-111">Value</span></span>  |<span data-ttu-id="4ade2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4ade2-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="4ade2-113">0</span><span class="sxs-lookup"><span data-stu-id="4ade2-113">0</span></span> | <span data-ttu-id="4ade2-114">Zwraca nazwy wszystkich kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="4ade2-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="4ade2-115">0x10</span><span class="sxs-lookup"><span data-stu-id="4ade2-115">0x10</span></span> | <span data-ttu-id="4ade2-116">Zwraca tylko nazwy kwalifikatory określonych bieżącą właściwość lub obiekt.</span><span class="sxs-lookup"><span data-stu-id="4ade2-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="4ade2-117">Dla właściwości: zwracać tylko kwalifikatory określonego we właściwości (w tym zastąpień), a nie te kwalifikatory propagowane z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="4ade2-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="4ade2-118">Dla wystąpienia obiektu: zwraca tylko nazwy kwalifikator danego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4ade2-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="4ade2-119">Dla klasy: przywrócenie tylko kwalifikatory określonych beiong klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="4ade2-119">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="4ade2-120">0x20</span><span class="sxs-lookup"><span data-stu-id="4ade2-120">0x20</span></span> | <span data-ttu-id="4ade2-121">Powrót propagowane tylko nazwy kwalifikatory z innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4ade2-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="4ade2-122">Dla właściwości: zwracane tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ade2-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="4ade2-123">Dla wystąpienia obiektu: Powrót propagowane tylko tych kwalifikatory z definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="4ade2-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="4ade2-124">Dla klasy: zwracane tylko nazwy kwalifikator odziedziczona z klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="4ade2-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

<span data-ttu-id="4ade2-125">`pstrNames`[out] Nowy `SAFEARRAY` zawierający żądanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4ade2-125">`pstrNames` [out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="4ade2-126">Tablica może mieć elementów 0.</span><span class="sxs-lookup"><span data-stu-id="4ade2-126">The array can have 0 elements.</span></span> <span data-ttu-id="4ade2-127">Jeśli wystąpi błąd, nowy `SAFEARRAY` nie są zwracane.</span><span class="sxs-lookup"><span data-stu-id="4ade2-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="4ade2-128">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4ade2-128">Return value</span></span>

<span data-ttu-id="4ade2-129">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="4ade2-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4ade2-130">Stała</span><span class="sxs-lookup"><span data-stu-id="4ade2-130">Constant</span></span>  |<span data-ttu-id="4ade2-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="4ade2-131">Value</span></span>  |<span data-ttu-id="4ade2-132">Opis</span><span class="sxs-lookup"><span data-stu-id="4ade2-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4ade2-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4ade2-133">0x80041008</span></span> | <span data-ttu-id="4ade2-134">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="4ade2-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4ade2-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4ade2-135">0x80041006</span></span> | <span data-ttu-id="4ade2-136">Można rozpocząć nowego wyliczenia jest za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="4ade2-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4ade2-137">0</span><span class="sxs-lookup"><span data-stu-id="4ade2-137">0</span></span> | <span data-ttu-id="4ade2-138">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4ade2-138">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4ade2-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ade2-139">Remarks</span></span>

<span data-ttu-id="4ade2-140">Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="4ade2-140">This function wraps a call to the [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="4ade2-141">Gdy po pobraniu Kwalifikator nazwy każdego kwalifikator będzie dostępny według nazwy przez wywołanie metody [QualifierSet_Get](qualifierset-get.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ade2-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span> 

<span data-ttu-id="4ade2-142">Nie jest błąd dla danego obiektu mieć zerowej kwalifikatory tak liczba parametrów w `pstrNames` przy powrocie może mieć wartość 0, mimo że funkcja zwraca `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="4ade2-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="4ade2-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ade2-143">Requirements</span></span>  
 <span data-ttu-id="4ade2-144">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ade2-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ade2-145">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4ade2-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4ade2-146">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4ade2-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ade2-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ade2-147">See also</span></span>  
[<span data-ttu-id="4ade2-148">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="4ade2-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
