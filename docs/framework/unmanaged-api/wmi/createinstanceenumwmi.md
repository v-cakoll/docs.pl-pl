---
title: "Funkcja CreateInstanceEnumWmi (niezarządzany wykaz interfejsów API)"
description: "Funkcja CreateInstanceEnumWmi zwraca moduł wyliczający zawierający wystąpień określonej klasy, które spełniają kryteria wyboru."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CreateInstanceEnumWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CreateInstanceEnumWmi
helpviewer_keywords: CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b796771b07dee28470d37ca3e4292c0a244e056b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="b8e2f-103">Funkcja CreateInstanceEnumWmi</span><span class="sxs-lookup"><span data-stu-id="b8e2f-103">CreateInstanceEnumWmi function</span></span>
<span data-ttu-id="b8e2f-104">Zwraca moduł wyliczający, który zwraca wystąpienia określonej klasy, które spełniają kryteria wyboru określony.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b8e2f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8e2f-105">Syntax</span></span>  
  
```  
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a><span data-ttu-id="b8e2f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8e2f-106">Parameters</span></span>

`strFilter`    
<span data-ttu-id="b8e2f-107">[in] Nazwa klasy, dla którego wystąpienia są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="b8e2f-108">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-108">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="b8e2f-109">[in] Kombinacja flag, które wpływają na działanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="b8e2f-110">Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="b8e2f-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="b8e2f-111">Stała</span><span class="sxs-lookup"><span data-stu-id="b8e2f-111">Constant</span></span>  |<span data-ttu-id="b8e2f-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="b8e2f-112">Value</span></span>  |<span data-ttu-id="b8e2f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b8e2f-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="b8e2f-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="b8e2f-114">0x20000</span></span> | <span data-ttu-id="b8e2f-115">Jeśli zestaw, funkcja pobiera poprawionych kwalifikatorów przechowywane w zlokalizowanych nazw ustawień regionalnych bieżącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="b8e2f-116">Jeśli nie zestawu, funkcja pobiera tylko kwalifikatory przechowywane w przestrzeni nazw bezpośrednim.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="b8e2f-117">0</span><span class="sxs-lookup"><span data-stu-id="b8e2f-117">0</span></span> | <span data-ttu-id="b8e2f-118">Wyliczenie zawiera to i podklasami w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="b8e2f-119">1</span><span class="sxs-lookup"><span data-stu-id="b8e2f-119">1</span></span> | <span data-ttu-id="b8e2f-120">Wyliczenie zawiera tylko czysty wystąpienia tej klasy i wyklucza wszystkie wystąpienia podklas, które dostarczają właściwości nie można odnaleźć w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="b8e2f-121">0x10</span><span class="sxs-lookup"><span data-stu-id="b8e2f-121">0x10</span></span> | <span data-ttu-id="b8e2f-122">Flaga powoduje Półsynchroniczne wywołania.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="b8e2f-123">0x20</span><span class="sxs-lookup"><span data-stu-id="b8e2f-123">0x20</span></span> | <span data-ttu-id="b8e2f-124">Funkcja zwraca tylko do przodu modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="b8e2f-125">Zwykle tylko do przodu moduły wyliczające są szybsze i używają mniej pamięci niż wyliczenia z konwencjonalnej, ale nie zezwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="b8e2f-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="b8e2f-126">0</span><span class="sxs-lookup"><span data-stu-id="b8e2f-126">0</span></span> | <span data-ttu-id="b8e2f-127">WMI zachowuje wskaźników do obiektów w enumration, dopóki ich wydania.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-127">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="b8e2f-128">Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="b8e2f-129">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="b8e2f-130">W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienia, które mogą być używane przez dostawcę, który dostarcza żądanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-130">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`  
<span data-ttu-id="b8e2f-131">[out] Uzyskuje wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="b8e2f-132">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-132">[in] The authorization level.</span></span>

<span data-ttu-id="b8e2f-133">`impLevel`[in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-133">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="b8e2f-134">[in] Wskaźnik do [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) obiekt, który reprezentuje bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-134">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="b8e2f-135">[in] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-135">[in] The user name.</span></span> <span data-ttu-id="b8e2f-136">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="b8e2f-137">[in] Hasło.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-137">[in] The password.</span></span> <span data-ttu-id="b8e2f-138">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="b8e2f-139">[in] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-139">[in] The domain name of the user.</span></span> <span data-ttu-id="b8e2f-140">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="b8e2f-141">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b8e2f-141">Return value</span></span>

<span data-ttu-id="b8e2f-142">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="b8e2f-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b8e2f-143">Stała</span><span class="sxs-lookup"><span data-stu-id="b8e2f-143">Constant</span></span>  |<span data-ttu-id="b8e2f-144">Wartość</span><span class="sxs-lookup"><span data-stu-id="b8e2f-144">Value</span></span>  |<span data-ttu-id="b8e2f-145">Opis</span><span class="sxs-lookup"><span data-stu-id="b8e2f-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="b8e2f-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="b8e2f-146">0x80041003</span></span> | <span data-ttu-id="b8e2f-147">Użytkownik nie ma uprawnień do wyświetlania wystąpienia określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="b8e2f-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b8e2f-148">0x80041001</span></span> | <span data-ttu-id="b8e2f-149">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="b8e2f-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="b8e2f-150">0x80041010</span></span> | <span data-ttu-id="b8e2f-151">`strFilter`nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b8e2f-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b8e2f-152">0x80041008</span></span> | <span data-ttu-id="b8e2f-153">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b8e2f-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b8e2f-154">0x80041006</span></span> | <span data-ttu-id="b8e2f-155">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="b8e2f-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="b8e2f-156">0x80041033</span></span> | <span data-ttu-id="b8e2f-157">Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="b8e2f-158">Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="b8e2f-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="b8e2f-159">0x80041015</span></span> | <span data-ttu-id="b8e2f-160">Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b8e2f-161">0</span><span class="sxs-lookup"><span data-stu-id="b8e2f-161">0</span></span> | <span data-ttu-id="b8e2f-162">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-162">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b8e2f-163">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8e2f-163">Remarks</span></span>

<span data-ttu-id="b8e2f-164">Ta funkcja jest zawijana wywołanie [metodę IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-164">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="b8e2f-165">Należy pamiętać, że zwrócony modułu wyliczającego nie mogą mieć żadnego elementu.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="b8e2f-166">Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="b8e2f-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8e2f-167">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8e2f-167">Requirements</span></span>  
 <span data-ttu-id="b8e2f-168">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8e2f-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8e2f-169">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b8e2f-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b8e2f-170">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b8e2f-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e2f-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8e2f-171">See also</span></span>  
[<span data-ttu-id="b8e2f-172">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="b8e2f-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
