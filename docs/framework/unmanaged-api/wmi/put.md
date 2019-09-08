---
title: Put — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja Put przypisuje nową wartość do nazwanej właściwości.
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
ms.openlocfilehash: 5aa629c2d07fb25db035cd80aba3c74413070e6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798400"
---
# <a name="put-function"></a><span data-ttu-id="62d68-103">Put — funkcja</span><span class="sxs-lookup"><span data-stu-id="62d68-103">Put function</span></span>

<span data-ttu-id="62d68-104">Ustawia nazwę właściwości nazwanej na nową wartość.</span><span class="sxs-lookup"><span data-stu-id="62d68-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="62d68-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="62d68-105">Syntax</span></span>

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a><span data-ttu-id="62d68-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="62d68-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="62d68-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="62d68-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="62d68-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="62d68-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="62d68-109">podczas Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="62d68-109">[in] The name of the property.</span></span> <span data-ttu-id="62d68-110">Ten parametr nie może `null`być.</span><span class="sxs-lookup"><span data-stu-id="62d68-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="62d68-111">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="62d68-111">[in] Reserved.</span></span> <span data-ttu-id="62d68-112">Ten parametr musi być równy 0.</span><span class="sxs-lookup"><span data-stu-id="62d68-112">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="62d68-113">podczas Wskaźnik do prawidłowego `VARIANT` , który będzie nową wartością właściwości.</span><span class="sxs-lookup"><span data-stu-id="62d68-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="62d68-114">Jeśli `pVal` jest `null` lub `null`wskazuje `VARIANT` na typ `VT_NULL`, właściwość jest ustawiona na.</span><span class="sxs-lookup"><span data-stu-id="62d68-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span>

`vtType`\
<span data-ttu-id="62d68-115">podczas Typ `VARIANT` wskazywany przez `pVal`.</span><span class="sxs-lookup"><span data-stu-id="62d68-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="62d68-116">Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="62d68-116">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="62d68-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="62d68-117">Return value</span></span>

<span data-ttu-id="62d68-118">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="62d68-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="62d68-119">Stała</span><span class="sxs-lookup"><span data-stu-id="62d68-119">Constant</span></span>  |<span data-ttu-id="62d68-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="62d68-120">Value</span></span>  |<span data-ttu-id="62d68-121">Opis</span><span class="sxs-lookup"><span data-stu-id="62d68-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="62d68-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="62d68-122">0x80041001</span></span> | <span data-ttu-id="62d68-123">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="62d68-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="62d68-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="62d68-124">0x80041008</span></span> | <span data-ttu-id="62d68-125">Co najmniej jeden parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="62d68-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="62d68-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="62d68-126">0x8004102a</span></span> | <span data-ttu-id="62d68-127">Nie rozpoznano typu właściwości.</span><span class="sxs-lookup"><span data-stu-id="62d68-127">The property type is not recognized.</span></span> <span data-ttu-id="62d68-128">Ta wartość jest zwracana podczas tworzenia wystąpień klas, jeśli Klasa już istnieje.</span><span class="sxs-lookup"><span data-stu-id="62d68-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="62d68-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="62d68-129">0x80041006</span></span> | <span data-ttu-id="62d68-130">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="62d68-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="62d68-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="62d68-131">0x80041005</span></span> | <span data-ttu-id="62d68-132">Dla wystąpień: Wskazuje, `pVal` że dla właściwości `VARIANT` wskazuje niewłaściwy typ.</span><span class="sxs-lookup"><span data-stu-id="62d68-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="62d68-133">Definicje klas: Właściwość już istnieje w klasie nadrzędnej, a nowy typ modelu COM różni się od starego typu COM.</span><span class="sxs-lookup"><span data-stu-id="62d68-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="62d68-134">0</span><span class="sxs-lookup"><span data-stu-id="62d68-134">0</span></span> | <span data-ttu-id="62d68-135">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="62d68-135">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="62d68-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62d68-136">Remarks</span></span>

<span data-ttu-id="62d68-137">Ta funkcja otacza wywołanie metody [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .</span><span class="sxs-lookup"><span data-stu-id="62d68-137">This function wraps a call to the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

<span data-ttu-id="62d68-138">Ta funkcja zawsze zastępuje bieżącą wartość właściwości nową.</span><span class="sxs-lookup"><span data-stu-id="62d68-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="62d68-139">Jeśli [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazuje definicję klasy, `Put` tworzy lub aktualizuje wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="62d68-139">If the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="62d68-140">Gdy [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazuje na wystąpienie CIM, `Put` aktualizuje tylko wartość właściwości. `Put` nie można utworzyć wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="62d68-140">When [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="62d68-141">Właściwość `__CLASS` systemowa jest tylko do zapisu podczas tworzenia klasy, gdy nie powinna pozostać pusta.</span><span class="sxs-lookup"><span data-stu-id="62d68-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="62d68-142">Wszystkie inne właściwości systemu są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="62d68-142">All other system properties are read-only.</span></span>

<span data-ttu-id="62d68-143">Użytkownik nie może tworzyć właściwości o nazwach zaczynających się lub kończących znakiem podkreślenia ("_").</span><span class="sxs-lookup"><span data-stu-id="62d68-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="62d68-144">Jest to zarezerwowane dla klas systemowych i właściwości.</span><span class="sxs-lookup"><span data-stu-id="62d68-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="62d68-145">Jeśli właściwość ustawiona przez `Put` funkcję istnieje w klasie nadrzędnej, wartość domyślna właściwości jest zmieniana, chyba że typ właściwości jest niezgodny z typem klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="62d68-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="62d68-146">Jeśli właściwość nie istnieje i nie jest to niezgodność typów, zostanie utworzona właściwość.</span><span class="sxs-lookup"><span data-stu-id="62d68-146">If the property does not exist and it is not a type mismatch, the property is created.</span></span>

<span data-ttu-id="62d68-147">Użyj parametru `vtType` tylko wtedy, gdy tworzysz nowe właściwości w definicji klasy CIM i `pVal` `VARIANT` jest `null` lub wskazuje typ `VT_NULL`.</span><span class="sxs-lookup"><span data-stu-id="62d68-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="62d68-148">W tym przypadku `vType` parametr określa typ CIM właściwości.</span><span class="sxs-lookup"><span data-stu-id="62d68-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="62d68-149">W każdym innym przypadku `vtType` należy mieć wartość 0.</span><span class="sxs-lookup"><span data-stu-id="62d68-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="62d68-150">`vtType`musi również mieć wartość 0, jeśli obiekt źródłowy jest wystąpieniem (nawet `Val` Jeśli `null`jest), ponieważ typ właściwości jest ustalony i nie można go zmienić.</span><span class="sxs-lookup"><span data-stu-id="62d68-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>

## <a name="example"></a><span data-ttu-id="62d68-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="62d68-151">Example</span></span>

<span data-ttu-id="62d68-152">Aby zapoznać się z przykładem, zobacz [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .</span><span class="sxs-lookup"><span data-stu-id="62d68-152">For an example, see the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="62d68-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62d68-153">Requirements</span></span>

<span data-ttu-id="62d68-154">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62d68-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="62d68-155">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="62d68-155">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="62d68-156">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="62d68-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="62d68-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62d68-157">See also</span></span>

- [<span data-ttu-id="62d68-158">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="62d68-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
