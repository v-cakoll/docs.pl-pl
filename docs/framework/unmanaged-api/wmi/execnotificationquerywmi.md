---
title: Funkcja ExecNotificationQueryWmi (niezarządzany wykaz interfejsów API)
description: Funkcja ExecNotificationQueryWmi wykonuje zapytanie w celu odbierania zdarzeń.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b5c26ab9c273b134915eea39078a83f569bcd32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462419"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="0a7a0-103">Funkcja ExecNotificationQueryWmi</span><span class="sxs-lookup"><span data-stu-id="0a7a0-103">ExecNotificationQueryWmi function</span></span>
<span data-ttu-id="0a7a0-104">Wykonuje zapytanie w celu odbierania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-104">Executes a query to receive events.</span></span> <span data-ttu-id="0a7a0-105">Wywołanie zwraca natychmiast, a obiekt wywołujący można sondować zwrócony modułu wyliczającego dla zdarzeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="0a7a0-106">Zwalnianie zwrócony modułu wyliczającego anuluje zapytania.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-106">Releasing the returned enumerator cancels the query.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="0a7a0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a7a0-107">Syntax</span></span>  
  
```  
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

## <a name="parameters"></a><span data-ttu-id="0a7a0-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a7a0-108">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="0a7a0-109">[in] Ciąg z prawidłowego zapytania języka obsługiwanego przez zarządzanie systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="0a7a0-110">Musi być "WQL" akronim język zapytań usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="0a7a0-111">[in] Tekst zapytania.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-111">[in] The text of the query.</span></span> <span data-ttu-id="0a7a0-112">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-112">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="0a7a0-113">[in] Kombinacja następujące dwie flagi, które wpływają na działanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="0a7a0-114">Te wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> 

| <span data-ttu-id="0a7a0-115">Stała</span><span class="sxs-lookup"><span data-stu-id="0a7a0-115">Constant</span></span> | <span data-ttu-id="0a7a0-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="0a7a0-116">Value</span></span>  | <span data-ttu-id="0a7a0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="0a7a0-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="0a7a0-118">0x10</span><span class="sxs-lookup"><span data-stu-id="0a7a0-118">0x10</span></span> | <span data-ttu-id="0a7a0-119">Flaga powoduje Półsynchroniczne wywołania.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="0a7a0-120">Jeśli ta flaga nie jest ustawiona, połączenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="0a7a0-121">Jest to spowodowane zdarzenia są odbierane w sposób ciągły, co oznacza, że użytkownik musi wykonać sondowanie zwrócony modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="0a7a0-122">Blokuje to wywołanie w nieskończoność uniemożliwia który.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="0a7a0-123">0x20</span><span class="sxs-lookup"><span data-stu-id="0a7a0-123">0x20</span></span> | <span data-ttu-id="0a7a0-124">Funkcja zwraca tylko do przodu modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="0a7a0-125">Zwykle tylko do przodu moduły wyliczające są szybsze i używają mniej pamięci niż wyliczenia z konwencjonalnej, ale nie zezwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="0a7a0-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`  
<span data-ttu-id="0a7a0-126">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="0a7a0-127">W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-127">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested events.</span></span> 

`ppEnum`  
<span data-ttu-id="0a7a0-128">[out] Jeśli nie występują błędy, uzyskuje wskaźnik do moduł wyliczający, który umożliwia obiekt wywołujący, aby pobrać wystąpień w zestawie wyników kwerendy.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="0a7a0-129">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="0a7a0-130">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-130">[in] The authorization level.</span></span>

<span data-ttu-id="0a7a0-131">`impLevel` [in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-131">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="0a7a0-132">[in] Wskaźnik do [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) obiekt, który reprezentuje bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-132">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="0a7a0-133">[in] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-133">[in] The user name.</span></span> <span data-ttu-id="0a7a0-134">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="0a7a0-135">[in] Hasło.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-135">[in] The password.</span></span> <span data-ttu-id="0a7a0-136">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="0a7a0-137">[in] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-137">[in] The domain name of the user.</span></span> <span data-ttu-id="0a7a0-138">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="0a7a0-139">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0a7a0-139">Return value</span></span>

<span data-ttu-id="0a7a0-140">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="0a7a0-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0a7a0-141">Stała</span><span class="sxs-lookup"><span data-stu-id="0a7a0-141">Constant</span></span>  |<span data-ttu-id="0a7a0-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="0a7a0-142">Value</span></span>  |<span data-ttu-id="0a7a0-143">Opis</span><span class="sxs-lookup"><span data-stu-id="0a7a0-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="0a7a0-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="0a7a0-144">0x80041003</span></span> | <span data-ttu-id="0a7a0-145">Użytkownik nie ma uprawnień do wyświetlania przynajmniej jednej z klas, które może zwracać funkcji.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="0a7a0-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0a7a0-146">0x80041001</span></span> | <span data-ttu-id="0a7a0-147">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0a7a0-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0a7a0-148">0x80041008</span></span> | <span data-ttu-id="0a7a0-149">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="0a7a0-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="0a7a0-150">0x80041010</span></span> | <span data-ttu-id="0a7a0-151">Kwerenda Określa klasę, która nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="0a7a0-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="0a7a0-152">0x80042002</span></span> | <span data-ttu-id="0a7a0-153">Zażądano zbyt dużo dokładność w dostarczania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="0a7a0-154">Należy określić większą tolerancją sondowania.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="0a7a0-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="0a7a0-155">0x80042001</span></span> | <span data-ttu-id="0a7a0-156">Requess zapytań zapewniają więcej informacji niż zarządzanie systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-156">The query requess more information than Windows Management can provide.</span></span> <span data-ttu-id="0a7a0-157">To `HRESULT` jest zwracany, gdy kwerenda powoduje żądanie, aby wykonać sondowanie wszystkie obiekty w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="0a7a0-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="0a7a0-158">0x80041017</span></span> | <span data-ttu-id="0a7a0-159">Zapytania wystąpił błąd składni.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="0a7a0-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="0a7a0-160">0x80041018</span></span> | <span data-ttu-id="0a7a0-161">Żądany język kwerendy nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="0a7a0-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="0a7a0-162">0x8004106c</span></span> | <span data-ttu-id="0a7a0-163">Zapytanie jest zbyt złożony.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0a7a0-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0a7a0-164">0x80041006</span></span> | <span data-ttu-id="0a7a0-165">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="0a7a0-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="0a7a0-166">0x80041033</span></span> | <span data-ttu-id="0a7a0-167">Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="0a7a0-168">Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="0a7a0-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="0a7a0-169">0x80041015</span></span> | <span data-ttu-id="0a7a0-170">Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="0a7a0-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="0a7a0-171">0x80041058</span></span> | <span data-ttu-id="0a7a0-172">Nie można przeanalizować zapytania.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="0a7a0-173">0</span><span class="sxs-lookup"><span data-stu-id="0a7a0-173">0</span></span> | <span data-ttu-id="0a7a0-174">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-174">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0a7a0-175">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a7a0-175">Remarks</span></span>

<span data-ttu-id="0a7a0-176">Ta funkcja jest zawijana wywołanie [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="0a7a0-177">Po powrocie z funkcji okresowo wywołujący zwróconego `ppEnum` do obiektu [dalej](next.md) funkcji, aby sprawdzić, czy wszystkie zdarzenia są dostępne.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="0a7a0-178">Istnieją ograniczenia liczby `AND` i `OR` słów kluczowych, które mogą być używane w zapytaniach WQL.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="0a7a0-179">Dużą liczbą słów kluczowych języka WQL używanych w zapytaniu złożonych może spowodować WMI do zwrócenia `WBEM_E_QUOTA_VIOLATION` (lub 0x8004106c) kod błędu jako `HRESULT` wartość.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="0a7a0-180">Limit słów kluczowych języka WQL zależy od tego, jak złożoność zapytanie jest.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="0a7a0-181">Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a7a0-182">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a7a0-182">Requirements</span></span>  
 <span data-ttu-id="0a7a0-183">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a7a0-183">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a7a0-184">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0a7a0-184">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0a7a0-185">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0a7a0-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a7a0-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a7a0-186">See also</span></span>  
[<span data-ttu-id="0a7a0-187">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="0a7a0-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
