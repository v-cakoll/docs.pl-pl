---
title: ExecNotificationQueryWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja ExecNotificationQueryWmi wykonuje zapytanie, aby odbierać zdarzenia.
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
ms.openlocfilehash: 3d8a7683eef52a5e91bf7aa84d5aa7db7dbdac8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130443"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="67fc2-103">ExecNotificationQueryWmi, funkcja</span><span class="sxs-lookup"><span data-stu-id="67fc2-103">ExecNotificationQueryWmi function</span></span>

<span data-ttu-id="67fc2-104">Wykonuje zapytanie do odbierania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="67fc2-104">Executes a query to receive events.</span></span> <span data-ttu-id="67fc2-105">Wywołanie wraca natychmiast, a obiekt wywołujący może sondować zwracany moduł wyliczający dla zdarzeń po ich nadejściu.</span><span class="sxs-lookup"><span data-stu-id="67fc2-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="67fc2-106">Zwolnienie zwróconego modułu wyliczającego powoduje anulowanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="67fc2-106">Releasing the returned enumerator cancels the query.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="67fc2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="67fc2-107">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="67fc2-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="67fc2-108">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="67fc2-109">podczas Ciąg z prawidłowym językiem zapytań obsługiwanym przez zarządzanie systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="67fc2-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="67fc2-110">Musi to być "WQL", akronim dla język zapytań usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="67fc2-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="67fc2-111">podczas Tekst zapytania.</span><span class="sxs-lookup"><span data-stu-id="67fc2-111">[in] The text of the query.</span></span> <span data-ttu-id="67fc2-112">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="67fc2-112">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="67fc2-113">podczas Kombinacja następujących dwóch flag mających wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="67fc2-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="67fc2-114">Te wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="67fc2-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

| <span data-ttu-id="67fc2-115">Stała</span><span class="sxs-lookup"><span data-stu-id="67fc2-115">Constant</span></span> | <span data-ttu-id="67fc2-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="67fc2-116">Value</span></span>  | <span data-ttu-id="67fc2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="67fc2-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="67fc2-118">0x10</span><span class="sxs-lookup"><span data-stu-id="67fc2-118">0x10</span></span> | <span data-ttu-id="67fc2-119">Flaga powoduje wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="67fc2-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="67fc2-120">Jeśli ta flaga nie jest ustawiona, wywołanie zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="67fc2-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="67fc2-121">Wynika to z faktu, że zdarzenia są ciągle odbierane, co oznacza, że użytkownik musi sondować zwrócony moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="67fc2-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="67fc2-122">Zablokowanie tego wywołania bezterminowo sprawia, że jest to niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="67fc2-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="67fc2-123">0x20</span><span class="sxs-lookup"><span data-stu-id="67fc2-123">0x20</span></span> | <span data-ttu-id="67fc2-124">Funkcja zwraca moduł wyliczający tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="67fc2-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="67fc2-125">Zazwyczaj moduły wyliczające tylko do przodu są szybsze i używają mniej pamięci niż konwencjonalne moduły wyliczające, ale nie pozwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="67fc2-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`\
<span data-ttu-id="67fc2-126">podczas Zazwyczaj ta wartość jest `null`.</span><span class="sxs-lookup"><span data-stu-id="67fc2-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="67fc2-127">W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="67fc2-127">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested events.</span></span>

`ppEnum`\
<span data-ttu-id="67fc2-128">określoną Jeśli błąd nie wystąpi, otrzymuje wskaźnik do modułu wyliczającego, który umożliwia obiektowi wywołującemu pobieranie wystąpień w zestawie wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="67fc2-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="67fc2-129">Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="67fc2-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="67fc2-130">podczas Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="67fc2-130">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="67fc2-131">podczas Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="67fc2-131">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="67fc2-132">podczas Wskaźnik do obiektu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , który reprezentuje bieżącą przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="67fc2-132">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="67fc2-133">podczas Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="67fc2-133">[in] The user name.</span></span> <span data-ttu-id="67fc2-134">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="67fc2-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="67fc2-135">podczas Hasło.</span><span class="sxs-lookup"><span data-stu-id="67fc2-135">[in] The password.</span></span> <span data-ttu-id="67fc2-136">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="67fc2-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="67fc2-137">podczas Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="67fc2-137">[in] The domain name of the user.</span></span> <span data-ttu-id="67fc2-138">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="67fc2-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="67fc2-139">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="67fc2-139">Return value</span></span>

<span data-ttu-id="67fc2-140">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="67fc2-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="67fc2-141">Stała</span><span class="sxs-lookup"><span data-stu-id="67fc2-141">Constant</span></span>  |<span data-ttu-id="67fc2-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="67fc2-142">Value</span></span>  |<span data-ttu-id="67fc2-143">Opis</span><span class="sxs-lookup"><span data-stu-id="67fc2-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="67fc2-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="67fc2-144">0x80041003</span></span> | <span data-ttu-id="67fc2-145">Użytkownik nie ma uprawnienia do wyświetlania jednej lub więcej klas, które funkcja może zwrócić.</span><span class="sxs-lookup"><span data-stu-id="67fc2-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="67fc2-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="67fc2-146">0x80041001</span></span> | <span data-ttu-id="67fc2-147">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="67fc2-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="67fc2-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="67fc2-148">0x80041008</span></span> | <span data-ttu-id="67fc2-149">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="67fc2-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="67fc2-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="67fc2-150">0x80041010</span></span> | <span data-ttu-id="67fc2-151">Zapytanie określa klasę, która nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="67fc2-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="67fc2-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="67fc2-152">0x80042002</span></span> | <span data-ttu-id="67fc2-153">Zażądano zbyt dużej dokładności dostarczania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="67fc2-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="67fc2-154">Należy określić większą tolerancję sondowania.</span><span class="sxs-lookup"><span data-stu-id="67fc2-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="67fc2-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="67fc2-155">0x80042001</span></span> | <span data-ttu-id="67fc2-156">Zapytanie żąda więcej informacji niż można zapewnić zarządzanie systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="67fc2-156">The query requests more information than Windows Management can provide.</span></span> <span data-ttu-id="67fc2-157">Ta `HRESULT` jest zwracana, gdy zapytanie zdarzenia powoduje żądanie sondowania wszystkich obiektów w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="67fc2-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="67fc2-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="67fc2-158">0x80041017</span></span> | <span data-ttu-id="67fc2-159">Zapytanie zawierało błąd składniowy.</span><span class="sxs-lookup"><span data-stu-id="67fc2-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="67fc2-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="67fc2-160">0x80041018</span></span> | <span data-ttu-id="67fc2-161">Żądany język kwerendy nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="67fc2-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="67fc2-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="67fc2-162">0x8004106c</span></span> | <span data-ttu-id="67fc2-163">Zapytanie jest zbyt złożone.</span><span class="sxs-lookup"><span data-stu-id="67fc2-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="67fc2-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="67fc2-164">0x80041006</span></span> | <span data-ttu-id="67fc2-165">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="67fc2-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="67fc2-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="67fc2-166">0x80041033</span></span> | <span data-ttu-id="67fc2-167">Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="67fc2-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="67fc2-168">Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="67fc2-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="67fc2-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="67fc2-169">0x80041015</span></span> | <span data-ttu-id="67fc2-170">Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="67fc2-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="67fc2-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="67fc2-171">0x80041058</span></span> | <span data-ttu-id="67fc2-172">Nie można przeanalizować zapytania.</span><span class="sxs-lookup"><span data-stu-id="67fc2-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="67fc2-173">0</span><span class="sxs-lookup"><span data-stu-id="67fc2-173">0</span></span> | <span data-ttu-id="67fc2-174">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="67fc2-174">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="67fc2-175">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67fc2-175">Remarks</span></span>

<span data-ttu-id="67fc2-176">Ta funkcja otacza wywołanie metody [IWbemServices:: ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) .</span><span class="sxs-lookup"><span data-stu-id="67fc2-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) method.</span></span>

<span data-ttu-id="67fc2-177">Po powrocie funkcji obiekt wywołujący okresowo przekazuje zwrócony obiekt `ppEnum` do [następnej](next.md) funkcji, aby sprawdzić, czy jakieś zdarzenia są dostępne.</span><span class="sxs-lookup"><span data-stu-id="67fc2-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="67fc2-178">Istnieją ograniczenia liczby `AND` i `OR` słów kluczowych, które mogą być używane w zapytaniach WQL.</span><span class="sxs-lookup"><span data-stu-id="67fc2-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="67fc2-179">Duża liczba słów kluczowych WQL używanych w złożonej kwerendzie może spowodować, że usługa WMI zwróci kod błędu `WBEM_E_QUOTA_VIOLATION` (lub 0x8004106c) jako wartość `HRESULT`ą.</span><span class="sxs-lookup"><span data-stu-id="67fc2-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="67fc2-180">Limit słów kluczowych WQL zależy od tego, jak złożona jest kwerenda.</span><span class="sxs-lookup"><span data-stu-id="67fc2-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="67fc2-181">Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="67fc2-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="67fc2-182">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67fc2-182">Requirements</span></span>

<span data-ttu-id="67fc2-183">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67fc2-183">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="67fc2-184">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="67fc2-184">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="67fc2-185">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="67fc2-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="67fc2-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67fc2-186">See also</span></span>

- [<span data-ttu-id="67fc2-187">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="67fc2-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
