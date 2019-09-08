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
# <a name="connectserverwmi-function"></a>ConnectServerWmi, funkcja

Tworzy połączenie za pomocą modelu DCOM do przestrzeni nazw usługi WMI na określonym komputerze.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

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

## <a name="parameters"></a>Parametry

`strNetworkResource`\
podczas Wskaźnik na prawidłowy `BSTR` , który zawiera ścieżkę obiektu poprawnej przestrzeni nazw usługi WMI. Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.

`strUser`\
podczas Wskaźnik do prawidłowego `BSTR` , który zawiera nazwę użytkownika. `null` Wartość wskazuje bieżący kontekst zabezpieczeń. Jeśli użytkownik należy do innej domeny niż bieżąca, `strUser` może również zawierać nazwę domeny i użytkownika rozdzieloną ukośnikiem odwrotnym. `strUser`może być również w formacie głównej nazwy użytkownika (UPN), np `userName@domainName`. Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.

`strPassword`\
podczas Wskaźnik do prawidłowego `BSTR` , który zawiera hasło. `null` Wskazuje bieżący kontekst zabezpieczeń. Pusty ciąg ("") wskazuje prawidłowe hasło o zerowej długości.

`strLocale`\
podczas Wskaźnik do prawidłowego `BSTR` , który wskazuje prawidłowe ustawienia regionalne do pobierania informacji. W przypadku identyfikatorów ustawień regionalnych firmy Microsoft format ciągu to "MS\_*XXX*", gdzie *XXX* jest ciągiem w formacie szesnastkowym, który wskazuje identyfikator ustawień regionalnych (LCID). Jeśli określono nieprawidłowe ustawienia regionalne, metoda zwraca `WBEM_E_INVALID_PARAMETER` wyjątek z wyjątkiem systemu Windows 7, gdzie zamiast tego używane są domyślne ustawienia regionalne serwera. Jeśli null1, używane są bieżące ustawienia regionalne.

`lSecurityFlags`\
podczas Flagi do przekazania do `ConnectServerWmi` metody. Wartość zero (0) dla tego parametru powoduje wywołanie `ConnectServerWmi` zwrotne tylko po ustanowieniu połączenia z serwerem. Może to spowodować, że aplikacja nie odpowie w nieskończoność, jeśli serwer zostanie przerwany. Pozostałe prawidłowe wartości to:

| Stała  | Wartość  | Opis  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Zarezerwowane do użytku wewnętrznego. Nie używać. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi`zwraca co najmniej dwie minuty. |

`strAuthority`\
podczas Nazwa domeny użytkownika. Może mieć następujące wartości:

| Wartość | Opis |
|---------|---------|
| puste | Używane jest uwierzytelnianie NTLM, a używana jest domena NTLM bieżącego użytkownika. Jeśli `strUser` określa domenę (zalecaną lokalizację), nie może być określona w tym miejscu. Funkcja zwraca wartość `WBEM_E_INVALID_PARAMETER` , jeśli określisz domenę w obu parametrach. |
| Kerberos:*nazwa podmiotu zabezpieczeń* | Używane jest uwierzytelnianie Kerberos, a ten parametr zawiera nazwę główną protokołu Kerberos. |
| NTLMDOMAIN:*nazwa domeny* | Używane jest uwierzytelnianie NT LAN Manager, a ten parametr zawiera nazwę domeny NTLM. |

`pCtx`\
podczas Zazwyczaj ten parametr to `null`. W przeciwnym razie jest wskaźnikiem do obiektu [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wymaganego przez co najmniej jednego dostawcę klas dynamicznych.

`ppNamespace`\
określoną Gdy funkcja zwraca, otrzymuje wskaźnik do obiektu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) powiązanego z określoną przestrzenią nazw. Jest ona ustawiona na `null` wartość, gdy wystąpi błąd.

`impLevel`\
podczas Poziom personifikacji.

`authLevel`\
podczas Poziom autoryzacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemLocator:: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) .

W przypadku lokalnego dostępu do domyślnej przestrzeni nazw `strNetworkResource` może to być prosta ścieżka obiektu: "root\default" lub "\\.\root\default". Aby uzyskać dostęp do domyślnej przestrzeni nazw na komputerze zdalnym przy użyciu sieci com lub zgodnej z firmą Microsoft, należy uwzględnić nazwę\\komputera: "myserver\root\default". Nazwą komputera może być również nazwa DNS lub adres IP. `ConnectServerWmi` Funkcja może również łączyć się z komputerami z uruchomionym protokołem IPv6 przy użyciu adresu IPv6.

`strUser`nie może być pustym ciągiem. Jeśli domena jest określona w `strAuthority`, nie może być również uwzględniona w `strUser`lub funkcja zwraca `WBEM_E_INVALID_PARAMETER`.

## <a name="requirements"></a>Wymagania

 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówki** WMINet_Utils.idl

 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
