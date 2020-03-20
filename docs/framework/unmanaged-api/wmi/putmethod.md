---
title: Funkcja PutMethod (odwołanie do niezarządzanego interfejsu API)
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
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174917"
---
# <a name="putmethod-function"></a><span data-ttu-id="aef79-103">PutMethod, funkcja</span><span class="sxs-lookup"><span data-stu-id="aef79-103">PutMethod function</span></span>
<span data-ttu-id="aef79-104">Tworzy metodę.</span><span class="sxs-lookup"><span data-stu-id="aef79-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="aef79-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="aef79-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="aef79-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aef79-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="aef79-107">[w] Ten parametr jest nieużywane.</span><span class="sxs-lookup"><span data-stu-id="aef79-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="aef79-108">[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="aef79-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="aef79-109">[w] Nazwa metody do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="aef79-109">[in] The name of the method to create.</span></span>

`lFlags`  
<span data-ttu-id="aef79-110">[w] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="aef79-110">[in] Reserved.</span></span> <span data-ttu-id="aef79-111">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="aef79-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="aef79-112">[w] Wskaźnik do kopii [__Parameters klasy systemowej,](/windows/desktop/WmiSdk/--parameters) która `in` zawiera parametry metody.</span><span class="sxs-lookup"><span data-stu-id="aef79-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="aef79-113">Ten parametr jest ignorowany, jeśli jest ustawiony na `null`.</span><span class="sxs-lookup"><span data-stu-id="aef79-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="aef79-114">[w]  Wskaźnik do kopii [__Parameters klasy systemowej,](/windows/desktop/WmiSdk/--parameters) która `out` zawiera parametry metody.</span><span class="sxs-lookup"><span data-stu-id="aef79-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="aef79-115">Ten parametr jest ignorowany, jeśli jest ustawiony na `null`.</span><span class="sxs-lookup"><span data-stu-id="aef79-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="aef79-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aef79-116">Return value</span></span>

<span data-ttu-id="aef79-117">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="aef79-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="aef79-118">Stały</span><span class="sxs-lookup"><span data-stu-id="aef79-118">Constant</span></span>  |<span data-ttu-id="aef79-119">Wartość</span><span class="sxs-lookup"><span data-stu-id="aef79-119">Value</span></span>  |<span data-ttu-id="aef79-120">Opis</span><span class="sxs-lookup"><span data-stu-id="aef79-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="aef79-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="aef79-121">0x80041008</span></span> | <span data-ttu-id="aef79-122">Co najmniej jeden parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="aef79-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="aef79-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="aef79-123">0x80041043</span></span> | <span data-ttu-id="aef79-124">Parametr `[in, out]` metody określony zarówno w *pInSignature* i *pOutSignature* obiektów mają różne kwalifikatory.</span><span class="sxs-lookup"><span data-stu-id="aef79-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="aef79-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="aef79-125">0x80041036</span></span> | <span data-ttu-id="aef79-126">Brak specyfikacji kwalifikatora **identyfikatora** brakuje parametru metody.</span><span class="sxs-lookup"><span data-stu-id="aef79-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="aef79-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="aef79-127">0x80041038</span></span> | <span data-ttu-id="aef79-128">Seria identyfikatorów, która jest przypisana do parametrów metody nie jest kolejna lub nie zaczyna się od 0.</span><span class="sxs-lookup"><span data-stu-id="aef79-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="aef79-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="aef79-129">0x80041039</span></span> | <span data-ttu-id="aef79-130">Zwracana wartość metody ma kwalifikator **identyfikatora.**</span><span class="sxs-lookup"><span data-stu-id="aef79-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="aef79-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="aef79-131">0x80041034</span></span> | <span data-ttu-id="aef79-132">Podjęto próbę ponownego użycia istniejącej nazwy metody z klasy nadrzędnej, a podpisy nie były zgodne.</span><span class="sxs-lookup"><span data-stu-id="aef79-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="aef79-133">0</span><span class="sxs-lookup"><span data-stu-id="aef79-133">0</span></span> | <span data-ttu-id="aef79-134">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aef79-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="aef79-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aef79-135">Remarks</span></span>

<span data-ttu-id="aef79-136">Ta funkcja zawija wywołanie [metody IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)</span><span class="sxs-lookup"><span data-stu-id="aef79-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="aef79-137">To wywołanie metody jest `ptr` obsługiwane tylko wtedy, gdy jest definicją klasy CIM.</span><span class="sxs-lookup"><span data-stu-id="aef79-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="aef79-138">Manipulacja metodą nie jest dostępna w wskaźnikach [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazujących na wystąpienia cim.</span><span class="sxs-lookup"><span data-stu-id="aef79-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="aef79-139">Użytkownicy nie mogą tworzyć metod o nazwach, które rozpoczynają się lub kończą na podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="aef79-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="aef79-140">Jest to zarezerwowane dla klas systemowych i właściwości.</span><span class="sxs-lookup"><span data-stu-id="aef79-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="aef79-141">Dla metody `in` i `out` parametry są opisane jako właściwości w [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) obiektów.</span><span class="sxs-lookup"><span data-stu-id="aef79-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="aef79-142">Parametr `[in/out]` można zdefiniować, dodając tę samą właściwość `pInSignature` `pOutSignature` do obu obiektów wskazywał przez i parametrów.</span><span class="sxs-lookup"><span data-stu-id="aef79-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="aef79-143">W takim przypadku właściwości mają tę samą wartość kwalifikatora **identyfikatora.**</span><span class="sxs-lookup"><span data-stu-id="aef79-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="aef79-144">Każda właściwość w [obiekcie](/windows/desktop/WmiSdk/--parameters) klasy `ReturnValue` __Parameters innej niż musi mieć kwalifikator **identyfikatora,** wartość liczbową opartą na wartości zerowej, która identyfikuje kolejność, w jakiej pojawiają się parametry.</span><span class="sxs-lookup"><span data-stu-id="aef79-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="aef79-145">Żadne dwa parametry nie mogą mieć tej samej wartości **identyfikatora** i nie można pominąć żadnej wartości **identyfikatora.**</span><span class="sxs-lookup"><span data-stu-id="aef79-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="aef79-146">Jeśli wystąpi którykolwiek `PutMethod` z `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`tych warunków, funkcja zwraca wartość .</span><span class="sxs-lookup"><span data-stu-id="aef79-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="aef79-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="aef79-147">Example</span></span>

<span data-ttu-id="aef79-148">Na przykład zobacz [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="aef79-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="aef79-149">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aef79-149">Requirements</span></span>  
 <span data-ttu-id="aef79-150">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aef79-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aef79-151">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="aef79-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="aef79-152">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aef79-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef79-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aef79-153">See also</span></span>

- [<span data-ttu-id="aef79-154">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="aef79-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
