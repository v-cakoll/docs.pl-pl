---
title: Funkcja QualifierSet_Next (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_Next pobiera następny kwalifikatora w wyliczeniu.
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
ms.openlocfilehash: 35ab5b64b3c7e364e0dd11c002b87a0a413f4335
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532438"
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="2358c-103">QualifierSet_Next — funkcja</span><span class="sxs-lookup"><span data-stu-id="2358c-103">QualifierSet_Next function</span></span>
<span data-ttu-id="2358c-104">Pobiera następny kwalifikatora w wyliczeniu, który uruchamiany przy użyciu wywołania do [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="2358c-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2358c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2358c-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="2358c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2358c-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="2358c-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="2358c-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="2358c-108">[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2358c-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="2358c-109">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="2358c-109">[in] Reserved.</span></span> <span data-ttu-id="2358c-110">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="2358c-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="2358c-111">[out] Nazwa kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="2358c-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="2358c-112">Jeśli `null`, ten parametr jest ignorowane; w przeciwnym razie `pstrName` nie powinien wskazywać do prawidłowego `BSTR` lub występuje przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="2358c-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="2358c-113">Jeśli nie ma wartości null, funkcja zawsze przydziela nową `BSTR` zwróceniem `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="2358c-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="2358c-114">[out] Jeśli operacja się powiedzie, wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="2358c-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="2358c-115">Jeśli funkcja zawiedzie, `VARIANT` wskazywany przez `pVal` nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="2358c-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="2358c-116">Jeśli ten parametr jest `null`, parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="2358c-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="2358c-117">[out] Wskaźnik na wartość typu LONG, który odbiera wersja kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="2358c-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="2358c-118">Jeśli informacje o wersji nie jest wymagana, ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="2358c-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="2358c-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2358c-119">Return value</span></span>

<span data-ttu-id="2358c-120">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="2358c-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2358c-121">Stała</span><span class="sxs-lookup"><span data-stu-id="2358c-121">Constant</span></span>  |<span data-ttu-id="2358c-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="2358c-122">Value</span></span>  |<span data-ttu-id="2358c-123">Opis</span><span class="sxs-lookup"><span data-stu-id="2358c-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2358c-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2358c-124">0x80041008</span></span> | <span data-ttu-id="2358c-125">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2358c-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="2358c-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="2358c-126">0x8004101d</span></span> | <span data-ttu-id="2358c-127">Obiekt wywołujący nie wywołał [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2358c-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2358c-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2358c-128">0x80041006</span></span> | <span data-ttu-id="2358c-129">Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="2358c-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="2358c-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="2358c-130">0x40005</span></span> | <span data-ttu-id="2358c-131">Nie więcej kwalifikatorów są pozostawiane w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="2358c-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2358c-132">0</span><span class="sxs-lookup"><span data-stu-id="2358c-132">0</span></span> | <span data-ttu-id="2358c-133">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2358c-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2358c-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2358c-134">Remarks</span></span>

<span data-ttu-id="2358c-135">Ta funkcja zawija wywołanie do [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) metody.</span><span class="sxs-lookup"><span data-stu-id="2358c-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="2358c-136">Należy wywołać `QualifierSet_Next` funkcja wielokrotnie wyliczyć wszystkie kwalifikatory aż zwrot funkcji `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="2358c-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="2358c-137">Aby zakończyć wyliczenia wcześnie, należy wywołać [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="2358c-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="2358c-138">Kolejność kwalifikatory zwrócony podczas wyliczania jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="2358c-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="2358c-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2358c-139">Requirements</span></span>  
 <span data-ttu-id="2358c-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2358c-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2358c-141">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2358c-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2358c-142">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2358c-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2358c-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2358c-143">See also</span></span>
- [<span data-ttu-id="2358c-144">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="2358c-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
