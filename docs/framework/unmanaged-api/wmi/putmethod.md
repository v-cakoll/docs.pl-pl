---
title: PutMethod — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja PutMethod tworzy metodę.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2b41cbbade9da5c2095309b9039b8ce2758f6f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798365"
---
# <a name="putmethod-function"></a><span data-ttu-id="74231-103">PutMethod, funkcja</span><span class="sxs-lookup"><span data-stu-id="74231-103">PutMethod function</span></span>
<span data-ttu-id="74231-104">Tworzy metodę.</span><span class="sxs-lookup"><span data-stu-id="74231-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="74231-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="74231-105">Syntax</span></span>  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="74231-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="74231-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="74231-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="74231-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="74231-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="74231-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="74231-109">podczas Nazwa metody do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="74231-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="74231-110">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="74231-110">[in] Reserved.</span></span> <span data-ttu-id="74231-111">Ten parametr musi być równy 0.</span><span class="sxs-lookup"><span data-stu-id="74231-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="74231-112">podczas Wskaźnik do kopii [klasy systemowej __Parameters](/windows/desktop/WmiSdk/--parameters) , która zawiera `in` parametry dla metody.</span><span class="sxs-lookup"><span data-stu-id="74231-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="74231-113">Ten parametr jest ignorowany, jeśli `null`jest ustawiony na.</span><span class="sxs-lookup"><span data-stu-id="74231-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="74231-114">podczas  Wskaźnik do kopii [klasy systemowej __Parameters](/windows/desktop/WmiSdk/--parameters) , która zawiera `out` parametry dla metody.</span><span class="sxs-lookup"><span data-stu-id="74231-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="74231-115">Ten parametr jest ignorowany, jeśli `null`jest ustawiony na.</span><span class="sxs-lookup"><span data-stu-id="74231-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="74231-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="74231-116">Return value</span></span>

<span data-ttu-id="74231-117">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="74231-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="74231-118">Stała</span><span class="sxs-lookup"><span data-stu-id="74231-118">Constant</span></span>  |<span data-ttu-id="74231-119">Wartość</span><span class="sxs-lookup"><span data-stu-id="74231-119">Value</span></span>  |<span data-ttu-id="74231-120">Opis</span><span class="sxs-lookup"><span data-stu-id="74231-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="74231-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="74231-121">0x80041008</span></span> | <span data-ttu-id="74231-122">Co najmniej jeden parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="74231-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="74231-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="74231-123">0x80041043</span></span> | <span data-ttu-id="74231-124">Parametr metody określony w obiektach pInSignature i *pOutSignature* ma różne kwalifikatory. `[in, out]`</span><span class="sxs-lookup"><span data-stu-id="74231-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="74231-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="74231-125">0x80041036</span></span> | <span data-ttu-id="74231-126">Parametr metody nie zawiera specyfikacji kwalifikatora **ID** .</span><span class="sxs-lookup"><span data-stu-id="74231-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="74231-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="74231-127">0x80041038</span></span> | <span data-ttu-id="74231-128">Seria identyfikatorów, która jest przypisana do parametrów metody, nie jest powtarzana lub nie zaczyna się od 0.</span><span class="sxs-lookup"><span data-stu-id="74231-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="74231-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="74231-129">0x80041039</span></span> | <span data-ttu-id="74231-130">Wartość zwracana dla metody ma kwalifikator **identyfikatora** .</span><span class="sxs-lookup"><span data-stu-id="74231-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="74231-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="74231-131">0x80041034</span></span> | <span data-ttu-id="74231-132">Podjęto próbę ponownego użycia istniejącej nazwy metody z klasy nadrzędnej i sygnatury są niezgodne.</span><span class="sxs-lookup"><span data-stu-id="74231-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="74231-133">0</span><span class="sxs-lookup"><span data-stu-id="74231-133">0</span></span> | <span data-ttu-id="74231-134">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="74231-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="74231-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74231-135">Remarks</span></span>

<span data-ttu-id="74231-136">Ta funkcja otacza wywołanie metody [IWbemClassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .</span><span class="sxs-lookup"><span data-stu-id="74231-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="74231-137">To wywołanie metody jest obsługiwane tylko wtedy `ptr` , gdy jest definicją klasy CIM.</span><span class="sxs-lookup"><span data-stu-id="74231-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="74231-138">Manipulowanie metodami nie jest dostępne ze wskaźników [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , które wskazują wystąpienia modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="74231-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="74231-139">Użytkownicy nie mogą tworzyć metod o nazwach zaczynających się lub kończących znakiem podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="74231-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="74231-140">Jest to zarezerwowane dla klas systemowych i właściwości.</span><span class="sxs-lookup"><span data-stu-id="74231-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="74231-141">W przypadku metody `in` parametry i `out` są opisane jako właściwości w obiektach [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="74231-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="74231-142">Parametr można zdefiniować przez dodanie tej samej właściwości do obu obiektów wskazywanych `pInSignature` przez parametry i `pOutSignature`. `[in/out]`</span><span class="sxs-lookup"><span data-stu-id="74231-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="74231-143">W takim przypadku właściwości mają tę samą wartość kwalifikatora **ID** .</span><span class="sxs-lookup"><span data-stu-id="74231-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="74231-144">Każda właściwość obiektu klasy [__Parameters](/windows/desktop/WmiSdk/--parameters) innego niż `ReturnValue` musi mieć kwalifikator **identyfikatora** , wartość liczbową zero, która identyfikuje kolejność wyświetlania parametrów.</span><span class="sxs-lookup"><span data-stu-id="74231-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="74231-145">Żadne dwa parametry nie mogą mieć tej samej wartości **identyfikatora** i nie można pominąć wartości **identyfikatora** .</span><span class="sxs-lookup"><span data-stu-id="74231-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="74231-146">Jeśli wystąpi dowolny warunek, `PutMethod` funkcja zwraca. `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`</span><span class="sxs-lookup"><span data-stu-id="74231-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="74231-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="74231-147">Example</span></span>

<span data-ttu-id="74231-148">Aby zapoznać się z przykładem, zobacz [IWbemClassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .</span><span class="sxs-lookup"><span data-stu-id="74231-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="74231-149">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74231-149">Requirements</span></span>  
 <span data-ttu-id="74231-150">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74231-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74231-151">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="74231-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="74231-152">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="74231-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74231-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74231-153">See also</span></span>

- [<span data-ttu-id="74231-154">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="74231-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
