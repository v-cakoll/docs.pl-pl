---
title: "Funkcja PutClassWmi (niezarządzany wykaz interfejsów API)"
description: "Funkcja PutClassWmi tworzy nową klasę lub aktualizuje istniejący zestaw."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutClassWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutClassWmi
helpviewer_keywords: PutClassWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 219cec2096cd3d1dfe1e0d3c0903b62692e444e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="putclasswmi-function"></a><span data-ttu-id="456da-103">Funkcja PutClassWmi</span><span class="sxs-lookup"><span data-stu-id="456da-103">PutClassWmi function</span></span>
<span data-ttu-id="456da-104">Tworzy nową klasę lub aktualizuje istniejący zestaw.</span><span class="sxs-lookup"><span data-stu-id="456da-104">Creates a new class or updates an existing one.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="456da-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="456da-105">Syntax</span></span>  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="456da-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="456da-106">Parameters</span></span>

`pObject`    
<span data-ttu-id="456da-107">[in] Wskaźnik do prawidłową definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="456da-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="456da-108">Go muszą zostać poprawnie zainicjowane ze wszystkich wartości właściwości wymaganych.</span><span class="sxs-lookup"><span data-stu-id="456da-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`   
<span data-ttu-id="456da-109">[in] Kombinacja flag, które wpływają na działanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="456da-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="456da-110">Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="456da-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="456da-111">Stała</span><span class="sxs-lookup"><span data-stu-id="456da-111">Constant</span></span>  |<span data-ttu-id="456da-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="456da-112">Value</span></span>  |<span data-ttu-id="456da-113">Opis</span><span class="sxs-lookup"><span data-stu-id="456da-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="456da-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="456da-114">0x20000</span></span> | <span data-ttu-id="456da-115">Jeśli zestaw, WMI nie przechowuje żadnych kwalifikatorów ze zmianami podtyp.</span><span class="sxs-lookup"><span data-stu-id="456da-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> </br> <span data-ttu-id="456da-116">Jeśli nie zestawu, zakłada się, że ten obiekt nie jest lokalizowany, a wszystkie kwalifikatory są storedwith tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="456da-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="456da-117">0</span><span class="sxs-lookup"><span data-stu-id="456da-117">0</span></span> | <span data-ttu-id="456da-118">Jeśli nie istnieje lub jego zastąpienie, jeśli już istnieje, należy utworzyć klasę.</span><span class="sxs-lookup"><span data-stu-id="456da-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="456da-119">1</span><span class="sxs-lookup"><span data-stu-id="456da-119">1</span></span> | <span data-ttu-id="456da-120">Aktualizacja klasy.</span><span class="sxs-lookup"><span data-stu-id="456da-120">Update the class.</span></span> <span data-ttu-id="456da-121">Klasa musi istnieć wywołanie powiódł się.</span><span class="sxs-lookup"><span data-stu-id="456da-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="456da-122">2</span><span class="sxs-lookup"><span data-stu-id="456da-122">2</span></span> | <span data-ttu-id="456da-123">Tworzenie klasy.</span><span class="sxs-lookup"><span data-stu-id="456da-123">Create the class.</span></span> <span data-ttu-id="456da-124">Połączenie nie powiedzie się, jeśli klasa już istnieje.</span><span class="sxs-lookup"><span data-stu-id="456da-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="456da-125">0x10</span><span class="sxs-lookup"><span data-stu-id="456da-125">0x10</span></span> | <span data-ttu-id="456da-126">Flaga powoduje Półsynchroniczne wywołania.</span><span class="sxs-lookup"><span data-stu-id="456da-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="456da-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="456da-127">0x10000</span></span> | <span data-ttu-id="456da-128">Wypychania dostawcy należy określić tę flagę podczas wywoływania metody `PutClassWmi` aby wskazać, że ta klasa została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="456da-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="456da-129">0</span><span class="sxs-lookup"><span data-stu-id="456da-129">0</span></span> | <span data-ttu-id="456da-130">Umożliwia klasy aktualizacji, jeśli istnieją żadne klasy pochodnej i żadnych wystąpień tej klasy.</span><span class="sxs-lookup"><span data-stu-id="456da-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="456da-131">Umożliwia także aktualizacje we wszystkich przypadkach, jeśli zmiana dotyczy tylko kwalifikatory bez znaczenia, takie jak kwalifikator opisu.</span><span class="sxs-lookup"><span data-stu-id="456da-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="456da-132">Jeśli są wystąpienia klasy lub zmiany są ważne kwalifikatory, aktualizacja nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="456da-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="456da-133">0x20</span><span class="sxs-lookup"><span data-stu-id="456da-133">0x20</span></span> | <span data-ttu-id="456da-134">Umożliwia aktualizowanie klas, nawet jeśli są klasy podrzędne tak długo, jak zmiana nie powoduje konfliktów z klasy podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="456da-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="456da-135">Ta flaga umożliwia na przykład nową właściwość ma zostać dodana do klasy podstawowej, który nie został wcześniej wymienione w żadnej z klas podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="456da-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="456da-136">Jeśli są wystąpienia klasy aktualizacji nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="456da-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="456da-137">0x40</span><span class="sxs-lookup"><span data-stu-id="456da-137">0x40</span></span> | <span data-ttu-id="456da-138">Wymusza aktualizacje klas, gdy klasy podrzędne powodujące konflikt.</span><span class="sxs-lookup"><span data-stu-id="456da-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="456da-139">Na przykład ta flaga wymusza aktualizację, jeśli kwalifikator klasa jest zdefiniowana w klasie podrzędnej, a klasa podstawowa próbuje dodać ten sam kwalifikator, który powoduje konflikt z jedną istniejących danych.</span><span class="sxs-lookup"><span data-stu-id="456da-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with thte existing one.</span></span> <span data-ttu-id="456da-140">W trybie wymuszania tis konflikt został rozwiązany przez usunięcie powodujące konflikt kwalifikator klasy podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="456da-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`  
<span data-ttu-id="456da-141">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="456da-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="456da-142">W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy.</span><span class="sxs-lookup"><span data-stu-id="456da-142">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="456da-143">[out] Jeśli `null`, ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="456da-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="456da-144">Jeśli `lFlags` zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja zwraca bezpośrednio z `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="456da-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="456da-145">`ppCallResult` Parametru otrzymuje wskaźnik do nowego [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) obiektu.</span><span class="sxs-lookup"><span data-stu-id="456da-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="456da-146">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="456da-146">Return value</span></span>

<span data-ttu-id="456da-147">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="456da-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="456da-148">Stała</span><span class="sxs-lookup"><span data-stu-id="456da-148">Constant</span></span>  |<span data-ttu-id="456da-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="456da-149">Value</span></span>  |<span data-ttu-id="456da-150">Opis</span><span class="sxs-lookup"><span data-stu-id="456da-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="456da-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="456da-151">0x80041003</span></span> | <span data-ttu-id="456da-152">Użytkownik nie ma uprawnień do tworzenia lub modyfikowania klasy.</span><span class="sxs-lookup"><span data-stu-id="456da-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="456da-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="456da-153">0x80041001</span></span> | <span data-ttu-id="456da-154">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="456da-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="456da-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="456da-155">0x80041010</span></span> | <span data-ttu-id="456da-156">Określona klasa jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="456da-156">The specified class is not valid.</span></span> <span data-ttu-id="456da-157">Oznacza to, że zwykle `pObject` określa wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="456da-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="456da-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="456da-158">0x80041008</span></span> | <span data-ttu-id="456da-159">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="456da-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="456da-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="456da-160">0x80041016</span></span> | <span data-ttu-id="456da-161">Nazwa określona klasa jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="456da-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="456da-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="456da-162">0x80041025</span></span> | <span data-ttu-id="456da-163">Podjęto próbę dokonania zmiany, która będzie unieważnia podklasę.</span><span class="sxs-lookup"><span data-stu-id="456da-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="456da-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="456da-164">0x80041019</span></span> | <span data-ttu-id="456da-165">`WBEM_FLAG_CREATE_ONLY` Określono flagę, ale klasa już istnieje.</span><span class="sxs-lookup"><span data-stu-id="456da-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="456da-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="456da-166">0x80041002</span></span> | <span data-ttu-id="456da-167">`WBEM_FLAG_UPDATE_ONLY`został określony w `lFlags`, a nie znaleziono klasy.</span><span class="sxs-lookup"><span data-stu-id="456da-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="456da-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="456da-168">0x80041020</span></span> | <span data-ttu-id="456da-169">Wymagane właściwości dla klasy nie zostały ustawione.</span><span class="sxs-lookup"><span data-stu-id="456da-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="456da-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="456da-170">0x80041006</span></span> | <span data-ttu-id="456da-171">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="456da-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="456da-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="456da-172">0x80041033</span></span> | <span data-ttu-id="456da-173">Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="456da-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="456da-174">Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="456da-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="456da-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="456da-175">0x80041015</span></span> | <span data-ttu-id="456da-176">Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="456da-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="456da-177">0</span><span class="sxs-lookup"><span data-stu-id="456da-177">0</span></span> | <span data-ttu-id="456da-178">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="456da-178">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="456da-179">Uwagi</span><span class="sxs-lookup"><span data-stu-id="456da-179">Remarks</span></span>

<span data-ttu-id="456da-180">Ta funkcja jest zawijana wywołanie [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="456da-180">This function wraps a call to the [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="456da-181">Użytkownik nie może utworzyć klasy o nazwach zaczynać się ani kończyć chacater podkreślenia</span><span class="sxs-lookup"><span data-stu-id="456da-181">The user may not create classes with names that begin or end with an underscore chacater</span></span>

<span data-ttu-id="456da-182">Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="456da-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="456da-183">Wymagania</span><span class="sxs-lookup"><span data-stu-id="456da-183">Requirements</span></span>  
 <span data-ttu-id="456da-184">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="456da-184">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="456da-185">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="456da-185">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="456da-186">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="456da-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="456da-187">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="456da-187">See also</span></span>  
[<span data-ttu-id="456da-188">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="456da-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
