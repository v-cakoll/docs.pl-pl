---
title: ConnectServerWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja ConnectServerWmi używa modelu DCOM do utworzenia połączenia z przestrzenią nazw usługi WMI.
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ebb268dcee877f4e9aea0c88852333897030dd1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798755"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="bf1c0-103">ConnectServerWmi, funkcja</span><span class="sxs-lookup"><span data-stu-id="bf1c0-103">ConnectServerWmi function</span></span>

<span data-ttu-id="bf1c0-104">Tworzy połączenie za pomocą modelu DCOM do przestrzeni nazw usługi WMI na określonym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bf1c0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf1c0-105">Syntax</span></span>

```cpp
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel,
   [in] DWORD              authLevel
);
```

## <a name="parameters"></a><span data-ttu-id="bf1c0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf1c0-106">Parameters</span></span>

`strNetworkResource`\
<span data-ttu-id="bf1c0-107">podczas Wskaźnik na prawidłowy `BSTR` , który zawiera ścieżkę obiektu poprawnej przestrzeni nazw usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-107">[in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="bf1c0-108">Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-108">See the [Remarks](#remarks) section for more information.</span></span>

`strUser`\
<span data-ttu-id="bf1c0-109">podczas Wskaźnik do prawidłowego `BSTR` , który zawiera nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-109">[in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="bf1c0-110">`null` Wartość wskazuje bieżący kontekst zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="bf1c0-111">Jeśli użytkownik należy do innej domeny niż bieżąca, `strUser` może również zawierać nazwę domeny i użytkownika rozdzieloną ukośnikiem odwrotnym.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="bf1c0-112">`strUser`może być również w formacie głównej nazwy użytkownika (UPN), np `userName@domainName`.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-112">`strUser` can also be in user principal name (UPN) format, such as `userName@domainName`.</span></span> <span data-ttu-id="bf1c0-113">Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-113">See the [Remarks](#remarks) section for more information.</span></span>

`strPassword`\
<span data-ttu-id="bf1c0-114">podczas Wskaźnik do prawidłowego `BSTR` , który zawiera hasło.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-114">[in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="bf1c0-115">`null` Wskazuje bieżący kontekst zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="bf1c0-116">Pusty ciąg ("") wskazuje prawidłowe hasło o zerowej długości.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-116">An empty string ("") indicates a valid zero-length password.</span></span>

`strLocale`\
<span data-ttu-id="bf1c0-117">podczas Wskaźnik do prawidłowego `BSTR` , który wskazuje prawidłowe ustawienia regionalne do pobierania informacji.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-117">[in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="bf1c0-118">W przypadku identyfikatorów ustawień regionalnych firmy Microsoft format ciągu to "MS\_*XXX*", gdzie *XXX* jest ciągiem w formacie szesnastkowym, który wskazuje identyfikator ustawień regionalnych (LCID).</span><span class="sxs-lookup"><span data-stu-id="bf1c0-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="bf1c0-119">Jeśli określono nieprawidłowe ustawienia regionalne, metoda zwraca `WBEM_E_INVALID_PARAMETER` wyjątek z wyjątkiem systemu Windows 7, gdzie zamiast tego używane są domyślne ustawienia regionalne serwera.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="bf1c0-120">Jeśli null1, używane są bieżące ustawienia regionalne.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-120">If \`null1, the current locale is used.</span></span>

`lSecurityFlags`\
<span data-ttu-id="bf1c0-121">podczas Flagi do przekazania do `ConnectServerWmi` metody.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-121">[in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="bf1c0-122">Wartość zero (0) dla tego parametru powoduje wywołanie `ConnectServerWmi` zwrotne tylko po ustanowieniu połączenia z serwerem.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="bf1c0-123">Może to spowodować, że aplikacja nie odpowie w nieskończoność, jeśli serwer zostanie przerwany.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="bf1c0-124">Pozostałe prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="bf1c0-124">The other valid values are:</span></span>

| <span data-ttu-id="bf1c0-125">Stała</span><span class="sxs-lookup"><span data-stu-id="bf1c0-125">Constant</span></span>  | <span data-ttu-id="bf1c0-126">Wartość</span><span class="sxs-lookup"><span data-stu-id="bf1c0-126">Value</span></span>  | <span data-ttu-id="bf1c0-127">Opis</span><span class="sxs-lookup"><span data-stu-id="bf1c0-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="bf1c0-128">0x40</span><span class="sxs-lookup"><span data-stu-id="bf1c0-128">0x40</span></span> | <span data-ttu-id="bf1c0-129">Zarezerwowane do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-129">Reserved for internal use.</span></span> <span data-ttu-id="bf1c0-130">Nie używać.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="bf1c0-131">0x80</span><span class="sxs-lookup"><span data-stu-id="bf1c0-131">0x80</span></span> | <span data-ttu-id="bf1c0-132">`ConnectServerWmi`zwraca co najmniej dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

`strAuthority`\
<span data-ttu-id="bf1c0-133">podczas Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-133">[in] The domain name of the user.</span></span> <span data-ttu-id="bf1c0-134">Może mieć następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="bf1c0-134">It can have the following values:</span></span>

| <span data-ttu-id="bf1c0-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="bf1c0-135">Value</span></span> | <span data-ttu-id="bf1c0-136">Opis</span><span class="sxs-lookup"><span data-stu-id="bf1c0-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="bf1c0-137">puste</span><span class="sxs-lookup"><span data-stu-id="bf1c0-137">blank</span></span> | <span data-ttu-id="bf1c0-138">Używane jest uwierzytelnianie NTLM, a używana jest domena NTLM bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="bf1c0-139">Jeśli `strUser` określa domenę (zalecaną lokalizację), nie może być określona w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="bf1c0-140">Funkcja zwraca wartość `WBEM_E_INVALID_PARAMETER` , jeśli określisz domenę w obu parametrach.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="bf1c0-141">Kerberos:*nazwa podmiotu zabezpieczeń*</span><span class="sxs-lookup"><span data-stu-id="bf1c0-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="bf1c0-142">Używane jest uwierzytelnianie Kerberos, a ten parametr zawiera nazwę główną protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="bf1c0-143">NTLMDOMAIN:*nazwa domeny*</span><span class="sxs-lookup"><span data-stu-id="bf1c0-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="bf1c0-144">Używane jest uwierzytelnianie NT LAN Manager, a ten parametr zawiera nazwę domeny NTLM.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`\
<span data-ttu-id="bf1c0-145">podczas Zazwyczaj ten parametr to `null`.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-145">[in] Typically, this parameter is `null`.</span></span> <span data-ttu-id="bf1c0-146">W przeciwnym razie jest wskaźnikiem do obiektu [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wymaganego przez co najmniej jednego dostawcę klas dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span>

`ppNamespace`\
<span data-ttu-id="bf1c0-147">określoną Gdy funkcja zwraca, otrzymuje wskaźnik do obiektu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) powiązanego z określoną przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="bf1c0-148">Jest ona ustawiona na `null` wartość, gdy wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`\
<span data-ttu-id="bf1c0-149">podczas Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-149">[in] The impersonation level.</span></span>

`authLevel`\
<span data-ttu-id="bf1c0-150">podczas Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="bf1c0-151">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bf1c0-151">Return value</span></span>

<span data-ttu-id="bf1c0-152">Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="bf1c0-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bf1c0-153">Stała</span><span class="sxs-lookup"><span data-stu-id="bf1c0-153">Constant</span></span>  |<span data-ttu-id="bf1c0-154">Wartość</span><span class="sxs-lookup"><span data-stu-id="bf1c0-154">Value</span></span>  |<span data-ttu-id="bf1c0-155">Opis</span><span class="sxs-lookup"><span data-stu-id="bf1c0-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="bf1c0-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bf1c0-156">0x80041001</span></span> | <span data-ttu-id="bf1c0-157">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bf1c0-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bf1c0-158">0x80041008</span></span> | <span data-ttu-id="bf1c0-159">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bf1c0-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bf1c0-160">0x80041006</span></span> | <span data-ttu-id="bf1c0-161">Za mało dostępnej pamięci, aby ukończyć tę operację.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="bf1c0-162">0</span><span class="sxs-lookup"><span data-stu-id="bf1c0-162">0</span></span> | <span data-ttu-id="bf1c0-163">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="bf1c0-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf1c0-164">Remarks</span></span>

<span data-ttu-id="bf1c0-165">Ta funkcja otacza wywołanie metody [IWbemLocator:: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) .</span><span class="sxs-lookup"><span data-stu-id="bf1c0-165">This function wraps a call to the [IWbemLocator::ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) method.</span></span>

<span data-ttu-id="bf1c0-166">W przypadku lokalnego dostępu do domyślnej przestrzeni nazw `strNetworkResource` może to być prosta ścieżka obiektu: "root\default" lub "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="bf1c0-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="bf1c0-167">Aby uzyskać dostęp do domyślnej przestrzeni nazw na komputerze zdalnym przy użyciu sieci com lub zgodnej z firmą Microsoft, należy uwzględnić nazwę\\komputera: "myserver\root\default".</span><span class="sxs-lookup"><span data-stu-id="bf1c0-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="bf1c0-168">Nazwą komputera może być również nazwa DNS lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="bf1c0-169">`ConnectServerWmi` Funkcja może również łączyć się z komputerami z uruchomionym protokołem IPv6 przy użyciu adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="bf1c0-170">`strUser`nie może być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="bf1c0-171">Jeśli domena jest określona w `strAuthority`, nie może być również uwzględniona w `strUser`lub funkcja zwraca `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="bf1c0-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf1c0-172">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf1c0-172">Requirements</span></span>

 <span data-ttu-id="bf1c0-173">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf1c0-173">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="bf1c0-174">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bf1c0-174">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="bf1c0-175">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bf1c0-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bf1c0-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf1c0-176">See also</span></span>

- [<span data-ttu-id="bf1c0-177">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="bf1c0-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
