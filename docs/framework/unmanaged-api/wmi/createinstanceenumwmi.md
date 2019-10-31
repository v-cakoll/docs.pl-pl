---
title: CreateInstanceEnumWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja CreateInstanceEnumWmi zwraca moduł wyliczający zawierający wystąpienia określonej klasy, które spełniają kryteria wyboru.
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
ms.openlocfilehash: 9ffa718be0e8b67471fdf8cb277df201388d2840
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130403"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="bc7b1-103">CreateInstanceEnumWmi, funkcja</span><span class="sxs-lookup"><span data-stu-id="bc7b1-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="bc7b1-104">Zwraca moduł wyliczający, który zwraca wystąpienia określonej klasy, które spełniają określone kryteria wyboru.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bc7b1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc7b1-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="bc7b1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc7b1-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="bc7b1-107">podczas Nazwa klasy, dla której wystąpienia są żądane.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="bc7b1-108">Ten parametr nie może być `null`.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="bc7b1-109">podczas Kombinacja flag mających wpływ na zachowanie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="bc7b1-110">Poniższe wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="bc7b1-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bc7b1-111">Stała</span><span class="sxs-lookup"><span data-stu-id="bc7b1-111">Constant</span></span>  |<span data-ttu-id="bc7b1-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="bc7b1-112">Value</span></span>  |<span data-ttu-id="bc7b1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bc7b1-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="bc7b1-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="bc7b1-114">0x20000</span></span> | <span data-ttu-id="bc7b1-115">W przypadku ustawienia funkcja pobiera zmienione kwalifikatory przechowywane w zlokalizowanej przestrzeni nazw ustawień regionalnych bieżącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="bc7b1-116">Jeśli nie zostanie ustawiona, funkcja pobiera tylko kwalifikatory przechowywane w bezpośredniej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="bc7b1-117">0</span><span class="sxs-lookup"><span data-stu-id="bc7b1-117">0</span></span> | <span data-ttu-id="bc7b1-118">Wyliczenie zawiera te i wszystkie podklasy w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="bc7b1-119">1</span><span class="sxs-lookup"><span data-stu-id="bc7b1-119">1</span></span> | <span data-ttu-id="bc7b1-120">Wyliczenie obejmuje tylko czyste wystąpienia tej klasy i wyklucza wszystkie wystąpienia podklas, które nie znalazły właściwości w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="bc7b1-121">0x10</span><span class="sxs-lookup"><span data-stu-id="bc7b1-121">0x10</span></span> | <span data-ttu-id="bc7b1-122">Flaga powoduje wywołanie półsynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="bc7b1-123">0x20</span><span class="sxs-lookup"><span data-stu-id="bc7b1-123">0x20</span></span> | <span data-ttu-id="bc7b1-124">Funkcja zwraca moduł wyliczający tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="bc7b1-125">Zazwyczaj moduły wyliczające tylko do przodu są szybsze i używają mniej pamięci niż konwencjonalne moduły wyliczające, ale nie pozwalają na wywołania [klonowania](clone.md).</span><span class="sxs-lookup"><span data-stu-id="bc7b1-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="bc7b1-126">0</span><span class="sxs-lookup"><span data-stu-id="bc7b1-126">0</span></span> | <span data-ttu-id="bc7b1-127">Usługa WMI zachowuje wskaźniki do obiektów w wyliczeniu do momentu ich zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="bc7b1-128">Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` w celu uzyskania najlepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="bc7b1-129">podczas Zazwyczaj ta wartość jest `null`.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="bc7b1-130">W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="bc7b1-131">określoną Odbiera wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="bc7b1-132">podczas Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="bc7b1-133">podczas Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="bc7b1-134">podczas Wskaźnik do obiektu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , który reprezentuje bieżącą przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="bc7b1-135">podczas Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-135">[in] The user name.</span></span> <span data-ttu-id="bc7b1-136">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="bc7b1-137">podczas Hasło.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-137">[in] The password.</span></span> <span data-ttu-id="bc7b1-138">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="bc7b1-139">podczas Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-139">[in] The domain name of the user.</span></span> <span data-ttu-id="bc7b1-140">Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="bc7b1-141">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bc7b1-141">Return value</span></span>

<span data-ttu-id="bc7b1-142">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="bc7b1-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bc7b1-143">Stała</span><span class="sxs-lookup"><span data-stu-id="bc7b1-143">Constant</span></span>  |<span data-ttu-id="bc7b1-144">Wartość</span><span class="sxs-lookup"><span data-stu-id="bc7b1-144">Value</span></span>  |<span data-ttu-id="bc7b1-145">Opis</span><span class="sxs-lookup"><span data-stu-id="bc7b1-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="bc7b1-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="bc7b1-146">0x80041003</span></span> | <span data-ttu-id="bc7b1-147">Użytkownik nie ma uprawnienia do wyświetlania wystąpień określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="bc7b1-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bc7b1-148">0x80041001</span></span> | <span data-ttu-id="bc7b1-149">Wystąpił nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="bc7b1-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="bc7b1-150">0x80041010</span></span> | <span data-ttu-id="bc7b1-151">`strFilter` nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bc7b1-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bc7b1-152">0x80041008</span></span> | <span data-ttu-id="bc7b1-153">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bc7b1-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bc7b1-154">0x80041006</span></span> | <span data-ttu-id="bc7b1-155">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="bc7b1-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="bc7b1-156">0x80041033</span></span> | <span data-ttu-id="bc7b1-157">Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="bc7b1-158">Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="bc7b1-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="bc7b1-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="bc7b1-159">0x80041015</span></span> | <span data-ttu-id="bc7b1-160">Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="bc7b1-161">0</span><span class="sxs-lookup"><span data-stu-id="bc7b1-161">0</span></span> | <span data-ttu-id="bc7b1-162">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="bc7b1-163">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc7b1-163">Remarks</span></span>

<span data-ttu-id="bc7b1-164">Ta funkcja otacza wywołanie metody [IWbemServices:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) .</span><span class="sxs-lookup"><span data-stu-id="bc7b1-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="bc7b1-165">Zwróć uwagę, że zwrócony moduł wyliczający może mieć elementy zerowe.</span><span class="sxs-lookup"><span data-stu-id="bc7b1-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="bc7b1-166">Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="bc7b1-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="bc7b1-167">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc7b1-167">Requirements</span></span>

<span data-ttu-id="bc7b1-168">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc7b1-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="bc7b1-169">**Nagłówek:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="bc7b1-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="bc7b1-170">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bc7b1-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bc7b1-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc7b1-171">See also</span></span>

- [<span data-ttu-id="bc7b1-172">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="bc7b1-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
