---
title: Funkcja ExecNotificationQueryWmi (niezarządzany wykaz interfejsów API)
description: Funkcja ExecNotificationQueryWmi wykonuje zapytanie w celu odbierania zdarzeń.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9cac00ff96d0c7007bdd6135282c3f767217385e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935619"
---
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi, funkcja

Wykonuje zapytanie, aby odbierać zdarzenia. To wywołanie zwraca natychmiast, a obiekt wywołujący można sondować zwróconego modułu wyliczającego dla zdarzenia podczas ich dostarczania. Zwalnianie zwróconego modułu wyliczającego anuluje zapytania.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT ExecNotificationQueryWmi (
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

## <a name="parameters"></a>Parametry

`strQueryLanguage`\
[in] Ciąg z językiem prawidłowe zapytanie obsługiwane przez Windows Management. Musi to być "WQL" akronim języka WMI Query Language.

`strQuery`\
[in] Tekst zapytania. Ten parametr nie może być `null`.

`lFlags`\
[in] Kombinacja następujące dwie flagi, które mają wpływ na zachowanie tej funkcji. Te wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.

| Stała | Wartość  | Opis  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje, że wywołanie półsynchronicznej. Jeśli ta flaga nie jest ustawiona, połączenie nie powiedzie się. Jest to spowodowane zdarzenia są odbierane w sposób ciągły, co oznacza, że użytkownik musi wykonać sondowanie zwróconego modułu wyliczającego. Blokowanie to wywołanie przez czas nieokreślony uniemożliwia który. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkcja zwraca tylko do przodu modułu wyliczającego. Zwykle tylko do przodu moduły wyliczające są realizowane szybciej i używać mniej pamięci niż moduły wyliczające konwencjonalnych, ale nie zezwalają na wywołania [klonowania](clone.md). |

`pCtx`\
[in] Ta wartość jest zazwyczaj `null`. W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanych zdarzeń.

`ppEnum`\
[out] Jeśli żaden błąd nie wystąpi, otrzymuje wskaźnik, aby moduł wyliczający, który umożliwia obiektowi wywołującemu, można pobrać wystąpień w zestawie wyników zapytania. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`authLevel`\
[in] Poziom autoryzacji.

`impLevel`\
[in] Poziom personifikacji.

`pCurrentNamespace`\
[in] Wskaźnik do [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) obiekt, który reprezentuje bieżącej przestrzeni nazw.

`strUser`\
[in] Nazwa użytkownika. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

`strPassword`\
[in] Hasło. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

`strAuthority`\
[in] Nazwa domeny użytkownika. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Użytkownik nie ma uprawnień do wyświetlania przynajmniej jednej z klas, które może zwracać funkcji. |
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Zapytanie Określa klasę, która nie istnieje. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Zażądano zbyt dużo precyzji podczas dostarczania zdarzeń. Większe tolerancji sondowania musi być określona. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | Zapytanie żąda informacji niż może zapewnić zarządzania Windows. To `HRESULT` jest zwracany, jeśli wyniki zapytania dotyczącego zdarzenia, w żądaniu skierowanym do sondowania wszystkie obiekty w przestrzeni nazw. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Zapytania ma błąd składni. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Żądany język kwerendy nie jest obsługiwane. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Zapytanie jest zbyt złożony. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI został prawdopodobnie zatrzymane i ponowne uruchamianie. Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | Nie można przeanalizować zapytania. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) metody.

Po powrocie z tej funkcji okresowo wywołujący zwracanego `ppEnum` obiekt [dalej](next.md) funkcji, aby sprawdzić, czy wszystkie zdarzenia są dostępne.

Istnieją limity liczby `AND` i `OR` słów kluczowych, które mogą być używane w kwerendach WQL. Dużej liczby WQL słowa kluczowe używane w złożonych kwerend może spowodować, że usługi WMI do zwrócenia `WBEM_E_QUOTA_VIOLATION` (lub 0x8004106c) kod błędu, jako `HRESULT` wartość. Limit słowa kluczowe języka WQL zależy od tego, jak złożona jest zapytanie.

Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils.idl

**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)