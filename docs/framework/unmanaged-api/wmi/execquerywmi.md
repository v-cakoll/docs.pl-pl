---
title: ExecQueryWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja ExecQueryWmi wykonuje zapytanie w celu pobrania obiektów.
ms.date: 11/06/2017
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
ms.openlocfilehash: b8547d306819e85b838f1160d9912dd43e42f2f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798691"
---
# <a name="execquerywmi-function"></a>ExecQueryWmi, funkcja

Wykonuje zapytanie w celu pobrania obiektów.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
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

## <a name="parameters"></a>Parametry

`strQueryLanguage`\
podczas Ciąg z prawidłowym językiem zapytań obsługiwanym przez zarządzanie systemem Windows. Musi to być "WQL", akronim dla język zapytań usługi WMI.

`strQuery`\
podczas Tekst zapytania. Ten parametr nie może `null`być.

`lFlags`\
podczas Kombinacja flag mających wpływ na zachowanie tej funkcji. Poniższe wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

| Stała | Wartość  | Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | W przypadku ustawienia funkcja pobiera zmienione kwalifikatory przechowywane w zlokalizowanej przestrzeni nazw ustawień regionalnych bieżącego połączenia. <br/> Jeśli nie zostanie ustawiona, funkcja pobiera tylko kwalifikatory przechowywane w bezpośredniej przestrzeni nazw. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje wywołanie półsynchronicznej. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkcja zwraca moduł wyliczający tylko do przodu. Zazwyczaj moduły wyliczające tylko do przodu są szybsze i używają mniej pamięci niż konwencjonalne moduły wyliczające, ale nie pozwalają na wywołania [klonowania](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Usługa WMI zachowuje wskaźniki do obiektów w wyliczeniu do momentu ich zwolnienia. |
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Zapewnia, że wszystkie zwrócone obiekty mają wystarczającą ilość informacji, tak aby `null`nie były to właściwości systemu, takie jak **__PATH**, **__RELPATH**i **__SERVER**. |
| `WBEM_FLAG_PROTOTYPE` | 2 | Ta flaga jest używana do tworzenia prototypów. Nie wykonuje zapytania i zamiast tego zwraca obiekt, który wygląda jak typowy obiekt wynikowy. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | Powoduje bezpośredni dostęp do dostawcy dla określonej klasy bez względu na jego klasę nadrzędną ani żadnej podklasy. |

Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` zapewniają najlepszą wydajność.

`pCtx`\
podczas Zazwyczaj ta wartość to `null`. W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane klasy.

`ppEnum`\
określoną Jeśli błąd nie wystąpi, otrzymuje wskaźnik do modułu wyliczającego, który umożliwia obiektowi wywołującemu pobieranie wystąpień w zestawie wyników zapytania. Zapytanie może mieć zestaw wyników o zerowej instancji. Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.

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
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Zapytanie zawierało błąd składniowy. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Żądany język kwerendy nie jest obsługiwany. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Zapytanie jest zbyt złożone. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona. Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Zapytanie określa klasę, która nie istnieje. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemServices:: ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) .

Ta funkcja przetwarza zapytanie określone w `strQuery` parametrze i tworzy moduł wyliczający, za pomocą którego obiekt wywołujący może uzyskać dostęp do wyników zapytania. Moduł wyliczający jest wskaźnikiem do interfejsu [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) ; wyniki zapytania są wystąpieniami obiektów klasy udostępnianych za pomocą interfejsu [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Istnieją limity dotyczące liczby `AND` i `OR` słów kluczowych, które mogą być używane w zapytaniach WQL. Duża liczba słów kluczowych WQL używanych w złożonej kwerendzie może spowodować, że usługa WMI `WBEM_E_QUOTA_VIOLATION` zwróci kod błędu (lub 0x8004106c) `HRESULT` jako wartość. Limit słów kluczowych WQL zależy od tego, jak złożona jest kwerenda.

Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** WMINet_Utils.idl

**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
