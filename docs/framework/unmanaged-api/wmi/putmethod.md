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
ms.openlocfilehash: 1d409507de593cf198fe87340eece6820eaefc63
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127333"
---
# <a name="putmethod-function"></a><span data-ttu-id="e3f9e-103">PutMethod, funkcja</span><span class="sxs-lookup"><span data-stu-id="e3f9e-103">PutMethod function</span></span>
<span data-ttu-id="e3f9e-104">Tworzy metodę.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e3f9e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3f9e-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="e3f9e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3f9e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e3f9e-107">podczas Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e3f9e-108">podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="e3f9e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="e3f9e-109">podczas Nazwa metody do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="e3f9e-110">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-110">[in] Reserved.</span></span> <span data-ttu-id="e3f9e-111">Ten parametr musi być równy 0.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="e3f9e-112">podczas Wskaźnik do kopii [klasy systemowej __Parameters](/windows/desktop/WmiSdk/--parameters) , która zawiera `in` parametry dla metody.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="e3f9e-113">Ten parametr jest ignorowany, jeśli jest ustawiony na `null`.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="e3f9e-114">podczas  Wskaźnik do kopii [klasy systemowej __Parameters](/windows/desktop/WmiSdk/--parameters) , która zawiera `out` parametry dla metody.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="e3f9e-115">Ten parametr jest ignorowany, jeśli jest ustawiony na `null`.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="e3f9e-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3f9e-116">Return value</span></span>

<span data-ttu-id="e3f9e-117">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="e3f9e-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e3f9e-118">Stała</span><span class="sxs-lookup"><span data-stu-id="e3f9e-118">Constant</span></span>  |<span data-ttu-id="e3f9e-119">Wartość</span><span class="sxs-lookup"><span data-stu-id="e3f9e-119">Value</span></span>  |<span data-ttu-id="e3f9e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e3f9e-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e3f9e-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e3f9e-121">0x80041008</span></span> | <span data-ttu-id="e3f9e-122">Co najmniej jeden parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="e3f9e-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="e3f9e-123">0x80041043</span></span> | <span data-ttu-id="e3f9e-124">`[in, out]` parametr metody określony w obiektach *pInSignature* i *pOutSignature* ma różne kwalifikatory.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="e3f9e-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="e3f9e-125">0x80041036</span></span> | <span data-ttu-id="e3f9e-126">Parametr metody nie zawiera specyfikacji kwalifikatora **ID** .</span><span class="sxs-lookup"><span data-stu-id="e3f9e-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="e3f9e-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="e3f9e-127">0x80041038</span></span> | <span data-ttu-id="e3f9e-128">Seria identyfikatorów, która jest przypisana do parametrów metody, nie jest powtarzana lub nie zaczyna się od 0.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="e3f9e-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="e3f9e-129">0x80041039</span></span> | <span data-ttu-id="e3f9e-130">Wartość zwracana dla metody ma kwalifikator **identyfikatora** .</span><span class="sxs-lookup"><span data-stu-id="e3f9e-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="e3f9e-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="e3f9e-131">0x80041034</span></span> | <span data-ttu-id="e3f9e-132">Podjęto próbę ponownego użycia istniejącej nazwy metody z klasy nadrzędnej i sygnatury są niezgodne.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="e3f9e-133">0</span><span class="sxs-lookup"><span data-stu-id="e3f9e-133">0</span></span> | <span data-ttu-id="e3f9e-134">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="e3f9e-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3f9e-135">Remarks</span></span>

<span data-ttu-id="e3f9e-136">Ta funkcja otacza wywołanie metody [IWbemClassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .</span><span class="sxs-lookup"><span data-stu-id="e3f9e-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="e3f9e-137">To wywołanie metody jest obsługiwane tylko wtedy, gdy `ptr` jest definicją klasy CIM.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="e3f9e-138">Manipulowanie metodami nie jest dostępne ze wskaźników [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , które wskazują wystąpienia modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="e3f9e-139">Użytkownicy nie mogą tworzyć metod o nazwach zaczynających się lub kończących znakiem podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="e3f9e-140">Jest to zarezerwowane dla klas systemowych i właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="e3f9e-141">Dla metody `in` i `out` parametry są opisane jako właściwości w [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) obiektów.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="e3f9e-142">Parametr `[in/out]` można zdefiniować przez dodanie tej samej właściwości do obu obiektów wskazywanych przez `pInSignature` i `pOutSignature` parametrów.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="e3f9e-143">W takim przypadku właściwości mają tę samą wartość kwalifikatora **ID** .</span><span class="sxs-lookup"><span data-stu-id="e3f9e-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="e3f9e-144">Każda właściwość obiektu klasy [__Parameters](/windows/desktop/WmiSdk/--parameters) innego niż `ReturnValue` musi mieć kwalifikator **identyfikatora** , wartość liczbową zero, która identyfikuje kolejność wyświetlania parametrów.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="e3f9e-145">Żadne dwa parametry nie mogą mieć tej samej wartości **identyfikatora** i nie można pominąć wartości **identyfikatora** .</span><span class="sxs-lookup"><span data-stu-id="e3f9e-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="e3f9e-146">Jeśli wystąpi dowolny warunek, funkcja `PutMethod` zwraca `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="e3f9e-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="e3f9e-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3f9e-147">Example</span></span>

<span data-ttu-id="e3f9e-148">Aby zapoznać się z przykładem, zobacz [IWbemClassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .</span><span class="sxs-lookup"><span data-stu-id="e3f9e-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3f9e-149">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3f9e-149">Requirements</span></span>  
 <span data-ttu-id="e3f9e-150">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3f9e-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3f9e-151">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="e3f9e-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e3f9e-152">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e3f9e-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3f9e-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3f9e-153">See also</span></span>

- [<span data-ttu-id="e3f9e-154">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="e3f9e-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
