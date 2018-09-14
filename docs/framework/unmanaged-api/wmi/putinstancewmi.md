---
title: Funkcja PutInstanceWmi (niezarządzany wykaz interfejsów API)
description: Funkcja PutInstanceWmi tworzy lub aktualizuje wystąpienia istniejącej klasy.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67abf017040b9e6bbe9b10e560c8d57c124ae84e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516688"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="34857-103">PutInstanceWmi — funkcja</span><span class="sxs-lookup"><span data-stu-id="34857-103">PutInstanceWmi function</span></span>
<span data-ttu-id="34857-104">Tworzy lub aktualizuje wystąpienia istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="34857-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="34857-105">Wystąpienie jest zapisywany do repozytorium WMI.</span><span class="sxs-lookup"><span data-stu-id="34857-105">The instance is written to the WMI repository.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="34857-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="34857-106">Syntax</span></span>  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="34857-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="34857-107">Parameters</span></span>

`pInst`    
<span data-ttu-id="34857-108">[in] Wskaźnik do wystąpienia jako writen.</span><span class="sxs-lookup"><span data-stu-id="34857-108">[in] A pointer to the instance to be writen.</span></span>

`lFlags`   
<span data-ttu-id="34857-109">[in] Kombinacja flag, które mają wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="34857-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="34857-110">Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="34857-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="34857-111">Stała</span><span class="sxs-lookup"><span data-stu-id="34857-111">Constant</span></span>  |<span data-ttu-id="34857-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="34857-112">Value</span></span>  |<span data-ttu-id="34857-113">Opis</span><span class="sxs-lookup"><span data-stu-id="34857-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="34857-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="34857-114">0x20000</span></span> | <span data-ttu-id="34857-115">Jeśli ustawiona, usługi WMI nie przechowuje żadnych kwalifikatorów z **zmieniony** wersja.</span><span class="sxs-lookup"><span data-stu-id="34857-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> </br> <span data-ttu-id="34857-116">W przeciwnym razie zestawu, zakłada się, że ten obiekt nie jest zlokalizowana, a wszystkie kwalifikatory są storedwith tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="34857-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="34857-117">0</span><span class="sxs-lookup"><span data-stu-id="34857-117">0</span></span> | <span data-ttu-id="34857-118">Utwórz wystąpienie, jeśli on nie istnieje, lub go zastąpić, jeśli już istnieje.</span><span class="sxs-lookup"><span data-stu-id="34857-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="34857-119">1</span><span class="sxs-lookup"><span data-stu-id="34857-119">1</span></span> | <span data-ttu-id="34857-120">Aktualizuj wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="34857-120">Update the instance.</span></span> <span data-ttu-id="34857-121">Wystąpienie musi istnieć przez wywołanie zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="34857-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="34857-122">2</span><span class="sxs-lookup"><span data-stu-id="34857-122">2</span></span> | <span data-ttu-id="34857-123">Utwórz wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="34857-123">Create the instance.</span></span> <span data-ttu-id="34857-124">Wywołanie zakończy się niepowodzeniem, jeśli wystąpienie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="34857-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="34857-125">0x10</span><span class="sxs-lookup"><span data-stu-id="34857-125">0x10</span></span> | <span data-ttu-id="34857-126">Flaga powoduje, że wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="34857-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`  
<span data-ttu-id="34857-127">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="34857-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="34857-128">W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy.</span><span class="sxs-lookup"><span data-stu-id="34857-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="34857-129">[out] Jeśli `null`, ten parametr jest nieużywana.</span><span class="sxs-lookup"><span data-stu-id="34857-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="34857-130">Jeśli `lFlags` zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja zwraca natychmiast za pomocą `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="34857-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="34857-131">`ppCallResult` Parametru otrzymuje wskaźnik do nowego [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) obiektu.</span><span class="sxs-lookup"><span data-stu-id="34857-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="34857-132">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="34857-132">Return value</span></span>

<span data-ttu-id="34857-133">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="34857-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="34857-134">Stała</span><span class="sxs-lookup"><span data-stu-id="34857-134">Constant</span></span>  |<span data-ttu-id="34857-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="34857-135">Value</span></span>  |<span data-ttu-id="34857-136">Opis</span><span class="sxs-lookup"><span data-stu-id="34857-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="34857-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="34857-137">0x80041003</span></span> | <span data-ttu-id="34857-138">Użytkownik nie ma uprawnień do aktualizowania wystąpienie określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="34857-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="34857-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="34857-139">0x80041001</span></span> | <span data-ttu-id="34857-140">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="34857-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="34857-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="34857-141">0x80041010</span></span> | <span data-ttu-id="34857-142">Klasy obsługi tego wystąpienia jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="34857-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="34857-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="34857-143">0x80041028</span></span> | <span data-ttu-id="34857-144">`null` została określona dla właściwości, która nie może być `null`, taki, który jest oznaczony za **indeksowany** lub **Not_Null** kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="34857-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="34857-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="34857-145">0x8004100f</span></span> | <span data-ttu-id="34857-146">Określone wystąpienie jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="34857-146">The specified instance is not valid.</span></span> <span data-ttu-id="34857-147">(Na przykład, wywołanie `PutInstanceWmi` za pomocą klasy zwraca tę wartość.)</span><span class="sxs-lookup"><span data-stu-id="34857-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="34857-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="34857-148">0x80041008</span></span> | <span data-ttu-id="34857-149">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="34857-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="34857-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="34857-150">0x80041019</span></span> | <span data-ttu-id="34857-151">`WBEM_FLAG_CREATE_ONLY` Określono flagę, ale wystąpienie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="34857-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="34857-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="34857-152">0x80041002</span></span> | <span data-ttu-id="34857-153">`WBEM_FLAG_UPDATE_ONLY` został określony w `lFlags`, ale wystąpienie nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="34857-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="34857-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="34857-154">0x80041006</span></span> | <span data-ttu-id="34857-155">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="34857-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="34857-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="34857-156">0x80041033</span></span> | <span data-ttu-id="34857-157">WMI został prawdopodobnie zatrzymane i ponowne uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="34857-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="34857-158">Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="34857-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="34857-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="34857-159">0x80041015</span></span> | <span data-ttu-id="34857-160">Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="34857-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="34857-161">0</span><span class="sxs-lookup"><span data-stu-id="34857-161">0</span></span> | <span data-ttu-id="34857-162">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="34857-162">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="34857-163">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34857-163">Remarks</span></span>

<span data-ttu-id="34857-164">Ta funkcja zawija wywołanie do [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) metody.</span><span class="sxs-lookup"><span data-stu-id="34857-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="34857-165">`PutInstanceWmi` Obsługuje tworzenie wystąpień i aktualizowanie wystąpień istniejące klasy tylko funkcji.</span><span class="sxs-lookup"><span data-stu-id="34857-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="34857-166">W zależności od sposobu `pCtx` zestaw parametrów, niektórych lub wszystkich właściwości wystąpienia są aktualizowane.</span><span class="sxs-lookup"><span data-stu-id="34857-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span> 

<span data-ttu-id="34857-167">Gdy wystąpienie wskazywany przez `pInst` należy do podklasy, Windows Management wywołania odpowiedzialny za klasy, z których pochodzi podklasy dostawców.</span><span class="sxs-lookup"><span data-stu-id="34857-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="34857-168">Wszystkie z tych dostawców musi zakończyć się dla oryginalnej `PutInstanceWmi` żądanie zakończyło się sukcesem.</span><span class="sxs-lookup"><span data-stu-id="34857-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="34857-169">Najpierw nosi nazwę dostawcy, obsługujące klasie najwyższego poziomu w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="34857-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="34857-170">Kolejności wywoływania będzie kontynuowane z użyciem podklasę klasy najwyższego poziomu i rozpoczynające się od góry do dołu dopóki nie osiągnie zarządzania Windows dostawca dla klasy będącej właścicielem wystąpienia wskazywany przez `pInst`.</span><span class="sxs-lookup"><span data-stu-id="34857-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="34857-171">Windows Management nie wywołuje dostawców dla każdego wystąpienia klasy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="34857-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span> 

<span data-ttu-id="34857-172">Jeśli aplikacja musi zaktualizować wystąpienie, które należy do hierarchii klas, `pInst` parametru musi wskazywać na wystąpienie zawierającego właściwości, które mają być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="34857-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="34857-173">Oznacza to, należy wziąć pod uwagę wystąpienie docelowe, który należy do **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="34857-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="34857-174">**ClassB** wystąpienia jest pochodną **ClassA**, i **ClassA** nie definiuje właściwości **PropA**.</span><span class="sxs-lookup"><span data-stu-id="34857-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="34857-175">Jeśli aplikacja chce, aby wprowadzić zmiany do wartości **PropA** w **ClassB** wystąpienia, należy ustawić `pInst` tego wystąpienia, a nie wystąpieniem **ClassA** .</span><span class="sxs-lookup"><span data-stu-id="34857-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="34857-176">Wywoływanie `PutInstanceWmi` nie jest dozwolona w wystąpieniu klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="34857-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="34857-177">Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="34857-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="34857-178">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34857-178">Requirements</span></span>  
 <span data-ttu-id="34857-179">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34857-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34857-180">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="34857-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="34857-181">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="34857-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34857-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34857-182">See also</span></span>  
[<span data-ttu-id="34857-183">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="34857-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
