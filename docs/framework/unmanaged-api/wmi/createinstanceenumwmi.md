---
title: Funkcja CreateInstanceEnumWmi (niezarządzany wykaz interfejsów API)
description: Funkcja CreateInstanceEnumWmi zwraca moduł wyliczający zawierający wystąpień określonej klasy, które spełniają kryteria wyboru.
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a1d082cae19bd83c90e063d841a0c9e4602bc40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040706"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="f0d70-103">CreateInstanceEnumWmi — funkcja</span><span class="sxs-lookup"><span data-stu-id="f0d70-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="f0d70-104">Zwraca moduł wyliczający, który zwraca wystąpienia określonej klasy, spełniających kryteria określonego zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="f0d70-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f0d70-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0d70-105">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="f0d70-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0d70-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="f0d70-107">[in] Nazwa klasy, dla którego wystąpienia są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="f0d70-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="f0d70-108">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="f0d70-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="f0d70-109">[in] Kombinacja flag, które mają wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0d70-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="f0d70-110">Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="f0d70-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f0d70-111">Stała</span><span class="sxs-lookup"><span data-stu-id="f0d70-111">Constant</span></span>  |<span data-ttu-id="f0d70-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="f0d70-112">Value</span></span>  |<span data-ttu-id="f0d70-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f0d70-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="f0d70-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="f0d70-114">0x20000</span></span> | <span data-ttu-id="f0d70-115">Jeśli zestaw, funkcja pobiera poprawionych kwalifikatorów, przechowywane w zlokalizowanych nazw ustawień regionalnych bieżącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="f0d70-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="f0d70-116">W przeciwnym razie zestawu, funkcja pobiera kwalifikatory przechowywanych w bezpośrednim przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f0d70-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="f0d70-117">0</span><span class="sxs-lookup"><span data-stu-id="f0d70-117">0</span></span> | <span data-ttu-id="f0d70-118">Wyliczanie obejmuje to i podklasami w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="f0d70-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="f0d70-119">1</span><span class="sxs-lookup"><span data-stu-id="f0d70-119">1</span></span> | <span data-ttu-id="f0d70-120">Wyliczenie zawiera tylko czyste wystąpienia tej klasy i nie obejmuje wszystkich wystąpień podklas, które dostarczają właściwości nie można odnaleźć w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="f0d70-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="f0d70-121">0x10</span><span class="sxs-lookup"><span data-stu-id="f0d70-121">0x10</span></span> | <span data-ttu-id="f0d70-122">Flaga powoduje, że wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="f0d70-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="f0d70-123">0x20</span><span class="sxs-lookup"><span data-stu-id="f0d70-123">0x20</span></span> | <span data-ttu-id="f0d70-124">Funkcja zwraca tylko do przodu modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="f0d70-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="f0d70-125">Zwykle tylko do przodu moduły wyliczające są realizowane szybciej i używać mniej pamięci niż moduły wyliczające konwencjonalnych, ale nie zezwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="f0d70-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="f0d70-126">0</span><span class="sxs-lookup"><span data-stu-id="f0d70-126">0</span></span> | <span data-ttu-id="f0d70-127">WMI zachowuje wskaźników do obiektów w wyliczeniu, dopóki ich wydaniu.</span><span class="sxs-lookup"><span data-stu-id="f0d70-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="f0d70-128">Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` uzyskać najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="f0d70-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="f0d70-129">[in] Ta wartość jest zazwyczaj `null`.</span><span class="sxs-lookup"><span data-stu-id="f0d70-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="f0d70-130">W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienia, która może być używana przez dostawcę, który dostarcza żądanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f0d70-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="f0d70-131">[out] Otrzymuje wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="f0d70-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="f0d70-132">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f0d70-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="f0d70-133">[in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="f0d70-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="f0d70-134">[in] Wskaźnik do [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) obiekt, który reprezentuje bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f0d70-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="f0d70-135">[in] Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f0d70-135">[in] The user name.</span></span> <span data-ttu-id="f0d70-136">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f0d70-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="f0d70-137">[in] Hasło.</span><span class="sxs-lookup"><span data-stu-id="f0d70-137">[in] The password.</span></span> <span data-ttu-id="f0d70-138">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f0d70-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="f0d70-139">[in] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f0d70-139">[in] The domain name of the user.</span></span> <span data-ttu-id="f0d70-140">Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f0d70-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="f0d70-141">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f0d70-141">Return value</span></span>

<span data-ttu-id="f0d70-142">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="f0d70-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f0d70-143">Stała</span><span class="sxs-lookup"><span data-stu-id="f0d70-143">Constant</span></span>  |<span data-ttu-id="f0d70-144">Wartość</span><span class="sxs-lookup"><span data-stu-id="f0d70-144">Value</span></span>  |<span data-ttu-id="f0d70-145">Opis</span><span class="sxs-lookup"><span data-stu-id="f0d70-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="f0d70-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="f0d70-146">0x80041003</span></span> | <span data-ttu-id="f0d70-147">Użytkownik nie ma uprawnień do wyświetlania wystąpienia określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="f0d70-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="f0d70-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f0d70-148">0x80041001</span></span> | <span data-ttu-id="f0d70-149">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="f0d70-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="f0d70-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="f0d70-150">0x80041010</span></span> | <span data-ttu-id="f0d70-151">`strFilter` nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f0d70-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f0d70-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f0d70-152">0x80041008</span></span> | <span data-ttu-id="f0d70-153">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f0d70-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f0d70-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f0d70-154">0x80041006</span></span> | <span data-ttu-id="f0d70-155">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="f0d70-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="f0d70-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="f0d70-156">0x80041033</span></span> | <span data-ttu-id="f0d70-157">WMI został prawdopodobnie zatrzymane i ponowne uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="f0d70-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="f0d70-158">Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie.</span><span class="sxs-lookup"><span data-stu-id="f0d70-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="f0d70-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="f0d70-159">0x80041015</span></span> | <span data-ttu-id="f0d70-160">Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="f0d70-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f0d70-161">0</span><span class="sxs-lookup"><span data-stu-id="f0d70-161">0</span></span> | <span data-ttu-id="f0d70-162">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f0d70-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="f0d70-163">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0d70-163">Remarks</span></span>

<span data-ttu-id="f0d70-164">Ta funkcja zawija wywołanie do [metodę IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) metody.</span><span class="sxs-lookup"><span data-stu-id="f0d70-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="f0d70-165">Należy pamiętać, że zwrócony moduł wyliczający może mieć żadnego elementu.</span><span class="sxs-lookup"><span data-stu-id="f0d70-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="f0d70-166">Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0d70-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0d70-167">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0d70-167">Requirements</span></span>

<span data-ttu-id="f0d70-168">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0d70-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="f0d70-169">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f0d70-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="f0d70-170">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f0d70-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f0d70-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0d70-171">See also</span></span>

- [<span data-ttu-id="f0d70-172">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="f0d70-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)