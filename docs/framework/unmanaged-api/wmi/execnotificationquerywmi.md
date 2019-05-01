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
ms.openlocfilehash: 9cac00ff96d0c7007bdd6135282c3f767217385e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935619"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="8ca67-103">ExecNotificationQueryWmi, funkcja</span><span class="sxs-lookup"><span data-stu-id="8ca67-103">ExecNotificationQueryWmi function</span></span>

<span data-ttu-id="8ca67-104">Wykonuje zapytanie, aby odbierać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8ca67-104">Executes a query to receive events.</span></span> <span data-ttu-id="8ca67-105">To wywołanie zwraca natychmiast, a obiekt wywołujący można sondować zwróconego modułu wyliczającego dla zdarzenia podczas ich dostarczania.</span><span class="sxs-lookup"><span data-stu-id="8ca67-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="8ca67-106">Zwalnianie zwróconego modułu wyliczającego anuluje zapytania.</span><span class="sxs-lookup"><span data-stu-id="8ca67-106">Releasing the returned enumerator cancels the query.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="8ca67-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ca67-107">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="8ca67-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ca67-108">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="8ca67-109">[in] Ciąg z językiem prawidłowe zapytanie obsługiwane przez Windows Management.</span><span class="sxs-lookup"><span data-stu-id="8ca67-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="8ca67-110">Musi to być "WQL" akronim języka WMI Query Language.</span><span class="sxs-lookup"><span data-stu-id="8ca67-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="8ca67-111">[in] Tekst zapytania.</span><span class="sxs-lookup"><span data-stu-id="8ca67-111">[in] The text of the query.</span></span> <span data-ttu-id="8ca67-112">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="8ca67-112">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="8ca67-113">[in] Kombinacja następujące dwie flagi, które mają wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8ca67-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="8ca67-114">Te wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8ca67-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

| <span data-ttu-id="8ca67-115">Stała</span><span class="sxs-lookup"><span data-stu-id="8ca67-115">Constant</span></span> | <span data-ttu-id="8ca67-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="8ca67-116">Value</span></span>  | <span data-ttu-id="8ca67-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca67-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="8ca67-118">0x10</span><span class="sxs-lookup"><span data-stu-id="8ca67-118">0x10</span></span> | <span data-ttu-id="8ca67-119">Flaga powoduje, że wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="8ca67-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="8ca67-120">Jeśli ta flaga nie jest ustawiona, połączenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="8ca67-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="8ca67-121">Jest to spowodowane zdarzenia są odbierane w sposób ciągły, co oznacza, że użytkownik musi wykonać sondowanie zwróconego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="8ca67-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="8ca67-122">Blokowanie to wywołanie przez czas nieokreślony uniemożliwia który.</span><span class="sxs-lookup"><span data-stu-id="8ca67-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="8ca67-123">0x20</span><span class="sxs-lookup"><span data-stu-id="8ca67-123">0x20</span></span> | <span data-ttu-id="8ca67-124">Funkcja zwraca tylko do przodu modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="8ca67-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="8ca67-125">Zwykle tylko do przodu moduły wyliczające są realizowane szybciej i używać mniej pamięci niż moduły wyliczające konwencjonalnych, ale nie zezwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="8ca67-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`\
<span data-ttu-id="8ca67-126">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="8ca67-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="8ca67-127">W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8ca67-127">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested events.</span></span>

`ppEnum`\
<span data-ttu-id="8ca67-128">[out] Jeśli żaden błąd nie wystąpi, otrzymuje wskaźnik, aby moduł wyliczający, który umożliwia obiektowi wywołującemu, można pobrać wystąpień w zestawie wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="8ca67-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="8ca67-129">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8ca67-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="8ca67-130">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="8ca67-130">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="8ca67-131">[in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="8ca67-131">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="8ca67-132">[in] Wskaźnik do [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) obiekt, który reprezentuje bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8ca67-132">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="8ca67-133">[in] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ca67-133">[in] The user name.</span></span> <span data-ttu-id="8ca67-134">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8ca67-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="8ca67-135">[in] Hasło.</span><span class="sxs-lookup"><span data-stu-id="8ca67-135">[in] The password.</span></span> <span data-ttu-id="8ca67-136">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8ca67-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="8ca67-137">[in] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ca67-137">[in] The domain name of the user.</span></span> <span data-ttu-id="8ca67-138">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8ca67-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="8ca67-139">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8ca67-139">Return value</span></span>

<span data-ttu-id="8ca67-140">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="8ca67-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8ca67-141">Stała</span><span class="sxs-lookup"><span data-stu-id="8ca67-141">Constant</span></span>  |<span data-ttu-id="8ca67-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="8ca67-142">Value</span></span>  |<span data-ttu-id="8ca67-143">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca67-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="8ca67-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="8ca67-144">0x80041003</span></span> | <span data-ttu-id="8ca67-145">Użytkownik nie ma uprawnień do wyświetlania przynajmniej jednej z klas, które może zwracać funkcji.</span><span class="sxs-lookup"><span data-stu-id="8ca67-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="8ca67-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8ca67-146">0x80041001</span></span> | <span data-ttu-id="8ca67-147">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="8ca67-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8ca67-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8ca67-148">0x80041008</span></span> | <span data-ttu-id="8ca67-149">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8ca67-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="8ca67-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="8ca67-150">0x80041010</span></span> | <span data-ttu-id="8ca67-151">Zapytanie Określa klasę, która nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="8ca67-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="8ca67-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="8ca67-152">0x80042002</span></span> | <span data-ttu-id="8ca67-153">Zażądano zbyt dużo precyzji podczas dostarczania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8ca67-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="8ca67-154">Większe tolerancji sondowania musi być określona.</span><span class="sxs-lookup"><span data-stu-id="8ca67-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="8ca67-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="8ca67-155">0x80042001</span></span> | <span data-ttu-id="8ca67-156">Zapytanie żąda informacji niż może zapewnić zarządzania Windows.</span><span class="sxs-lookup"><span data-stu-id="8ca67-156">The query requests more information than Windows Management can provide.</span></span> <span data-ttu-id="8ca67-157">To `HRESULT` jest zwracany, jeśli wyniki zapytania dotyczącego zdarzenia, w żądaniu skierowanym do sondowania wszystkie obiekty w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8ca67-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="8ca67-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="8ca67-158">0x80041017</span></span> | <span data-ttu-id="8ca67-159">Zapytania ma błąd składni.</span><span class="sxs-lookup"><span data-stu-id="8ca67-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="8ca67-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="8ca67-160">0x80041018</span></span> | <span data-ttu-id="8ca67-161">Żądany język kwerendy nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="8ca67-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="8ca67-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="8ca67-162">0x8004106c</span></span> | <span data-ttu-id="8ca67-163">Zapytanie jest zbyt złożony.</span><span class="sxs-lookup"><span data-stu-id="8ca67-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8ca67-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8ca67-164">0x80041006</span></span> | <span data-ttu-id="8ca67-165">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="8ca67-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="8ca67-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="8ca67-166">0x80041033</span></span> | <span data-ttu-id="8ca67-167">WMI został prawdopodobnie zatrzymane i ponowne uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="8ca67-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="8ca67-168">Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="8ca67-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="8ca67-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="8ca67-169">0x80041015</span></span> | <span data-ttu-id="8ca67-170">Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="8ca67-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="8ca67-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="8ca67-171">0x80041058</span></span> | <span data-ttu-id="8ca67-172">Nie można przeanalizować zapytania.</span><span class="sxs-lookup"><span data-stu-id="8ca67-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="8ca67-173">0</span><span class="sxs-lookup"><span data-stu-id="8ca67-173">0</span></span> | <span data-ttu-id="8ca67-174">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8ca67-174">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="8ca67-175">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ca67-175">Remarks</span></span>

<span data-ttu-id="8ca67-176">Ta funkcja zawija wywołanie do [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) metody.</span><span class="sxs-lookup"><span data-stu-id="8ca67-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) method.</span></span>

<span data-ttu-id="8ca67-177">Po powrocie z tej funkcji okresowo wywołujący zwracanego `ppEnum` obiekt [dalej](next.md) funkcji, aby sprawdzić, czy wszystkie zdarzenia są dostępne.</span><span class="sxs-lookup"><span data-stu-id="8ca67-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="8ca67-178">Istnieją limity liczby `AND` i `OR` słów kluczowych, które mogą być używane w kwerendach WQL.</span><span class="sxs-lookup"><span data-stu-id="8ca67-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="8ca67-179">Dużej liczby WQL słowa kluczowe używane w złożonych kwerend może spowodować, że usługi WMI do zwrócenia `WBEM_E_QUOTA_VIOLATION` (lub 0x8004106c) kod błędu, jako `HRESULT` wartość.</span><span class="sxs-lookup"><span data-stu-id="8ca67-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="8ca67-180">Limit słowa kluczowe języka WQL zależy od tego, jak złożona jest zapytanie.</span><span class="sxs-lookup"><span data-stu-id="8ca67-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="8ca67-181">Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="8ca67-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="8ca67-182">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ca67-182">Requirements</span></span>

<span data-ttu-id="8ca67-183">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ca67-183">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="8ca67-184">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8ca67-184">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="8ca67-185">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca67-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8ca67-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ca67-186">See also</span></span>

- [<span data-ttu-id="8ca67-187">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="8ca67-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)