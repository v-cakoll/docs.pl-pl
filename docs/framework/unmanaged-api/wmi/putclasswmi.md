---
title: Funkcja PutClassWmi (niezarządzany wykaz interfejsów API)
description: Funkcja PutClassWmi tworzy nową klasę lub aktualizuje istniejący zestaw.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de08662a825a84f19a40863cf73481d89364ebd0
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046561"
---
# <a name="putclasswmi-function"></a><span data-ttu-id="1db52-103">PutClassWmi — funkcja</span><span class="sxs-lookup"><span data-stu-id="1db52-103">PutClassWmi function</span></span>
<span data-ttu-id="1db52-104">Tworzy nową klasę lub aktualizuje istniejący zestaw.</span><span class="sxs-lookup"><span data-stu-id="1db52-104">Creates a new class or updates an existing one.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1db52-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1db52-105">Syntax</span></span>  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="1db52-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1db52-106">Parameters</span></span>

`pObject`    
<span data-ttu-id="1db52-107">[in] Wskaźnik do prawidłową definicją klasy.</span><span class="sxs-lookup"><span data-stu-id="1db52-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="1db52-108">Jego musi być prawidłowo zainicjowany przy użyciu wartości wymaganej właściwości.</span><span class="sxs-lookup"><span data-stu-id="1db52-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`   
<span data-ttu-id="1db52-109">[in] Kombinacja flag, które mają wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="1db52-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="1db52-110">Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="1db52-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="1db52-111">Stała</span><span class="sxs-lookup"><span data-stu-id="1db52-111">Constant</span></span>  |<span data-ttu-id="1db52-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="1db52-112">Value</span></span>  |<span data-ttu-id="1db52-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1db52-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="1db52-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="1db52-114">0x20000</span></span> | <span data-ttu-id="1db52-115">Jeśli zestaw, usługa WMI nie przechowuje żadnych kwalifikatorów zmienionych wersji.</span><span class="sxs-lookup"><span data-stu-id="1db52-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> </br> <span data-ttu-id="1db52-116">W przeciwnym razie zestawu, zakłada się, że ten obiekt nie jest zlokalizowana, a wszystkie kwalifikatory są storedwith tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1db52-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="1db52-117">0</span><span class="sxs-lookup"><span data-stu-id="1db52-117">0</span></span> | <span data-ttu-id="1db52-118">Jeśli nie istnieje, lub go zastąpić, jeśli już istnieje, należy utworzyć klasę.</span><span class="sxs-lookup"><span data-stu-id="1db52-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="1db52-119">1</span><span class="sxs-lookup"><span data-stu-id="1db52-119">1</span></span> | <span data-ttu-id="1db52-120">Aktualizacja klasy.</span><span class="sxs-lookup"><span data-stu-id="1db52-120">Update the class.</span></span> <span data-ttu-id="1db52-121">Klasa musi istnieć przez wywołanie zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1db52-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="1db52-122">2</span><span class="sxs-lookup"><span data-stu-id="1db52-122">2</span></span> | <span data-ttu-id="1db52-123">Utwórz klasę.</span><span class="sxs-lookup"><span data-stu-id="1db52-123">Create the class.</span></span> <span data-ttu-id="1db52-124">Wywołanie zakończy się niepowodzeniem, jeśli klasa już istnieje.</span><span class="sxs-lookup"><span data-stu-id="1db52-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="1db52-125">0x10</span><span class="sxs-lookup"><span data-stu-id="1db52-125">0x10</span></span> | <span data-ttu-id="1db52-126">Flaga powoduje, że wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="1db52-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="1db52-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="1db52-127">0x10000</span></span> | <span data-ttu-id="1db52-128">Dostawców wypychania należy określić tę flagę podczas wywoływania `PutClassWmi` do wskazania, że ta klasa została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="1db52-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="1db52-129">0</span><span class="sxs-lookup"><span data-stu-id="1db52-129">0</span></span> | <span data-ttu-id="1db52-130">Umożliwia klasy do zaktualizowania, jeśli istnieją nie klasy pochodne oraz żadnych wystąpień tej klasy.</span><span class="sxs-lookup"><span data-stu-id="1db52-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="1db52-131">Umożliwia także aktualizacje we wszystkich przypadkach, jeśli ta zmiana jest tylko do "nieważne" kwalifikatorów, takich jak kwalifikator opisu.</span><span class="sxs-lookup"><span data-stu-id="1db52-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="1db52-132">Jeśli są wystąpienia klasy lub zmiany mają ważne kwalifikatorów, aktualizacja nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="1db52-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="1db52-133">0x20</span><span class="sxs-lookup"><span data-stu-id="1db52-133">0x20</span></span> | <span data-ttu-id="1db52-134">Umożliwia aktualizowanie klas, nawet jeśli występują podrzędnego klasy tak długo, jak zmiany nie powoduje konfliktów z klasy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="1db52-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="1db52-135">Ta flaga umożliwia na przykład nową właściwość do dodania do klasy bazowej, która nie została wcześniej wymienione w dowolnej klasy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="1db52-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="1db52-136">Jeśli klasa ma wystąpień, aktualizacja nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="1db52-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="1db52-137">0x40</span><span class="sxs-lookup"><span data-stu-id="1db52-137">0x40</span></span> | <span data-ttu-id="1db52-138">Wymusza aktualizowanie klas, gdy klasy podrzędne powodujące konflikt.</span><span class="sxs-lookup"><span data-stu-id="1db52-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="1db52-139">Na przykład ta flaga wymusza aktualizację, jeśli kwalifikator klasa jest zdefiniowana w klasie podrzędnej, a klasa bazowa próbuje dodać ten sam kwalifikator, który powoduje konflikt z jedną istniejących danych.</span><span class="sxs-lookup"><span data-stu-id="1db52-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with thte existing one.</span></span> <span data-ttu-id="1db52-140">W trybie wymuszania tym konflikt został rozwiązany przez usunięcie powodujące konflikt kwalifikator klasy podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="1db52-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`  
<span data-ttu-id="1db52-141">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="1db52-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="1db52-142">W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy.</span><span class="sxs-lookup"><span data-stu-id="1db52-142">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="1db52-143">[out] Jeśli `null`, ten parametr jest nieużywana.</span><span class="sxs-lookup"><span data-stu-id="1db52-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="1db52-144">Jeśli `lFlags` zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja zwraca natychmiast za pomocą `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="1db52-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="1db52-145">`ppCallResult` Parametru otrzymuje wskaźnik do nowego [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) obiektu.</span><span class="sxs-lookup"><span data-stu-id="1db52-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="1db52-146">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1db52-146">Return value</span></span>

<span data-ttu-id="1db52-147">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="1db52-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1db52-148">Stała</span><span class="sxs-lookup"><span data-stu-id="1db52-148">Constant</span></span>  |<span data-ttu-id="1db52-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="1db52-149">Value</span></span>  |<span data-ttu-id="1db52-150">Opis</span><span class="sxs-lookup"><span data-stu-id="1db52-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="1db52-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="1db52-151">0x80041003</span></span> | <span data-ttu-id="1db52-152">Użytkownik nie ma uprawnień do utworzenia lub zmodyfikowania klasy.</span><span class="sxs-lookup"><span data-stu-id="1db52-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="1db52-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="1db52-153">0x80041001</span></span> | <span data-ttu-id="1db52-154">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="1db52-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="1db52-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="1db52-155">0x80041010</span></span> | <span data-ttu-id="1db52-156">Określona klasa jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="1db52-156">The specified class is not valid.</span></span> <span data-ttu-id="1db52-157">Oznacza to, że zwykle `pObject` określa obiektu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1db52-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1db52-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1db52-158">0x80041008</span></span> | <span data-ttu-id="1db52-159">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="1db52-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="1db52-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="1db52-160">0x80041016</span></span> | <span data-ttu-id="1db52-161">Nazwa określona klasa jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="1db52-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="1db52-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="1db52-162">0x80041025</span></span> | <span data-ttu-id="1db52-163">Podjęto próbę dokonania zmiany, który będzie unieważnia podklasę.</span><span class="sxs-lookup"><span data-stu-id="1db52-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="1db52-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="1db52-164">0x80041019</span></span> | <span data-ttu-id="1db52-165">`WBEM_FLAG_CREATE_ONLY` Określono flagę, ale klasa już istnieje.</span><span class="sxs-lookup"><span data-stu-id="1db52-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="1db52-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="1db52-166">0x80041002</span></span> | <span data-ttu-id="1db52-167">`WBEM_FLAG_UPDATE_ONLY` został określony w `lFlags`, i nie można odnaleźć klasy.</span><span class="sxs-lookup"><span data-stu-id="1db52-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="1db52-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="1db52-168">0x80041020</span></span> | <span data-ttu-id="1db52-169">Wymagane właściwości dla klasy nie wszystkie zostały ustawione.</span><span class="sxs-lookup"><span data-stu-id="1db52-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1db52-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1db52-170">0x80041006</span></span> | <span data-ttu-id="1db52-171">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="1db52-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="1db52-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="1db52-172">0x80041033</span></span> | <span data-ttu-id="1db52-173">WMI został prawdopodobnie zatrzymane i ponowne uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="1db52-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="1db52-174">Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="1db52-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="1db52-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="1db52-175">0x80041015</span></span> | <span data-ttu-id="1db52-176">Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="1db52-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="1db52-177">0</span><span class="sxs-lookup"><span data-stu-id="1db52-177">0</span></span> | <span data-ttu-id="1db52-178">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1db52-178">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1db52-179">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1db52-179">Remarks</span></span>

<span data-ttu-id="1db52-180">Ta funkcja zawija wywołanie do [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) metody.</span><span class="sxs-lookup"><span data-stu-id="1db52-180">This function wraps a call to the [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) method.</span></span>

<span data-ttu-id="1db52-181">Użytkownik nie może utworzyć klasy z nazwami będącymi zaczynać się ani kończyć znakiem podkreślenia chacater</span><span class="sxs-lookup"><span data-stu-id="1db52-181">The user may not create classes with names that begin or end with an underscore chacater</span></span>

<span data-ttu-id="1db52-182">Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="1db52-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="1db52-183">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1db52-183">Requirements</span></span>  
 <span data-ttu-id="1db52-184">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1db52-184">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1db52-185">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1db52-185">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1db52-186">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1db52-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db52-187">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1db52-187">See also</span></span>  
[<span data-ttu-id="1db52-188">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="1db52-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
