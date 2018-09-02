---
title: Funkcja ConnectServerWmi (niezarządzany wykaz interfejsów API)
description: Funkcja ConnectServerWmi używa modelu DCOM, aby utworzyć połączenie do przestrzeni nazw usługi WMI.
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
ms.openlocfilehash: 163e61eef8a753b5b6470285e5e3ce63789e25a4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416140"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="5492a-103">ConnectServerWmi — funkcja</span><span class="sxs-lookup"><span data-stu-id="5492a-103">ConnectServerWmi function</span></span>
<span data-ttu-id="5492a-104">Tworzy połączenie za pomocą modelu DCOM do przestrzeni nazw usługi WMI na określonym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5492a-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5492a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5492a-105">Syntax</span></span>  
  
```  
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
## <a name="parameters"></a><span data-ttu-id="5492a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5492a-106">Parameters</span></span>

<span data-ttu-id="5492a-107">`strNetworkResource` [in] Wskaźnik do prawidłowego `BSTR` zawierający ścieżkę obiektu poprawną przestrzeń nazw usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="5492a-107">`strNetworkResource` [in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="5492a-108">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="5492a-108">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="5492a-109">`strUser` [in] Wskaźnik do prawidłowego `BSTR` zawierający nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5492a-109">`strUser` [in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="5492a-110">A `null` wartość wskazuje bieżącego kontekstu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5492a-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="5492a-111">Jeśli użytkownik znajduje się w innej domenie niż bieżąca `strUser` może również zawierać nazwę domeny i użytkownika, oddzielone ukośnikiem.</span><span class="sxs-lookup"><span data-stu-id="5492a-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="5492a-112">`strUser` może również być użytkownika głównej nazwy (UPN) sformatować, suhc jako *userName@domainName*.</span><span class="sxs-lookup"><span data-stu-id="5492a-112">`strUser` can also be in user principal name (UPN) format, suhc as *userName@domainName*.</span></span> <span data-ttu-id="5492a-113">Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="5492a-113">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="5492a-114">`strPassword` [in] Wskaźnik do prawidłowego `BSTR` zawierającą hasło.</span><span class="sxs-lookup"><span data-stu-id="5492a-114">`strPassword` [in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="5492a-115">A `null` wskazuje bieżącego kontekstu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5492a-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="5492a-116">Ciąg pusty ("") wskazuje prawidłowe hasło o zerowej długości.</span><span class="sxs-lookup"><span data-stu-id="5492a-116">An empty string ("") indicates a valid zero-length password.</span></span>

<span data-ttu-id="5492a-117">`strLocale` [in] Wskaźnik do prawidłowego `BSTR` oznacza to poprawne ustawienia regionalne na potrzeby pobierania informacji.</span><span class="sxs-lookup"><span data-stu-id="5492a-117">`strLocale` [in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="5492a-118">W przypadku identyfikatorów ustawień regionalnych firmy Microsoft jest format ciągu "MS\_*xxx*", gdzie *xxx* jest ciągiem w postaci szesnastkowej, która wskazuje identyfikator ustawień regionalnych (LCID).</span><span class="sxs-lookup"><span data-stu-id="5492a-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="5492a-119">Jeśli określono nieprawidłowe ustawienia regionalne, metoda zwraca `WBEM_E_INVALID_PARAMETER` z wyjątkiem na Windows 7, w których domyślne ustawienia regionalne serwera jest używana zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="5492a-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="5492a-120">Jeśli "null1, bieżących ustawień regionalnych jest używany.</span><span class="sxs-lookup"><span data-stu-id="5492a-120">If \`null1, the current locale is used.</span></span> 
 
<span data-ttu-id="5492a-121">`lSecurityFlags` [in] Flagi do przekazania do `ConnectServerWmi` metody.</span><span class="sxs-lookup"><span data-stu-id="5492a-121">`lSecurityFlags` [in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="5492a-122">Wartość zero (0) dla tego parametru powoduje wywołanie `ConnectServerWmi` zwracanie tylko wtedy, gdy zostanie nawiązane połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="5492a-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="5492a-123">Może to spowodować, że aplikacja nie odpowiada je na czas nieokreślony Jeśli serwer jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="5492a-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="5492a-124">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="5492a-124">The other valid values are:</span></span>

| <span data-ttu-id="5492a-125">Stała</span><span class="sxs-lookup"><span data-stu-id="5492a-125">Constant</span></span>  | <span data-ttu-id="5492a-126">Wartość</span><span class="sxs-lookup"><span data-stu-id="5492a-126">Value</span></span>  | <span data-ttu-id="5492a-127">Opis</span><span class="sxs-lookup"><span data-stu-id="5492a-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="5492a-128">0x40</span><span class="sxs-lookup"><span data-stu-id="5492a-128">0x40</span></span> | <span data-ttu-id="5492a-129">Zarezerwowane do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="5492a-129">Reserved for internal use.</span></span> <span data-ttu-id="5492a-130">Nie używać.</span><span class="sxs-lookup"><span data-stu-id="5492a-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="5492a-131">0x80</span><span class="sxs-lookup"><span data-stu-id="5492a-131">0x80</span></span> | <span data-ttu-id="5492a-132">`ConnectServerWmi` Zwraca wartość w ciągu dwóch minut lub szybciej.</span><span class="sxs-lookup"><span data-stu-id="5492a-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

<span data-ttu-id="5492a-133">`strAuthority` [in] Nazwa domeny użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5492a-133">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="5492a-134">Może mieć następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="5492a-134">It can have the following values:</span></span>

| <span data-ttu-id="5492a-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="5492a-135">Value</span></span> | <span data-ttu-id="5492a-136">Opis</span><span class="sxs-lookup"><span data-stu-id="5492a-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="5492a-137">Puste</span><span class="sxs-lookup"><span data-stu-id="5492a-137">blank</span></span> | <span data-ttu-id="5492a-138">Zostanie użyte uwierzytelnianie NTLM, a używana jest Domena NTLM bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5492a-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="5492a-139">Jeśli `strUser` określa domenę (zalecana lokalizacja), nie może być określony w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="5492a-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="5492a-140">Funkcja zwraca `WBEM_E_INVALID_PARAMETER` w przypadku określenia domeny w obydwu parametrach.</span><span class="sxs-lookup"><span data-stu-id="5492a-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="5492a-141">Protokołu Kerberos:*nazwa główna*</span><span class="sxs-lookup"><span data-stu-id="5492a-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="5492a-142">Jest używane uwierzytelnianie Kerberos, a ten parametr zawiera nazwa główna protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="5492a-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="5492a-143">NTLMDOMAIN:*nazwy domeny*</span><span class="sxs-lookup"><span data-stu-id="5492a-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="5492a-144">Jest używane uwierzytelnianie programu NT LAN Manager, a ten parametr zawiera nazwę domeny uwierzytelnianie NTLM.</span><span class="sxs-lookup"><span data-stu-id="5492a-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`   
<span data-ttu-id="5492a-145">[in] Typowo, ten parametr jest `null`.</span><span class="sxs-lookup"><span data-stu-id="5492a-145">[in] Typically, this parameter is is `null`.</span></span> <span data-ttu-id="5492a-146">W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wymagany przez dostawców klasy dynamicznej co najmniej jeden obiekt.</span><span class="sxs-lookup"><span data-stu-id="5492a-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span> 

`ppNamespace`  
<span data-ttu-id="5492a-147">[out] Gdy funkcja zwróci wartość, otrzymuje wskaźnik [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) obiekt powiązany z określonego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="5492a-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="5492a-148">Jest ustawiona, aby wskazywał `null` po wystąpieniu błędu.</span><span class="sxs-lookup"><span data-stu-id="5492a-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`  
<span data-ttu-id="5492a-149">[in] Poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="5492a-149">[in] The impersonation level.</span></span>

`authLevel`  
<span data-ttu-id="5492a-150">[in] Poziom autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="5492a-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="5492a-151">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5492a-151">Return value</span></span>

<span data-ttu-id="5492a-152">Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="5492a-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5492a-153">Stała</span><span class="sxs-lookup"><span data-stu-id="5492a-153">Constant</span></span>  |<span data-ttu-id="5492a-154">Wartość</span><span class="sxs-lookup"><span data-stu-id="5492a-154">Value</span></span>  |<span data-ttu-id="5492a-155">Opis</span><span class="sxs-lookup"><span data-stu-id="5492a-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="5492a-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5492a-156">0x80041001</span></span> | <span data-ttu-id="5492a-157">Wystąpił błąd ogólny.</span><span class="sxs-lookup"><span data-stu-id="5492a-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5492a-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5492a-158">0x80041008</span></span> | <span data-ttu-id="5492a-159">Parametr jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="5492a-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5492a-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5492a-160">0x80041006</span></span> | <span data-ttu-id="5492a-161">Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="5492a-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5492a-162">0</span><span class="sxs-lookup"><span data-stu-id="5492a-162">0</span></span> | <span data-ttu-id="5492a-163">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5492a-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5492a-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5492a-164">Remarks</span></span>

<span data-ttu-id="5492a-165">Ta funkcja zawija wywołanie do [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="5492a-165">This function wraps a call to the [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) method.</span></span>

 <span data-ttu-id="5492a-166">Lokalny dostęp do domyślnej przestrzeni nazw `strNetworkResource` może być ścieżką prosty obiekt: "root\default" lub "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="5492a-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="5492a-167">Aby uzyskać dostęp do domyślnej przestrzeni nazw na komputerze zdalnym za pomocą modelu COM lub zgodny z programem Microsoft sieci, należy dołączyć nazwę komputera: "\\myserver\root\default".</span><span class="sxs-lookup"><span data-stu-id="5492a-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="5492a-168">Nazwa komputera może również być nazwy DNS lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="5492a-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="5492a-169">`ConnectServerWmi` Funkcji można też połączyć z komputerami z systemem IPv6 przy użyciu adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="5492a-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="5492a-170">`strUser` Nie może być ciągiem pustym.</span><span class="sxs-lookup"><span data-stu-id="5492a-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="5492a-171">Jeśli domena została określona w `strAuthority`, jego musi również być nieuwzględnione w `strUser`, lub funkcja zwraca `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="5492a-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>


## <a name="requirements"></a><span data-ttu-id="5492a-172">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5492a-172">Requirements</span></span>  
 <span data-ttu-id="5492a-173">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5492a-173">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5492a-174">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5492a-174">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5492a-175">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5492a-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5492a-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5492a-176">See also</span></span>  
[<span data-ttu-id="5492a-177">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="5492a-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
