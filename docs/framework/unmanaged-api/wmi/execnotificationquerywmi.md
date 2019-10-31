---
title: ExecNotificationQueryWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja ExecNotificationQueryWmi wykonuje zapytanie, aby odbierać zdarzenia.
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
ms.openlocfilehash: 3d8a7683eef52a5e91bf7aa84d5aa7db7dbdac8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130443"
---
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi, funkcja

Wykonuje zapytanie do odbierania zdarzeń. Wywołanie wraca natychmiast, a obiekt wywołujący może sondować zwracany moduł wyliczający dla zdarzeń po ich nadejściu. Zwolnienie zwróconego modułu wyliczającego powoduje anulowanie zapytania.

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
podczas Ciąg z prawidłowym językiem zapytań obsługiwanym przez zarządzanie systemem Windows. Musi to być "WQL", akronim dla język zapytań usługi WMI.

`strQuery`\
podczas Tekst zapytania. Ten parametr nie może być `null`.

`lFlags`\
podczas Kombinacja następujących dwóch flag mających wpływ na zachowanie tej funkcji. Te wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie.

| Stała | Wartość  | Opis  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje wywołanie półsynchronicznej. Jeśli ta flaga nie jest ustawiona, wywołanie zakończy się niepowodzeniem. Wynika to z faktu, że zdarzenia są ciągle odbierane, co oznacza, że użytkownik musi sondować zwrócony moduł wyliczający. Zablokowanie tego wywołania bezterminowo sprawia, że jest to niemożliwe. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkcja zwraca moduł wyliczający tylko do przodu. Zazwyczaj moduły wyliczające tylko do przodu są szybsze i używają mniej pamięci niż konwencjonalne moduły wyliczające, ale nie pozwalają na wywołania [klonowania](clone.md). |

`pCtx`\
podczas Zazwyczaj ta wartość jest `null`. W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane zdarzenia.

`ppEnum`\
określoną Jeśli błąd nie wystąpi, otrzymuje wskaźnik do modułu wyliczającego, który umożliwia obiektowi wywołującemu pobieranie wystąpień w zestawie wyników zapytania. Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.

`authLevel`\
podczas Poziom autoryzacji.

`impLevel`\
podczas Poziom personifikacji.

`pCurrentNamespace`\
podczas Wskaźnik do obiektu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , który reprezentuje bieżącą przestrzeń nazw.

`strUser`\
podczas Nazwa użytkownika. Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.

`strPassword`\
podczas Hasło. Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.

`strAuthority`\
podczas Nazwa domeny użytkownika. Zobacz funkcję [ConnectServerWmi](connectserverwmi.md) , aby uzyskać więcej informacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Użytkownik nie ma uprawnienia do wyświetlania jednej lub więcej klas, które funkcja może zwrócić. |
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Zapytanie określa klasę, która nie istnieje. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Zażądano zbyt dużej dokładności dostarczania zdarzeń. Należy określić większą tolerancję sondowania. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | Zapytanie żąda więcej informacji niż można zapewnić zarządzanie systemem Windows. Ta `HRESULT` jest zwracana, gdy zapytanie zdarzenia powoduje żądanie sondowania wszystkich obiektów w przestrzeni nazw. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Zapytanie zawierało błąd składniowy. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Żądany język kwerendy nie jest obsługiwany. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Zapytanie jest zbyt złożone. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona. Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | Nie można przeanalizować zapytania. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemServices:: ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) .

Po powrocie funkcji obiekt wywołujący okresowo przekazuje zwrócony obiekt `ppEnum` do [następnej](next.md) funkcji, aby sprawdzić, czy jakieś zdarzenia są dostępne.

Istnieją ograniczenia liczby `AND` i `OR` słów kluczowych, które mogą być używane w zapytaniach WQL. Duża liczba słów kluczowych WQL używanych w złożonej kwerendzie może spowodować, że usługa WMI zwróci kod błędu `WBEM_E_QUOTA_VIOLATION` (lub 0x8004106c) jako wartość `HRESULT`ą. Limit słów kluczowych WQL zależy od tego, jak złożona jest kwerenda.

Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils. idl

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
