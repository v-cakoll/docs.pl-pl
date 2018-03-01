---
title: "Funkcja ExecQueryWmi (niezarządzany wykaz interfejsów API)"
description: "Funkcja ExecQueryWmi wykonuje zapytanie w celu pobrania obiektów."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 872109cb0472a8404c492c2867429fe783f898eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="execquerywmi-function"></a><span data-ttu-id="6e3fa-103">Funkcja ExecQueryWmi</span><span class="sxs-lookup"><span data-stu-id="6e3fa-103">ExecQueryWmi function</span></span>
<span data-ttu-id="6e3fa-104">Wykonuje zapytanie w celu pobrania obiektów.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-104">Executes a query to retrieve objects.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6e3fa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e3fa-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="6e3fa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e3fa-106">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="6e3fa-107">[in] Ciąg z prawidłowego zapytania języka obsługiwanego przez zarządzanie systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="6e3fa-108">Musi być "WQL" akronim język zapytań usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="6e3fa-109">[in] Tekst zapytania.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-109">[in] The text of the query.</span></span> <span data-ttu-id="6e3fa-110">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-110">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="6e3fa-111">[in] Kombinacja flag, które wpływają na działanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="6e3fa-112">Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="6e3fa-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

| <span data-ttu-id="6e3fa-113">Stała</span><span class="sxs-lookup"><span data-stu-id="6e3fa-113">Constant</span></span> | <span data-ttu-id="6e3fa-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="6e3fa-114">Value</span></span>  | <span data-ttu-id="6e3fa-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6e3fa-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="6e3fa-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="6e3fa-116">0x20000</span></span> | <span data-ttu-id="6e3fa-117">Jeśli zestaw, funkcja pobiera poprawionych kwalifikatorów przechowywane w zlokalizowanych nazw ustawień regionalnych bieżącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="6e3fa-118">Jeśli nie zestawu, funkcja pobiera tylko kwalifikatory przechowywane w przestrzeni nazw bezpośrednim.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="6e3fa-119">0x10</span><span class="sxs-lookup"><span data-stu-id="6e3fa-119">0x10</span></span> | <span data-ttu-id="6e3fa-120">Flaga powoduje Półsynchroniczne wywołania.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="6e3fa-121">0x20</span><span class="sxs-lookup"><span data-stu-id="6e3fa-121">0x20</span></span> | <span data-ttu-id="6e3fa-122">Funkcja zwraca tylko do przodu modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="6e3fa-123">Zwykle tylko do przodu moduły wyliczające są szybsze i używają mniej pamięci niż wyliczenia z konwencjonalnej, ale nie zezwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="6e3fa-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="6e3fa-124">0</span><span class="sxs-lookup"><span data-stu-id="6e3fa-124">0</span></span> | <span data-ttu-id="6e3fa-125">WMI zachowuje wskaźników do obiektów w enumration, dopóki ich wydania.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-125">WMI retains pointers to objects in the enumration until they are released.</span></span> | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="6e3fa-126">0x100</span><span class="sxs-lookup"><span data-stu-id="6e3fa-126">0x100</span></span> | <span data-ttu-id="6e3fa-127">Zapewnia żadnego zwracane obiekty mają wystarczającą ilość informacji w nich sposób tej właściwości systemu, takich jak **__PATH**, **pobieranie właściwości __RELPATH**, i **__SERVER**, nie są `null`.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="6e3fa-128">2</span><span class="sxs-lookup"><span data-stu-id="6e3fa-128">2</span></span> | <span data-ttu-id="6e3fa-129">Ta flaga jest wykorzystywana do tworzenia prototypów.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-129">This flag is used for prototyping.</span></span> <span data-ttu-id="6e3fa-130">Nie wykonuj zapytania, a zamiast tego zwraca obiekt, który wygląda jak obiekt wyniku typowych.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="6e3fa-131">0x200</span><span class="sxs-lookup"><span data-stu-id="6e3fa-131">0x200</span></span> | <span data-ttu-id="6e3fa-132">Przyczyny bezpośredni dostęp do dostawcy dla klasy określonej niezależnie od swojej klasy nadrzędnej lub podklasy.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="6e3fa-133">Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="6e3fa-134">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="6e3fa-135">W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-135">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="6e3fa-136">[out] Jeśli nie występują błędy, uzyskuje wskaźnik do moduł wyliczający, który umożliwia obiekt wywołujący, aby pobrać wystąpień w zestawie wyników kwerendy.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="6e3fa-137">Zapytania mogą mieć zestaw wyników z wystąpień zero.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="6e3fa-138">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="6e3fa-139">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-139">[in] The authorization level.</span></span>

<span data-ttu-id="6e3fa-140">`impLevel`[in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-140">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="6e3fa-141">[in] Wskaźnik do [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) obiekt, który reprezentuje bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-141">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="6e3fa-142">[in] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-142">[in] The user name.</span></span> <span data-ttu-id="6e3fa-143">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="6e3fa-144">[in] Hasło.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-144">[in] The password.</span></span> <span data-ttu-id="6e3fa-145">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="6e3fa-146">[in] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-146">[in] The domain name of the user.</span></span> <span data-ttu-id="6e3fa-147">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="6e3fa-148">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6e3fa-148">Return value</span></span>

<span data-ttu-id="6e3fa-149">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="6e3fa-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6e3fa-150">Stała</span><span class="sxs-lookup"><span data-stu-id="6e3fa-150">Constant</span></span>  |<span data-ttu-id="6e3fa-151">Wartość</span><span class="sxs-lookup"><span data-stu-id="6e3fa-151">Value</span></span>  |<span data-ttu-id="6e3fa-152">Opis</span><span class="sxs-lookup"><span data-stu-id="6e3fa-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="6e3fa-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="6e3fa-153">0x80041003</span></span> | <span data-ttu-id="6e3fa-154">Użytkownik nie ma uprawnień do wyświetlania przynajmniej jednej z klas, które może zwracać funkcji.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="6e3fa-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6e3fa-155">0x80041001</span></span> | <span data-ttu-id="6e3fa-156">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6e3fa-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6e3fa-157">0x80041008</span></span> | <span data-ttu-id="6e3fa-158">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="6e3fa-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="6e3fa-159">0x80041017</span></span> | <span data-ttu-id="6e3fa-160">Zapytania wystąpił błąd składni.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="6e3fa-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="6e3fa-161">0x80041018</span></span> | <span data-ttu-id="6e3fa-162">Żądany język kwerendy nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="6e3fa-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="6e3fa-163">0x8004106c</span></span> | <span data-ttu-id="6e3fa-164">Zapytanie jest zbyt złożony.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6e3fa-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6e3fa-165">0x80041006</span></span> | <span data-ttu-id="6e3fa-166">Za mało pamięci jest dostępna do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="6e3fa-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="6e3fa-167">0x80041033</span></span> | <span data-ttu-id="6e3fa-168">Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="6e3fa-169">Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="6e3fa-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="6e3fa-170">0x80041015</span></span> | <span data-ttu-id="6e3fa-171">Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="6e3fa-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="6e3fa-172">0x80041002</span></span> | <span data-ttu-id="6e3fa-173">Kwerenda Określa klasę, która nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="6e3fa-174">0</span><span class="sxs-lookup"><span data-stu-id="6e3fa-174">0</span></span> | <span data-ttu-id="6e3fa-175">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-175">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="6e3fa-176">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e3fa-176">Remarks</span></span>

<span data-ttu-id="6e3fa-177">Ta funkcja jest zawijana wywołanie [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-177">This function wraps a call to the [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="6e3fa-178">Ta funkcja przetwarza zapytanie określone w `strQuery` parametru i tworzy moduł wyliczający, przez który wywołującego mogą uzyskiwać dostęp do wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="6e3fa-179">Moduł wyliczający jest wskaźnik do [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interfejsu; zapytanie wyniki są wystąpieniami klasy obiektów dostępne za pośrednictwem [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-179">The enumerator is a pointer to an [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interface; the query results are instances of class objects made available through the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interface.</span></span>

<span data-ttu-id="6e3fa-180">Istnieją ograniczenia liczby `AND` i `OR` słów kluczowych, które mogą być używane w zapytaniach WQL.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="6e3fa-181">Dużą liczbą słów kluczowych języka WQL używanych w zapytaniu złożonych może spowodować WMI do zwrócenia `WBEM_E_QUOTA_VIOLATION` (lub 0x8004106c) kod błędu jako `HRESULT` wartość.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="6e3fa-182">Limit słów kluczowych języka WQL zależy od tego, jak złożoność zapytanie jest.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="6e3fa-183">Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="6e3fa-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="6e3fa-184">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e3fa-184">Requirements</span></span>  
 <span data-ttu-id="6e3fa-185">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e3fa-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e3fa-186">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6e3fa-186">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6e3fa-187">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6e3fa-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3fa-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e3fa-188">See also</span></span>  
[<span data-ttu-id="6e3fa-189">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="6e3fa-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
