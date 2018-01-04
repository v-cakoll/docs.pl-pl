---
title: "Funkcja PutInstanceWmi (niezarządzany wykaz interfejsów API)"
description: "Funkcja PutInstanceWmi tworzy lub aktualizuje wystąpienia istniejącej klasy."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutInstanceWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutInstanceWmi
helpviewer_keywords: PutInstanceWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1996103eea87562226537f9aa90dc337c56313c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="f5ded-103">Funkcja PutInstanceWmi</span><span class="sxs-lookup"><span data-stu-id="f5ded-103">PutInstanceWmi function</span></span>
<span data-ttu-id="f5ded-104">Tworzy lub aktualizuje wystąpienia istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="f5ded-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="f5ded-105">Wystąpienie jest zapisywany w repozytorium WMI.</span><span class="sxs-lookup"><span data-stu-id="f5ded-105">The instance is written to the WMI repository.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f5ded-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5ded-106">Syntax</span></span>  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="f5ded-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5ded-107">Parameters</span></span>

`pInst`    
<span data-ttu-id="f5ded-108">[in] Wskaźnik do wystąpienie było writen.</span><span class="sxs-lookup"><span data-stu-id="f5ded-108">[in] A pointer to the instance to be writen.</span></span>

`lFlags`   
<span data-ttu-id="f5ded-109">[in] Kombinacja flag, które wpływają na działanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f5ded-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="f5ded-110">Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="f5ded-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="f5ded-111">Stała</span><span class="sxs-lookup"><span data-stu-id="f5ded-111">Constant</span></span>  |<span data-ttu-id="f5ded-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="f5ded-112">Value</span></span>  |<span data-ttu-id="f5ded-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f5ded-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="f5ded-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="f5ded-114">0x20000</span></span> | <span data-ttu-id="f5ded-115">Jeśli ustawiona, usługi WMI nie przechowuje żadnych kwalifikatorów z **zmieniony** podtyp.</span><span class="sxs-lookup"><span data-stu-id="f5ded-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> </br> <span data-ttu-id="f5ded-116">Jeśli nie zestawu, zakłada się, że ten obiekt nie jest lokalizowany, a wszystkie kwalifikatory są storedwith tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f5ded-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="f5ded-117">0</span><span class="sxs-lookup"><span data-stu-id="f5ded-117">0</span></span> | <span data-ttu-id="f5ded-118">Utworzenie wystąpienia, jeśli nie istnieje lub jego zastąpienie, jeśli już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f5ded-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="f5ded-119">1</span><span class="sxs-lookup"><span data-stu-id="f5ded-119">1</span></span> | <span data-ttu-id="f5ded-120">Zaktualizuj wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="f5ded-120">Update the instance.</span></span> <span data-ttu-id="f5ded-121">Wystąpienie musi istnieć wywołanie powiódł się.</span><span class="sxs-lookup"><span data-stu-id="f5ded-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="f5ded-122">2</span><span class="sxs-lookup"><span data-stu-id="f5ded-122">2</span></span> | <span data-ttu-id="f5ded-123">Utworzenie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f5ded-123">Create the instance.</span></span> <span data-ttu-id="f5ded-124">Wywołanie zakończy się niepowodzeniem, jeśli wystąpienie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f5ded-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="f5ded-125">0x10</span><span class="sxs-lookup"><span data-stu-id="f5ded-125">0x10</span></span> | <span data-ttu-id="f5ded-126">Flaga powoduje Półsynchroniczne wywołania.</span><span class="sxs-lookup"><span data-stu-id="f5ded-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`  
<span data-ttu-id="f5ded-127">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="f5ded-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="f5ded-128">W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy.</span><span class="sxs-lookup"><span data-stu-id="f5ded-128">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="f5ded-129">[out] Jeśli `null`, ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="f5ded-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="f5ded-130">Jeśli `lFlags` zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja zwraca bezpośrednio z `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="f5ded-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="f5ded-131">`ppCallResult` Parametru otrzymuje wskaźnik do nowego [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) obiektu.</span><span class="sxs-lookup"><span data-stu-id="f5ded-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="f5ded-132">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f5ded-132">Return value</span></span>

<span data-ttu-id="f5ded-133">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="f5ded-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f5ded-134">Stała</span><span class="sxs-lookup"><span data-stu-id="f5ded-134">Constant</span></span>  |<span data-ttu-id="f5ded-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="f5ded-135">Value</span></span>  |<span data-ttu-id="f5ded-136">Opis</span><span class="sxs-lookup"><span data-stu-id="f5ded-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="f5ded-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="f5ded-137">0x80041003</span></span> | <span data-ttu-id="f5ded-138">Użytkownik nie ma uprawnień do zaktualizowania wystąpienia określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="f5ded-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="f5ded-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f5ded-139">0x80041001</span></span> | <span data-ttu-id="f5ded-140">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="f5ded-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="f5ded-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="f5ded-141">0x80041010</span></span> | <span data-ttu-id="f5ded-142">Klasy obsługi tego wystąpienia jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="f5ded-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="f5ded-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="f5ded-143">0x80041028</span></span> | <span data-ttu-id="f5ded-144">`null` został określony dla właściwości, która nie może być `null`, takiej jak zostało oznaczone przez **indeksowane** lub **Not_Null** kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="f5ded-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="f5ded-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="f5ded-145">0x8004100f</span></span> | <span data-ttu-id="f5ded-146">Określone wystąpienie jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f5ded-146">The specified instance is not valid.</span></span> <span data-ttu-id="f5ded-147">(Na przykład wywołanie elementu `PutInstanceWmi` z klasą zwraca tę wartość.)</span><span class="sxs-lookup"><span data-stu-id="f5ded-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f5ded-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f5ded-148">0x80041008</span></span> | <span data-ttu-id="f5ded-149">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f5ded-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="f5ded-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="f5ded-150">0x80041019</span></span> | <span data-ttu-id="f5ded-151">`WBEM_FLAG_CREATE_ONLY` Określono flagę, ale wystąpienie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f5ded-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="f5ded-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f5ded-152">0x80041002</span></span> | <span data-ttu-id="f5ded-153">`WBEM_FLAG_UPDATE_ONLY`został określony w `lFlags`, ale wystąpienie nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f5ded-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f5ded-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f5ded-154">0x80041006</span></span> | <span data-ttu-id="f5ded-155">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="f5ded-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="f5ded-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="f5ded-156">0x80041033</span></span> | <span data-ttu-id="f5ded-157">Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="f5ded-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="f5ded-158">Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="f5ded-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="f5ded-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="f5ded-159">0x80041015</span></span> | <span data-ttu-id="f5ded-160">Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="f5ded-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f5ded-161">0</span><span class="sxs-lookup"><span data-stu-id="f5ded-161">0</span></span> | <span data-ttu-id="f5ded-162">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f5ded-162">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="f5ded-163">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5ded-163">Remarks</span></span>

<span data-ttu-id="f5ded-164">Ta funkcja jest zawijana wywołanie [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="f5ded-164">This function wraps a call to the [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="f5ded-165">`PutInstanceWmi` Funkcji obsługuje tworzenie wystąpień i aktualizowanie wystąpień tylko istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="f5ded-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="f5ded-166">W zależności od sposobu `pCtx` parametru jest ustawiona, niektórych lub wszystkich właściwości wystąpienia zostały zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="f5ded-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span> 

<span data-ttu-id="f5ded-167">Jeśli wystąpienie wskazywana przez `pInst` należy do podklasy, zarządzanie systemem Windows wywołania wszystkich dostawców odpowiedzialny za klasy, z których pochodzi podklasy.</span><span class="sxs-lookup"><span data-stu-id="f5ded-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="f5ded-168">Wszystkie z tych dostawców musi niepowodzeniem dla oryginalnej `PutInstanceWmi` żądanie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="f5ded-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="f5ded-169">Dostawca obsługi klasie najwyższego poziomu w hierarchii jest nazywany najpierw.</span><span class="sxs-lookup"><span data-stu-id="f5ded-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="f5ded-170">Kolejności wywoływania kontynuuje podklasa klasy najwyższego poziomu i będzie kontynuowane od góry do dołu, dopóki nie osiągnie zarządzania systemu Windows dostawcę dla klasy będącej właścicielem, jeśli wystąpienie wskazywana przez `pInst`.</span><span class="sxs-lookup"><span data-stu-id="f5ded-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="f5ded-171">Zarządzanie systemem Windows nie wywołuje dostawców dla każdego wystąpienia klasy podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f5ded-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span> 

<span data-ttu-id="f5ded-172">W przypadku aplikacji, należy zaktualizować wystąpienie, które należy do hierarchii klas, `pInst` parametru musi wskazywać wystąpienie zawierającego właściwości, które mają być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="f5ded-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="f5ded-173">Oznacza to, należy wziąć pod uwagę obiektu docelowego, który należy do **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="f5ded-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="f5ded-174">**ClassB** wystąpienia jest pochodną **ClassA**, i **ClassA** definiuje właściwość **PropA**.</span><span class="sxs-lookup"><span data-stu-id="f5ded-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="f5ded-175">Jeśli aplikacja chce wprowadzić zmianę do wartości **PropA** w **ClassB** wystąpienia, należy ustawić `pInst` do tego wystąpienia, a nie wystąpienia **ClassA** .</span><span class="sxs-lookup"><span data-stu-id="f5ded-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="f5ded-176">Wywoływanie `PutInstanceWmi` nie jest dozwolona w wystąpieniu klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="f5ded-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="f5ded-177">Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="f5ded-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5ded-178">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5ded-178">Requirements</span></span>  
 <span data-ttu-id="f5ded-179">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5ded-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5ded-180">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f5ded-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f5ded-181">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f5ded-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5ded-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5ded-182">See also</span></span>  
[<span data-ttu-id="f5ded-183">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="f5ded-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
