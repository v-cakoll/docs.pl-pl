---
title: Funkcja umieszczania (niezarządzany wykaz interfejsów API)
description: Funkcję Put przypisuje nową wartość o nazwie właściwości.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ec8fe889885b555cbf9a95cd34b7330efff27f2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518759"
---
# <a name="put-function"></a><span data-ttu-id="e7fc4-103">Umieść — funkcja</span><span class="sxs-lookup"><span data-stu-id="e7fc4-103">Put function</span></span>
<span data-ttu-id="e7fc4-104">Ustawia właściwość o nazwie na nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e7fc4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7fc4-105">Syntax</span></span>  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a><span data-ttu-id="e7fc4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7fc4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e7fc4-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e7fc4-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="e7fc4-109">[in] Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-109">[in] The name of the property.</span></span> <span data-ttu-id="e7fc4-110">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-110">This parameter cannot be `null`.</span></span>

`lFlags`  
<span data-ttu-id="e7fc4-111">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-111">[in] Reserved.</span></span> <span data-ttu-id="e7fc4-112">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-112">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="e7fc4-113">[in] Wskaźnik do prawidłowego `VARIANT` stanie się nowa wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="e7fc4-114">Jeśli `pVal` jest `null` lub wskazuje na `VARIANT` typu `VT_NULL`, zostaje ustalona `null`.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span> 

`vtType`  
<span data-ttu-id="e7fc4-115">[in] Typ `VARIANT` wskazywany przez `pVal`.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="e7fc4-116">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-116">See the [Remarks](#remarks) section for more information.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="e7fc4-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e7fc4-117">Return value</span></span>

<span data-ttu-id="e7fc4-118">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="e7fc4-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e7fc4-119">Stała</span><span class="sxs-lookup"><span data-stu-id="e7fc4-119">Constant</span></span>  |<span data-ttu-id="e7fc4-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="e7fc4-120">Value</span></span>  |<span data-ttu-id="e7fc4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="e7fc4-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e7fc4-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e7fc4-122">0x80041001</span></span> | <span data-ttu-id="e7fc4-123">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e7fc4-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e7fc4-124">0x80041008</span></span> | <span data-ttu-id="e7fc4-125">Jeden lub więcej parametrów są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="e7fc4-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="e7fc4-126">0x8004102a</span></span> | <span data-ttu-id="e7fc4-127">Nie rozpoznano typu właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-127">The property type is not recognized.</span></span> <span data-ttu-id="e7fc4-128">Ta wartość jest zwracana podczas tworzenia wystąpienia klasy, jeśli klasa już istnieje.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e7fc4-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e7fc4-129">0x80041006</span></span> | <span data-ttu-id="e7fc4-130">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="e7fc4-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="e7fc4-131">0x80041005</span></span> | <span data-ttu-id="e7fc4-132">Dla wystąpień: oznacza, że `pVal` wskazuje `VARIANT` nieprawidłowego typu właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="e7fc4-133">Aby uzyskać definicje klas: właściwość już istnieje w klasie nadrzędnej, a nowy typ COM jest inny niż stary typ COM.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e7fc4-134">0</span><span class="sxs-lookup"><span data-stu-id="e7fc4-134">0</span></span> | <span data-ttu-id="e7fc4-135">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-135">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="e7fc4-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7fc4-136">Remarks</span></span>

<span data-ttu-id="e7fc4-137">Ta funkcja zawija wywołanie do [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) metody.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-137">This function wraps a call to the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

<span data-ttu-id="e7fc4-138">Ta funkcja zawsze zastępuje bieżącą wartość właściwości nowej.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="e7fc4-139">Jeśli [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) punkty na definicję klasy `Put` tworzy lub aktualizuje wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-139">If the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="e7fc4-140">Gdy [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazuje na wystąpienie CIM `Put` aktualizuje wartości właściwości. `Put` nie można utworzyć wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-140">When [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="e7fc4-141">`__CLASS` System właściwość jest tylko zapisu podczas tworzenia klasy, gdy go nie może pozostać puste.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="e7fc4-142">Wszystkie pozostałe właściwości systemu są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-142">All other system properties are read-only.</span></span>

<span data-ttu-id="e7fc4-143">Użytkownik nie można utworzyć właściwości z nazwami będącymi rozpoczynać się ani kończyć znakiem podkreślenia ("_").</span><span class="sxs-lookup"><span data-stu-id="e7fc4-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="e7fc4-144">Jest on zarezerwowany dla klas systemowych i właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="e7fc4-145">Jeśli właściwość jest ustawiona `Put` istnieje funkcja w klasie nadrzędnej, wartość domyślna właściwości zostanie zmieniona, chyba że typ właściwości jest niezgodny z typem klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="e7fc4-146">Jeśli właściwość nie istnieje, nie jest niezgodność typu właściwości jest ceated.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-146">If the property does not exist and it is not a type mismatch, the property is ceated.</span></span>

<span data-ttu-id="e7fc4-147">Użyj `vtType` parametru tylko podczas tworzenia nowych właściwości w definicji klasy modelu wspólnych informacji i `pVal` jest `null` lub wskazuje na `VARIANT` typu `VT_NULL`.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="e7fc4-148">W tym przypadku `vType` parametr określa typ CIM właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="e7fc4-149">W każdym przypadku `vtType` musi mieć wartość 0.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="e7fc4-150">`vtType` musi również być na 0, jeśli obiekt źródłowy jest wystąpieniem (nawet jeśli `Val` jest `null`), ponieważ typ właściwości jest stała i nie można jej zmienić.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>   

## <a name="example"></a><span data-ttu-id="e7fc4-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7fc4-151">Example</span></span>

<span data-ttu-id="e7fc4-152">Aby uzyskać przykład, zobacz [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) metody.</span><span class="sxs-lookup"><span data-stu-id="e7fc4-152">For an example, see the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7fc4-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7fc4-153">Requirements</span></span>  
 <span data-ttu-id="e7fc4-154">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7fc4-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7fc4-155">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e7fc4-155">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e7fc4-156">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e7fc4-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7fc4-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7fc4-157">See also</span></span>  
[<span data-ttu-id="e7fc4-158">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="e7fc4-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
