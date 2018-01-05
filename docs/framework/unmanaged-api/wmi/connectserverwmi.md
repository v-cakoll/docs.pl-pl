---
title: "Funkcja ConnectServerWmi (niezarządzany wykaz interfejsów API)"
description: "Funkcja ConnectServerWmi używa modelu DCOM, aby utworzyć połączenie do przestrzeni nazw usługi WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ConnectServerWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ConnectServerWmi
helpviewer_keywords: ConnectServerWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc821bddf1d33ea1144fef0821b81cf027d8f92f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="connectserverwmi-function"></a>Funkcja ConnectServerWmi
Tworzy połączenie przy użyciu modelu DCOM do przestrzeni nazw usługi WMI na określonym komputerze.  
  
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

`strNetworkResource`[in] Wskaźnik do prawidłowej `BSTR` zawierający ścieżkę obiektu poprawną przestrzeń nazw usługi WMI. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`strUser`[in] Wskaźnik do prawidłowej `BSTR` zawierający nazwę użytkownika. A `null` wartość wskazuje bieżący kontekst zabezpieczeń. Jeśli użytkownik jest z innej domeny niż bieżąca `strUser` może również zawierać nazwę domeny i użytkownika oddzielone od ukośnika odwrotnego. `strUser`można również być w użytkownika nazwy głównej (UPN) sformatować, suhc jako  *userName@domainName* . Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`strPassword`[in] Wskaźnik do prawidłowej `BSTR` zawiera hasło. A `null` wskazuje bieżący kontekst zabezpieczeń. Ciąg pusty ("") wskazuje prawidłowe hasło o zerowej długości.

`strLocale`[in] Wskaźnik do prawidłowej `BSTR` wskazujące poprawne ustawienia regionalne pobierania informacji. Identyfikatorów ustawień regionalnych firmy Microsoft jest format ciągu "MS\_*xxx*", gdzie *xxx* jest ciągiem w postaci szesnastkowej, która wskazuje identyfikator ustawień regionalnych (LCID). Jeśli określono nieprawidłowe ustawienia regionalne, metoda zwraca `WBEM_E_INVALID_PARAMETER` z wyjątkiem systemu Windows 7, gdzie domyślnych ustawień regionalnych serwera zamiast niego jest używana. Jeśli "null1, bieżących ustawień regionalnych jest używany. 
 
`lSecurityFlags`[in] Flagi do przekazania do `ConnectServerWmi` metody. Wartość zero (0) tego parametru powoduje wywołanie `ConnectServerWmi` zwracanie tylko po nawiązaniu połączenia z serwerem. Może to spowodować, że aplikacja nie odpowiada je nieskończoność Jeśli serwer jest uszkodzona. Prawidłowe wartości to:

| Stała  | Wartość  | Opis  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Zarezerwowany do użytku wewnętrznego. Nie używać. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi`Zwraca w ciągu 2 minut lub mniej. |

`strAuthority`[in] Nazwa domeny użytkownika. Może mieć następujące wartości:

| Wartość | Opis |
|---------|---------|
| Puste | Uwierzytelnianie NTLM jest używany, a używana jest Domena NTLM bieżącego użytkownika. Jeśli `strUser` określa domenę (zalecana lokalizacja) nie może być określony w tym miejscu. Funkcja zwraca `WBEM_E_INVALID_PARAMETER` Jeśli Określ domenę w obydwu tych parametrów. |
| Protokołu Kerberos:*nazwa główna* | Jest używane uwierzytelnianie Kerberos, a ten parametr zawiera nazwy głównej protokołu Kerberos. |
| NTLMDOMAIN:*nazwy domeny* | Jest używane uwierzytelnianie programu NT LAN Manager, a ten parametr zawiera nazwę domeny uwierzytelnianie NTLM. |

`pCtx`   
[in] Zazwyczaj ten parametr jest `null`. W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) wymagany przez dostawców klasy dynamicznej co najmniej jeden obiekt. 

`ppNamespace`  
[out] Po powrocie z funkcji otrzymuje wskaźnik [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) obiekt powiązany z określonego obszaru nazw. Ustawiono wskaż `null` po wystąpieniu błędu.

`impLevel`  
[in] Poziom personifikacji.

`authLevel`  
[in] Poziom autoryzacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) metody.

 Lokalnego dostępu do domyślnej przestrzeni nazw `strNetworkResource` może być ścieżką prostego obiektu: "root\default" lub "\\.\root\default". Aby uzyskać dostęp do domyślnej przestrzeni nazw na komputerze zdalnym przy użyciu modelu COM lub zgodny z programem Microsoft sieci, dołączyć nazwę komputera: "\\myserver\root\default". Nazwa komputera może również zawierać nazwę DNS lub adres IP. `ConnectServerWmi` Funkcja umożliwia też łączność z komputerami z systemem IPv6 przy użyciu adresu IPv6.

`strUser`nie może być pustym ciągiem. Jeśli zostanie określona domena, w `strAuthority`, go nie może również być uwzględniony w `strUser`, lub funkcja zwraca `WBEM_E_INVALID_PARAMETER`.


## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
