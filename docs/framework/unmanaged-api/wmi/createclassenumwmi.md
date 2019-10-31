---
title: CreateClassEnumWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja CreateClassEnumWmi zwraca moduł wyliczający dla wszystkich klas, które spełniają określone kryteria.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1d637479bd140e635ee647a1e30d03343d8b0dcd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107531"
---
# <a name="createclassenumwmi-function"></a>CreateClassEnumWmi, funkcja
Zwraca moduł wyliczający dla wszystkich klas, które spełniają określone kryteria wyboru.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
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

`strSuperclass`\
podczas Jeśli nie `null` lub puste, określa nazwę klasy nadrzędnej; moduł wyliczający zwraca tylko podklasy tej klasy. Jeśli jest `null` lub puste i `lFlags` jest WBEM_FLAG_SHALLOW, zwraca tylko klasy najwyższego poziomu (klasy bez klasy nadrzędnej). Jeśli jest `null` lub puste i `lFlags` jest `WBEM_FLAG_DEEP`, zwraca wszystkie klasy w przestrzeni nazw.

`lFlags`\
podczas Kombinacja flag mających wpływ na zachowanie tej funkcji. Poniższe wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | W przypadku ustawienia funkcja pobiera zmienione kwalifikatory przechowywane w zlokalizowanej przestrzeni nazw ustawień regionalnych bieżącego połączenia. <br/> Jeśli nie zostanie ustawiona, funkcja pobiera tylko kwalifikatory przechowywane w bezpośredniej przestrzeni nazw. |
| `WBEM_FLAG_DEEP` | 0 | Wyliczenie obejmuje wszystkie podklasy w hierarchii, ale nie tę klasę. |
| `WBEM_FLAG_SHALLOW` | 1 | Wyliczenie obejmuje tylko czyste wystąpienia tej klasy i wyklucza wszystkie wystąpienia podklas, które nie znalazły właściwości w tej klasie. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje wywołanie półsynchronicznej. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkcja zwraca moduł wyliczający tylko do przodu. Zazwyczaj moduły wyliczające tylko do przodu są szybsze i używają mniej pamięci niż konwencjonalne moduły wyliczające, ale nie pozwalają na wywołania [klonowania](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Usługa WMI zachowuje wskaźniki do obiektów w wyliczeniu do momentu ich zwolnienia. |

Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` w celu uzyskania najlepszej wydajności.

`pCtx`\
podczas Zazwyczaj ta wartość jest `null`. W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane klasy.

`ppEnum`\
określoną Odbiera wskaźnik do modułu wyliczającego.

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
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` nie istnieje. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona. Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemServices:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) .

Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils. idl

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
