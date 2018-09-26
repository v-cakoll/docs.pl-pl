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
ms.openlocfilehash: 244df48606f6d971d6b6e246c4f9b73f916cbdcd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193817"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi — funkcja
Tworzy połączenie za pomocą modelu DCOM do przestrzeni nazw usługi WMI na określonym komputerze.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
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
## <a name="parameters"></a>Parametry

`strNetworkResource` [in] Wskaźnik do prawidłowego `BSTR` zawierający ścieżkę obiektu poprawną przestrzeń nazw usługi WMI. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`strUser` [in] Wskaźnik do prawidłowego `BSTR` zawierający nazwę użytkownika. A `null` wartość wskazuje bieżącego kontekstu zabezpieczeń. Jeśli użytkownik znajduje się w innej domenie niż bieżąca `strUser` może również zawierać nazwę domeny i użytkownika, oddzielone ukośnikiem. `strUser` można też w formacie głównej nazwy (UPN) użytkownika, takie jak `userName@domainName`. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`strPassword` [in] Wskaźnik do prawidłowego `BSTR` zawierającą hasło. A `null` wskazuje bieżącego kontekstu zabezpieczeń. Ciąg pusty ("") wskazuje prawidłowe hasło o zerowej długości.

`strLocale` [in] Wskaźnik do prawidłowego `BSTR` oznacza to poprawne ustawienia regionalne na potrzeby pobierania informacji. W przypadku identyfikatorów ustawień regionalnych firmy Microsoft jest format ciągu "MS\_*xxx*", gdzie *xxx* jest ciągiem w postaci szesnastkowej, która wskazuje identyfikator ustawień regionalnych (LCID). Jeśli określono nieprawidłowe ustawienia regionalne, metoda zwraca `WBEM_E_INVALID_PARAMETER` z wyjątkiem na Windows 7, w których domyślne ustawienia regionalne serwera jest używana zamiast tego. Jeśli "null1, bieżących ustawień regionalnych jest używany. 
 
`lSecurityFlags` [in] Flagi do przekazania do `ConnectServerWmi` metody. Wartość zero (0) dla tego parametru powoduje wywołanie `ConnectServerWmi` zwracanie tylko wtedy, gdy zostanie nawiązane połączenie z serwerem. Może to spowodować, że aplikacja nie odpowiada je na czas nieokreślony Jeśli serwer jest uszkodzony. Prawidłowe wartości to:

| Stała  | Wartość  | Opis  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Zarezerwowane do użytku wewnętrznego. Nie używać. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` Zwraca wartość w ciągu dwóch minut lub szybciej. |

`strAuthority` [in] Nazwa domeny użytkownika. Może mieć następujące wartości:

| Wartość | Opis |
|---------|---------|
| Puste | Zostanie użyte uwierzytelnianie NTLM, a używana jest Domena NTLM bieżącego użytkownika. Jeśli `strUser` określa domenę (zalecana lokalizacja), nie może być określony w tym miejscu. Funkcja zwraca `WBEM_E_INVALID_PARAMETER` w przypadku określenia domeny w obydwu parametrach. |
| Protokołu Kerberos:*nazwa główna* | Jest używane uwierzytelnianie Kerberos, a ten parametr zawiera nazwa główna protokołu Kerberos. |
| NTLMDOMAIN:*nazwy domeny* | Jest używane uwierzytelnianie programu NT LAN Manager, a ten parametr zawiera nazwę domeny uwierzytelnianie NTLM. |

`pCtx`   
[in] Typowo, ten parametr jest `null`. W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wymagany przez dostawców klasy dynamicznej co najmniej jeden obiekt. 

`ppNamespace`  
[out] Gdy funkcja zwróci wartość, otrzymuje wskaźnik [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) obiekt powiązany z określonego obszaru nazw. Jest ustawiona, aby wskazywał `null` po wystąpieniu błędu.

`impLevel`  
[in] Poziom personifikacji.

`authLevel`  
[in] Poziom autoryzacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) metody.

 Lokalny dostęp do domyślnej przestrzeni nazw `strNetworkResource` może być ścieżką prosty obiekt: "root\default" lub "\\.\root\default". Aby uzyskać dostęp do domyślnej przestrzeni nazw na komputerze zdalnym za pomocą modelu COM lub zgodny z programem Microsoft sieci, należy dołączyć nazwę komputera: "\\myserver\root\default". Nazwa komputera może również być nazwy DNS lub adres IP. `ConnectServerWmi` Funkcji można też połączyć z komputerami z systemem IPv6 przy użyciu adresu IPv6.

`strUser` Nie może być ciągiem pustym. Jeśli domena została określona w `strAuthority`, jego musi również być nieuwzględnione w `strUser`, lub funkcja zwraca `WBEM_E_INVALID_PARAMETER`.


## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
