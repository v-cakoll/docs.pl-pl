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
ms.openlocfilehash: 0ca510f30f0f38ae54eb83046b0e9d5541db882d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758689"
---
# <a name="putmethod-function"></a><span data-ttu-id="abce4-103">PutMethod — funkcja</span><span class="sxs-lookup"><span data-stu-id="abce4-103">PutMethod function</span></span>
<span data-ttu-id="abce4-104">Tworzy metodę.</span><span class="sxs-lookup"><span data-stu-id="abce4-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="abce4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="abce4-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="abce4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="abce4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="abce4-107">[in] Ten parametr jest nieużywany.</span><span class="sxs-lookup"><span data-stu-id="abce4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="abce4-108">[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="abce4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="abce4-109">[in] Nazwa metody do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="abce4-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="abce4-110">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="abce4-110">[in] Reserved.</span></span> <span data-ttu-id="abce4-111">Ten parametr musi być 0.</span><span class="sxs-lookup"><span data-stu-id="abce4-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="abce4-112">[in] Wskaźnik do kopię [klasy systemu __Parameters](/windows/desktop/WmiSdk/--parameters) zawierający `in` parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="abce4-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="abce4-113">Ten parametr jest ignorowany, jeśli ustawiono `null`.</span><span class="sxs-lookup"><span data-stu-id="abce4-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="abce4-114">[in]  Wskaźnik do kopię [klasy systemu __Parameters](/windows/desktop/WmiSdk/--parameters) zawierający `out` parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="abce4-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="abce4-115">Ten parametr jest ignorowany, jeśli ustawiono `null`.</span><span class="sxs-lookup"><span data-stu-id="abce4-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="abce4-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="abce4-116">Return value</span></span>

<span data-ttu-id="abce4-117">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="abce4-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="abce4-118">Stała</span><span class="sxs-lookup"><span data-stu-id="abce4-118">Constant</span></span>  |<span data-ttu-id="abce4-119">Wartość</span><span class="sxs-lookup"><span data-stu-id="abce4-119">Value</span></span>  |<span data-ttu-id="abce4-120">Opis</span><span class="sxs-lookup"><span data-stu-id="abce4-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="abce4-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="abce4-121">0x80041008</span></span> | <span data-ttu-id="abce4-122">Jeden lub więcej parametrów są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="abce4-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="abce4-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="abce4-123">0x80041043</span></span> | <span data-ttu-id="abce4-124">`[in, out]` Parametru metody, określona w obu *pInSignature* i *pOutSignature* obiekty mają różne kwalifikatorów.</span><span class="sxs-lookup"><span data-stu-id="abce4-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="abce4-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="abce4-125">0x80041036</span></span> | <span data-ttu-id="abce4-126">Parametr metody brakuje specyfikacji **identyfikator** kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="abce4-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="abce4-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="abce4-127">0x80041038</span></span> | <span data-ttu-id="abce4-128">Serii identyfikator, która jest przypisana do parametrów metody nie jest kolejnych lub nie rozpoczyna się od 0.</span><span class="sxs-lookup"><span data-stu-id="abce4-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="abce4-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="abce4-129">0x80041039</span></span> | <span data-ttu-id="abce4-130">Wartość zwracana dla metody ma **identyfikator** kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="abce4-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="abce4-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="abce4-131">0x80041034</span></span> | <span data-ttu-id="abce4-132">Nastąpiła próba ponownego użycia istniejącej nazwy metody z klasy nadrzędnej, a podpisy jest niezgodny.</span><span class="sxs-lookup"><span data-stu-id="abce4-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="abce4-133">0</span><span class="sxs-lookup"><span data-stu-id="abce4-133">0</span></span> | <span data-ttu-id="abce4-134">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="abce4-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="abce4-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abce4-135">Remarks</span></span>

<span data-ttu-id="abce4-136">Ta funkcja zawija wywołanie do [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="abce4-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="abce4-137">Wywołanie tej metody jest obsługiwana tylko wtedy, gdy `ptr` jest definicją klasy modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="abce4-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="abce4-138">Metoda manipulowania nie jest dostępna z [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźniki prowadzące do wystąpienia modelu CIM.</span><span class="sxs-lookup"><span data-stu-id="abce4-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="abce4-139">Użytkownicy nie mogą tworzyć metody z nazwami będącymi zaczynać się ani kończyć znakiem podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="abce4-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="abce4-140">Jest on zarezerwowany dla klas systemowych i właściwości.</span><span class="sxs-lookup"><span data-stu-id="abce4-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="abce4-141">Dla metody `in` i `out` parametry są określane jako właściwości w [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) obiektów.</span><span class="sxs-lookup"><span data-stu-id="abce4-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="abce4-142">`[in/out]` Można zdefiniować, dodając tę samą właściwość do obu obiektów wskazywany przez parametr `pInSignature` i `pOutSignature` parametrów.</span><span class="sxs-lookup"><span data-stu-id="abce4-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="abce4-143">W tym przypadku właściwości współużytkować ten sam **identyfikator** wartość kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="abce4-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="abce4-144">Każdej właściwości w [__Parameters](/windows/desktop/WmiSdk/--parameters) klasy obiektów innych niż `ReturnValue` musi mieć **identyfikator** kwalifikator, zaczynający się od zera wartość liczbowa, która określa kolejność, w jakiej są wyświetlane parametry.</span><span class="sxs-lookup"><span data-stu-id="abce4-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="abce4-145">Nie dwa parametry można mieć taką samą **identyfikator** wartości i nie **identyfikator** wartość może zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="abce4-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="abce4-146">W przypadku obu warunku `PutMethod` funkcja zwraca `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="abce4-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="abce4-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="abce4-147">Example</span></span>

<span data-ttu-id="abce4-148">Aby uzyskać przykład, zobacz [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="abce4-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="abce4-149">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abce4-149">Requirements</span></span>  
 <span data-ttu-id="abce4-150">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abce4-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abce4-151">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="abce4-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="abce4-152">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="abce4-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abce4-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abce4-153">See also</span></span>

- [<span data-ttu-id="abce4-154">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="abce4-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
