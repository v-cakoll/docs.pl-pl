---
title: Funkcja PutMethod (niezarządzany wykaz interfejsów API)
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
ms.openlocfilehash: 7f74b0d30a1a8899d3c8d0a2bf0f108ea11165cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="putmethod-function"></a><span data-ttu-id="d3f5b-103">Funkcja PutMethod</span><span class="sxs-lookup"><span data-stu-id="d3f5b-103">PutMethod function</span></span>
<span data-ttu-id="d3f5b-104">Tworzy metodę.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d3f5b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3f5b-105">Syntax</span></span>  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="d3f5b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3f5b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d3f5b-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d3f5b-108">[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="d3f5b-109">[in] Nazwa metody do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="d3f5b-110">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-110">[in] Reserved.</span></span> <span data-ttu-id="d3f5b-111">Ten parametr musi wynosić 0.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="d3f5b-112">[in] Wskaźnik do kopię [klasy systemu __Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) zawierający `in` parametry metody.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-112">[in] A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="d3f5b-113">Ten parametr jest ignorowana, jeśli ustawiono `null`.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="d3f5b-114">[in]  Wskaźnik do kopię [klasy systemu __Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) zawierający `out` parametry metody.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-114">[in]  A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="d3f5b-115">Ten parametr jest ignorowana, jeśli ustawiono `null`.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-115">This parameter is ignored if set to `null`.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="d3f5b-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d3f5b-116">Return value</span></span>

<span data-ttu-id="d3f5b-117">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d3f5b-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d3f5b-118">Stała</span><span class="sxs-lookup"><span data-stu-id="d3f5b-118">Constant</span></span>  |<span data-ttu-id="d3f5b-119">Wartość</span><span class="sxs-lookup"><span data-stu-id="d3f5b-119">Value</span></span>  |<span data-ttu-id="d3f5b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="d3f5b-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d3f5b-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d3f5b-121">0x80041008</span></span> | <span data-ttu-id="d3f5b-122">Jeden lub więcej parametrów nie są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="d3f5b-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="d3f5b-123">0x80041043</span></span> | <span data-ttu-id="d3f5b-124">`[in, out]` Określony zarówno parametr metody *pInSignature* i *pOutSignature* obiekty mają różne kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="d3f5b-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="d3f5b-125">0x80041036</span></span> | <span data-ttu-id="d3f5b-126">Parametr metody jest Brak specyfikacji **identyfikator** kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="d3f5b-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="d3f5b-127">0x80041038</span></span> | <span data-ttu-id="d3f5b-128">Serii identyfikator, która jest przypisana do parametry metody nie jest kolejnych lub nie rozpoczynają się od 0.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="d3f5b-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="d3f5b-129">0x80041039</span></span> | <span data-ttu-id="d3f5b-130">Wartość zwracana dla metody ma **identyfikator** kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="d3f5b-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="d3f5b-131">0x80041034</span></span> | <span data-ttu-id="d3f5b-132">Podjęto próbę ponownego użycia istniejącej nazwy metody z klasy nadrzędnej, a podpisy nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="d3f5b-133">0</span><span class="sxs-lookup"><span data-stu-id="d3f5b-133">0</span></span> | <span data-ttu-id="d3f5b-134">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d3f5b-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3f5b-135">Remarks</span></span>

<span data-ttu-id="d3f5b-136">Ta funkcja jest zawijana wywołanie [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-136">This function wraps a call to the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="d3f5b-137">Wywołanie tej metody jest obsługiwana tylko, jeśli `ptr` jest definicję klasy modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="d3f5b-138">Metoda manipulowania nie jest dostępna z [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) wskaźników, które wskazują wystąpienia modelu CIM.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-138">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) pointers that point to CIM instances.</span></span>

<span data-ttu-id="d3f5b-139">Użytkownicy nie mogą tworzyć metody o nazwach rozpoczynać się ani kończyć się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="d3f5b-140">Jest to zarezerwowana dla systemu klas i właściwości.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="d3f5b-141">W przypadku metody `in` i `out` parametry są opisane jako właściwości [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) obiektów.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objects.</span></span>

<span data-ttu-id="d3f5b-142">`[in/out]` Dodając oba obiekty wskazywanej przez tę samą właściwość można zdefiniować parametr `pInSignature` i `pOutSignature` parametrów.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="d3f5b-143">W takim przypadku udziału takie same właściwości **identyfikator** wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="d3f5b-144">Każdej właściwości w [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) innych niż klasa obiektu `ReturnValue` musi mieć **identyfikator** kwalifikator, wartość liczbową liczony od zera, który określa kolejność wyświetlania parametrów.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-144">Each property in a [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="d3f5b-145">Nie dwa parametry mają takie same **identyfikator** wartość i nie **identyfikator** wartość może być pominięte.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="d3f5b-146">W przypadku obu warunku `PutMethod` funkcja zwraca `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="d3f5b-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3f5b-147">Example</span></span>

<span data-ttu-id="d3f5b-148">Na przykład zobacz [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="d3f5b-148">For an example, see the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d3f5b-149">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3f5b-149">Requirements</span></span>  
 <span data-ttu-id="d3f5b-150">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3f5b-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3f5b-151">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d3f5b-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d3f5b-152">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d3f5b-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f5b-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3f5b-153">See also</span></span>  
[<span data-ttu-id="d3f5b-154">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="d3f5b-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
