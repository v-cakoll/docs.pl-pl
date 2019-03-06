---
title: Funkcja ExecQueryWmi (niezarządzany wykaz interfejsów API)
description: Funkcja ExecQueryWmi wykonuje zapytanie, aby pobrać obiekty.
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 402bbcb9ad5e462a55c5ec2716417f512f03ee19
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373221"
---
# <a name="execquerywmi-function"></a><span data-ttu-id="461eb-103">Funkcja ExecQueryWmi</span><span class="sxs-lookup"><span data-stu-id="461eb-103">ExecQueryWmi function</span></span>

<span data-ttu-id="461eb-104">Wykonuje zapytanie, aby pobrać obiekty.</span><span class="sxs-lookup"><span data-stu-id="461eb-104">Executes a query to retrieve objects.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="461eb-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="461eb-105">Syntax</span></span>

```cpp
HRESULT ExecQueryWmi (
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

## <a name="parameters"></a><span data-ttu-id="461eb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="461eb-106">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="461eb-107">[in] Ciąg z językiem prawidłowe zapytanie obsługiwane przez Windows Management.</span><span class="sxs-lookup"><span data-stu-id="461eb-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="461eb-108">Musi to być "WQL" akronim języka WMI Query Language.</span><span class="sxs-lookup"><span data-stu-id="461eb-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="461eb-109">[in] Tekst zapytania.</span><span class="sxs-lookup"><span data-stu-id="461eb-109">[in] The text of the query.</span></span> <span data-ttu-id="461eb-110">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="461eb-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="461eb-111">[in] Kombinacja flag, które mają wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="461eb-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="461eb-112">Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="461eb-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

| <span data-ttu-id="461eb-113">Stała</span><span class="sxs-lookup"><span data-stu-id="461eb-113">Constant</span></span> | <span data-ttu-id="461eb-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="461eb-114">Value</span></span>  | <span data-ttu-id="461eb-115">Opis</span><span class="sxs-lookup"><span data-stu-id="461eb-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="461eb-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="461eb-116">0x20000</span></span> | <span data-ttu-id="461eb-117">Jeśli zestaw, funkcja pobiera poprawionych kwalifikatorów, przechowywane w zlokalizowanych nazw ustawień regionalnych bieżącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="461eb-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="461eb-118">W przeciwnym razie zestawu, funkcja pobiera kwalifikatory przechowywanych w bezpośrednim przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="461eb-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="461eb-119">0x10</span><span class="sxs-lookup"><span data-stu-id="461eb-119">0x10</span></span> | <span data-ttu-id="461eb-120">Flaga powoduje, że wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="461eb-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="461eb-121">0x20</span><span class="sxs-lookup"><span data-stu-id="461eb-121">0x20</span></span> | <span data-ttu-id="461eb-122">Funkcja zwraca tylko do przodu modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="461eb-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="461eb-123">Zwykle tylko do przodu moduły wyliczające są realizowane szybciej i używać mniej pamięci niż moduły wyliczające konwencjonalnych, ale nie zezwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="461eb-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="461eb-124">0</span><span class="sxs-lookup"><span data-stu-id="461eb-124">0</span></span> | <span data-ttu-id="461eb-125">WMI zachowuje wskaźników do obiektów w wyliczeniu, dopóki ich wydaniu.</span><span class="sxs-lookup"><span data-stu-id="461eb-125">WMI retains pointers to objects in the enumeration until they are released.</span></span> |
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="461eb-126">0x100</span><span class="sxs-lookup"><span data-stu-id="461eb-126">0x100</span></span> | <span data-ttu-id="461eb-127">Zapewnia dowolnej zwracane obiekty mają wystarczającą ilość informacji w nich tak tej właściwości systemu, takie jak **__PATH**, **pobieranie właściwości __RELPATH**, i **__SERVER**, nie są `null`.</span><span class="sxs-lookup"><span data-stu-id="461eb-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="461eb-128">2</span><span class="sxs-lookup"><span data-stu-id="461eb-128">2</span></span> | <span data-ttu-id="461eb-129">Ta flaga jest używana do tworzenia prototypów.</span><span class="sxs-lookup"><span data-stu-id="461eb-129">This flag is used for prototyping.</span></span> <span data-ttu-id="461eb-130">Go nie jest wykonywane zapytanie, a zamiast tego zwraca obiekt, który wygląda jak obiekt wyniku typowe.</span><span class="sxs-lookup"><span data-stu-id="461eb-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="461eb-131">0x200</span><span class="sxs-lookup"><span data-stu-id="461eb-131">0x200</span></span> | <span data-ttu-id="461eb-132">Powoduje, że bezpośredni dostęp do dostawcy dla klasy określona bez względu na swoją klasą nadrzędną lub podklasy.</span><span class="sxs-lookup"><span data-stu-id="461eb-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="461eb-133">Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` uzyskać najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="461eb-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="461eb-134">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="461eb-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="461eb-135">W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy.</span><span class="sxs-lookup"><span data-stu-id="461eb-135">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="461eb-136">[out] Jeśli żaden błąd nie wystąpi, otrzymuje wskaźnik, aby moduł wyliczający, który umożliwia obiektowi wywołującemu, można pobrać wystąpień w zestawie wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="461eb-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="461eb-137">Zapytanie może mieć zestaw wyników z zerową wystąpień.</span><span class="sxs-lookup"><span data-stu-id="461eb-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="461eb-138">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="461eb-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="461eb-139">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="461eb-139">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="461eb-140">[in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="461eb-140">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="461eb-141">[in] Wskaźnik do [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) obiekt, który reprezentuje bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="461eb-141">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="461eb-142">[in] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="461eb-142">[in] The user name.</span></span> <span data-ttu-id="461eb-143">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="461eb-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="461eb-144">[in] Hasło.</span><span class="sxs-lookup"><span data-stu-id="461eb-144">[in] The password.</span></span> <span data-ttu-id="461eb-145">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="461eb-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="461eb-146">[in] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="461eb-146">[in] The domain name of the user.</span></span> <span data-ttu-id="461eb-147">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="461eb-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="461eb-148">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="461eb-148">Return value</span></span>

<span data-ttu-id="461eb-149">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="461eb-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="461eb-150">Stała</span><span class="sxs-lookup"><span data-stu-id="461eb-150">Constant</span></span>  |<span data-ttu-id="461eb-151">Wartość</span><span class="sxs-lookup"><span data-stu-id="461eb-151">Value</span></span>  |<span data-ttu-id="461eb-152">Opis</span><span class="sxs-lookup"><span data-stu-id="461eb-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="461eb-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="461eb-153">0x80041003</span></span> | <span data-ttu-id="461eb-154">Użytkownik nie ma uprawnień do wyświetlania przynajmniej jednej z klas, które może zwracać funkcji.</span><span class="sxs-lookup"><span data-stu-id="461eb-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="461eb-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="461eb-155">0x80041001</span></span> | <span data-ttu-id="461eb-156">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="461eb-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="461eb-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="461eb-157">0x80041008</span></span> | <span data-ttu-id="461eb-158">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="461eb-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="461eb-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="461eb-159">0x80041017</span></span> | <span data-ttu-id="461eb-160">Zapytania ma błąd składni.</span><span class="sxs-lookup"><span data-stu-id="461eb-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="461eb-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="461eb-161">0x80041018</span></span> | <span data-ttu-id="461eb-162">Żądany język kwerendy nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="461eb-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="461eb-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="461eb-163">0x8004106c</span></span> | <span data-ttu-id="461eb-164">Zapytanie jest zbyt złożony.</span><span class="sxs-lookup"><span data-stu-id="461eb-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="461eb-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="461eb-165">0x80041006</span></span> | <span data-ttu-id="461eb-166">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="461eb-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="461eb-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="461eb-167">0x80041033</span></span> | <span data-ttu-id="461eb-168">WMI został prawdopodobnie zatrzymane i ponowne uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="461eb-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="461eb-169">Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="461eb-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="461eb-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="461eb-170">0x80041015</span></span> | <span data-ttu-id="461eb-171">Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="461eb-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="461eb-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="461eb-172">0x80041002</span></span> | <span data-ttu-id="461eb-173">Zapytanie Określa klasę, która nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="461eb-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="461eb-174">0</span><span class="sxs-lookup"><span data-stu-id="461eb-174">0</span></span> | <span data-ttu-id="461eb-175">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="461eb-175">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="461eb-176">Uwagi</span><span class="sxs-lookup"><span data-stu-id="461eb-176">Remarks</span></span>

<span data-ttu-id="461eb-177">Ta funkcja zawija wywołanie do [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) metody.</span><span class="sxs-lookup"><span data-stu-id="461eb-177">This function wraps a call to the [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) method.</span></span>

<span data-ttu-id="461eb-178">Ta funkcja przetwarza zapytanie określone w `strQuery` parametru i tworzy moduł wyliczający, przez który obiekt wywołujący mogą uzyskiwać dostęp do wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="461eb-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="461eb-179">Moduł wyliczający jest wskaźnikiem do [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interfejsu; zapytanie wyniki są wystąpieniami typów obiektów klas udostępniane za pośrednictwem [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="461eb-179">The enumerator is a pointer to an [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; the query results are instances of class objects made available through the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.</span></span>

<span data-ttu-id="461eb-180">Istnieją limity liczby `AND` i `OR` słów kluczowych, które mogą być używane w kwerendach WQL.</span><span class="sxs-lookup"><span data-stu-id="461eb-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="461eb-181">Dużej liczby WQL słowa kluczowe używane w złożonych kwerend może spowodować, że usługi WMI do zwrócenia `WBEM_E_QUOTA_VIOLATION` (lub 0x8004106c) kod błędu, jako `HRESULT` wartość.</span><span class="sxs-lookup"><span data-stu-id="461eb-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="461eb-182">Limit słowa kluczowe języka WQL zależy od tego, jak złożona jest zapytanie.</span><span class="sxs-lookup"><span data-stu-id="461eb-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="461eb-183">Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="461eb-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="461eb-184">Wymagania</span><span class="sxs-lookup"><span data-stu-id="461eb-184">Requirements</span></span>

<span data-ttu-id="461eb-185">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="461eb-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="461eb-186">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="461eb-186">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="461eb-187">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="461eb-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="461eb-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="461eb-188">See also</span></span>

- [<span data-ttu-id="461eb-189">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="461eb-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)