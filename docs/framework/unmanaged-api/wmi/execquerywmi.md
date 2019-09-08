---
title: ExecQueryWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja ExecQueryWmi wykonuje zapytanie w celu pobrania obiektów.
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
ms.openlocfilehash: b8547d306819e85b838f1160d9912dd43e42f2f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798691"
---
# <a name="execquerywmi-function"></a><span data-ttu-id="79ab6-103">ExecQueryWmi, funkcja</span><span class="sxs-lookup"><span data-stu-id="79ab6-103">ExecQueryWmi function</span></span>

<span data-ttu-id="79ab6-104">Wykonuje zapytanie w celu pobrania obiektów.</span><span class="sxs-lookup"><span data-stu-id="79ab6-104">Executes a query to retrieve objects.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="79ab6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="79ab6-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="79ab6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="79ab6-106">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="79ab6-107">podczas Ciąg z prawidłowym językiem zapytań obsługiwanym przez zarządzanie systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="79ab6-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="79ab6-108">Musi to być "WQL", akronim dla język zapytań usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="79ab6-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="79ab6-109">podczas Tekst zapytania.</span><span class="sxs-lookup"><span data-stu-id="79ab6-109">[in] The text of the query.</span></span> <span data-ttu-id="79ab6-110">Ten parametr nie może `null`być.</span><span class="sxs-lookup"><span data-stu-id="79ab6-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="79ab6-111">podczas Kombinacja flag mających wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="79ab6-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="79ab6-112">Poniższe wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="79ab6-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

| <span data-ttu-id="79ab6-113">Stała</span><span class="sxs-lookup"><span data-stu-id="79ab6-113">Constant</span></span> | <span data-ttu-id="79ab6-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="79ab6-114">Value</span></span>  | <span data-ttu-id="79ab6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="79ab6-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="79ab6-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="79ab6-116">0x20000</span></span> | <span data-ttu-id="79ab6-117">W przypadku ustawienia funkcja pobiera zmienione kwalifikatory przechowywane w zlokalizowanej przestrzeni nazw ustawień regionalnych bieżącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="79ab6-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="79ab6-118">Jeśli nie zostanie ustawiona, funkcja pobiera tylko kwalifikatory przechowywane w bezpośredniej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="79ab6-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="79ab6-119">0x10</span><span class="sxs-lookup"><span data-stu-id="79ab6-119">0x10</span></span> | <span data-ttu-id="79ab6-120">Flaga powoduje wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="79ab6-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="79ab6-121">0x20</span><span class="sxs-lookup"><span data-stu-id="79ab6-121">0x20</span></span> | <span data-ttu-id="79ab6-122">Funkcja zwraca moduł wyliczający tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="79ab6-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="79ab6-123">Zazwyczaj moduły wyliczające tylko do przodu są szybsze i używają mniej pamięci niż konwencjonalne moduły wyliczające, ale nie pozwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="79ab6-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="79ab6-124">0</span><span class="sxs-lookup"><span data-stu-id="79ab6-124">0</span></span> | <span data-ttu-id="79ab6-125">Usługa WMI zachowuje wskaźniki do obiektów w wyliczeniu do momentu ich zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="79ab6-125">WMI retains pointers to objects in the enumeration until they are released.</span></span> |
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="79ab6-126">0x100</span><span class="sxs-lookup"><span data-stu-id="79ab6-126">0x100</span></span> | <span data-ttu-id="79ab6-127">Zapewnia, że wszystkie zwrócone obiekty mają wystarczającą ilość informacji, tak aby `null`nie były to właściwości systemu, takie jak **__PATH**, **__RELPATH**i **__SERVER**.</span><span class="sxs-lookup"><span data-stu-id="79ab6-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="79ab6-128">2</span><span class="sxs-lookup"><span data-stu-id="79ab6-128">2</span></span> | <span data-ttu-id="79ab6-129">Ta flaga jest używana do tworzenia prototypów.</span><span class="sxs-lookup"><span data-stu-id="79ab6-129">This flag is used for prototyping.</span></span> <span data-ttu-id="79ab6-130">Nie wykonuje zapytania i zamiast tego zwraca obiekt, który wygląda jak typowy obiekt wynikowy.</span><span class="sxs-lookup"><span data-stu-id="79ab6-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="79ab6-131">0x200</span><span class="sxs-lookup"><span data-stu-id="79ab6-131">0x200</span></span> | <span data-ttu-id="79ab6-132">Powoduje bezpośredni dostęp do dostawcy dla określonej klasy bez względu na jego klasę nadrzędną ani żadnej podklasy.</span><span class="sxs-lookup"><span data-stu-id="79ab6-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="79ab6-133">Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` zapewniają najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="79ab6-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="79ab6-134">podczas Zazwyczaj ta wartość to `null`.</span><span class="sxs-lookup"><span data-stu-id="79ab6-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="79ab6-135">W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane klasy.</span><span class="sxs-lookup"><span data-stu-id="79ab6-135">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="79ab6-136">określoną Jeśli błąd nie wystąpi, otrzymuje wskaźnik do modułu wyliczającego, który umożliwia obiektowi wywołującemu pobieranie wystąpień w zestawie wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="79ab6-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="79ab6-137">Zapytanie może mieć zestaw wyników o zerowej instancji.</span><span class="sxs-lookup"><span data-stu-id="79ab6-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="79ab6-138">Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="79ab6-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="79ab6-139">podczas Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="79ab6-139">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="79ab6-140">podczas Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="79ab6-140">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="79ab6-141">podczas Wskaźnik do obiektu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , który reprezentuje bieżącą przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="79ab6-141">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="79ab6-142">podczas Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="79ab6-142">[in] The user name.</span></span> <span data-ttu-id="79ab6-143">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="79ab6-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="79ab6-144">podczas Hasło.</span><span class="sxs-lookup"><span data-stu-id="79ab6-144">[in] The password.</span></span> <span data-ttu-id="79ab6-145">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="79ab6-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="79ab6-146">podczas Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="79ab6-146">[in] The domain name of the user.</span></span> <span data-ttu-id="79ab6-147">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="79ab6-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="79ab6-148">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="79ab6-148">Return value</span></span>

<span data-ttu-id="79ab6-149">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="79ab6-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="79ab6-150">Stała</span><span class="sxs-lookup"><span data-stu-id="79ab6-150">Constant</span></span>  |<span data-ttu-id="79ab6-151">Wartość</span><span class="sxs-lookup"><span data-stu-id="79ab6-151">Value</span></span>  |<span data-ttu-id="79ab6-152">Opis</span><span class="sxs-lookup"><span data-stu-id="79ab6-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="79ab6-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="79ab6-153">0x80041003</span></span> | <span data-ttu-id="79ab6-154">Użytkownik nie ma uprawnienia do wyświetlania jednej lub więcej klas, które funkcja może zwrócić.</span><span class="sxs-lookup"><span data-stu-id="79ab6-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="79ab6-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="79ab6-155">0x80041001</span></span> | <span data-ttu-id="79ab6-156">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="79ab6-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="79ab6-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="79ab6-157">0x80041008</span></span> | <span data-ttu-id="79ab6-158">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="79ab6-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="79ab6-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="79ab6-159">0x80041017</span></span> | <span data-ttu-id="79ab6-160">Zapytanie zawierało błąd składniowy.</span><span class="sxs-lookup"><span data-stu-id="79ab6-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="79ab6-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="79ab6-161">0x80041018</span></span> | <span data-ttu-id="79ab6-162">Żądany język kwerendy nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="79ab6-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="79ab6-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="79ab6-163">0x8004106c</span></span> | <span data-ttu-id="79ab6-164">Zapytanie jest zbyt złożone.</span><span class="sxs-lookup"><span data-stu-id="79ab6-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="79ab6-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="79ab6-165">0x80041006</span></span> | <span data-ttu-id="79ab6-166">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="79ab6-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="79ab6-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="79ab6-167">0x80041033</span></span> | <span data-ttu-id="79ab6-168">Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="79ab6-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="79ab6-169">Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="79ab6-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="79ab6-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="79ab6-170">0x80041015</span></span> | <span data-ttu-id="79ab6-171">Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="79ab6-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="79ab6-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="79ab6-172">0x80041002</span></span> | <span data-ttu-id="79ab6-173">Zapytanie określa klasę, która nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="79ab6-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="79ab6-174">0</span><span class="sxs-lookup"><span data-stu-id="79ab6-174">0</span></span> | <span data-ttu-id="79ab6-175">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="79ab6-175">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="79ab6-176">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79ab6-176">Remarks</span></span>

<span data-ttu-id="79ab6-177">Ta funkcja otacza wywołanie metody [IWbemServices:: ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) .</span><span class="sxs-lookup"><span data-stu-id="79ab6-177">This function wraps a call to the [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) method.</span></span>

<span data-ttu-id="79ab6-178">Ta funkcja przetwarza zapytanie określone w `strQuery` parametrze i tworzy moduł wyliczający, za pomocą którego obiekt wywołujący może uzyskać dostęp do wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="79ab6-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="79ab6-179">Moduł wyliczający jest wskaźnikiem do interfejsu [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) ; wyniki zapytania są wystąpieniami obiektów klasy udostępnianych za pomocą interfejsu [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="79ab6-179">The enumerator is a pointer to an [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; the query results are instances of class objects made available through the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.</span></span>

<span data-ttu-id="79ab6-180">Istnieją limity dotyczące liczby `AND` i `OR` słów kluczowych, które mogą być używane w zapytaniach WQL.</span><span class="sxs-lookup"><span data-stu-id="79ab6-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="79ab6-181">Duża liczba słów kluczowych WQL używanych w złożonej kwerendzie może spowodować, że usługa WMI `WBEM_E_QUOTA_VIOLATION` zwróci kod błędu (lub 0x8004106c) `HRESULT` jako wartość.</span><span class="sxs-lookup"><span data-stu-id="79ab6-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="79ab6-182">Limit słów kluczowych WQL zależy od tego, jak złożona jest kwerenda.</span><span class="sxs-lookup"><span data-stu-id="79ab6-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="79ab6-183">Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="79ab6-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="79ab6-184">Wymagania</span><span class="sxs-lookup"><span data-stu-id="79ab6-184">Requirements</span></span>

<span data-ttu-id="79ab6-185">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79ab6-185">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="79ab6-186">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="79ab6-186">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="79ab6-187">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="79ab6-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="79ab6-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79ab6-188">See also</span></span>

- [<span data-ttu-id="79ab6-189">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="79ab6-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
