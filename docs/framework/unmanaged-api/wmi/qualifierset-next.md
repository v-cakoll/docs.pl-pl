---
title: Funkcja QualifierSet_Next (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_Next pobiera kwalifikator dalej w wyliczeniu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8232691c697c51b5a480a68c6d952f294a63460
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460230"
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="9055a-103">Funkcja QualifierSet_Next</span><span class="sxs-lookup"><span data-stu-id="9055a-103">QualifierSet_Next function</span></span>
<span data-ttu-id="9055a-104">Pobiera kwalifikator dalej w wyliczeniu, który uruchomił się wywołaniem do [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="9055a-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9055a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9055a-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="9055a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9055a-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="9055a-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="9055a-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="9055a-108">[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9055a-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="9055a-109">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="9055a-109">[in] Reserved.</span></span> <span data-ttu-id="9055a-110">Ten parametr musi wynosić 0.</span><span class="sxs-lookup"><span data-stu-id="9055a-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="9055a-111">[out] Nazwa kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="9055a-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="9055a-112">Jeśli `null`, ten parametr jest ignorowana, a w przeciwnym razie `pstrName` nie powinny wskazywać na prawidłową `BSTR` lub występuje przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="9055a-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="9055a-113">Jeśli nie jest wartość null, funkcja zawsze przydziela nowy `BSTR` po zwraca `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="9055a-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="9055a-114">[out] Gdy to się powiedzie, wartość kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="9055a-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="9055a-115">W przypadku niepowodzenia funkcji `VARIANT` wskazywana przez `pVal` nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="9055a-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="9055a-116">Jeśli ten parametr ma `null`, parametr będzie ignorowany.</span><span class="sxs-lookup"><span data-stu-id="9055a-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="9055a-117">[out] Wskaźnik do LONG, który odbiera podtyp kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="9055a-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="9055a-118">Jeśli informacje o wersji nie jest wymagana, ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="9055a-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="9055a-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9055a-119">Return value</span></span>

<span data-ttu-id="9055a-120">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="9055a-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9055a-121">Stała</span><span class="sxs-lookup"><span data-stu-id="9055a-121">Constant</span></span>  |<span data-ttu-id="9055a-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="9055a-122">Value</span></span>  |<span data-ttu-id="9055a-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9055a-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9055a-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9055a-124">0x80041008</span></span> | <span data-ttu-id="9055a-125">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="9055a-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="9055a-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="9055a-126">0x8004101d</span></span> | <span data-ttu-id="9055a-127">Obiekt wywołujący nie wywołał [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="9055a-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9055a-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9055a-128">0x80041006</span></span> | <span data-ttu-id="9055a-129">Można rozpocząć nowego wyliczenia jest za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="9055a-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="9055a-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="9055a-130">0x40005</span></span> | <span data-ttu-id="9055a-131">Nie więcej kwalifikatory są pozostawiane w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="9055a-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9055a-132">0</span><span class="sxs-lookup"><span data-stu-id="9055a-132">0</span></span> | <span data-ttu-id="9055a-133">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9055a-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9055a-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9055a-134">Remarks</span></span>

<span data-ttu-id="9055a-135">Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="9055a-135">This function wraps a call to the [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="9055a-136">Należy wywołać `QualifierSet_Next` funkcja wielokrotnie wyliczyć wszystkie kwalifikatory do zwrot funkcji `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="9055a-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="9055a-137">Zakończenie wczesne wyliczenia, wywołaj [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="9055a-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="9055a-138">Kolejność kwalifikatory zwrócony podczas wykonywania wyliczenia jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="9055a-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="9055a-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9055a-139">Requirements</span></span>  
 <span data-ttu-id="9055a-140">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9055a-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9055a-141">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9055a-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9055a-142">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9055a-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9055a-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9055a-143">See also</span></span>  
[<span data-ttu-id="9055a-144">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="9055a-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
