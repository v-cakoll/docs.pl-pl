---
title: Funkcja CreateClassEnumWmi (niezarządzany wykaz interfejsów API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a4d2c2bd28640d0ac7124f8e0864e9e72fb1eb9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372337"
---
# <a name="createclassenumwmi-function"></a>CreateClassEnumWmi — funkcja
Zwraca moduł wyliczający dla wszystkich klas, które spełniają kryteria określonego zaznaczenia.

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
[in] W przeciwnym razie `null` lub puste, określa nazwę klasy nadrzędnej; moduł wyliczający zwraca tylko podklasy tej klasy. Jeśli jest `null` lub puste i `lFlags` WBEM_FLAG_SHALLOW, zwraca tylko klas najwyższego poziomu (klas z nie klasy nadrzędnej). Jeśli jest `null` lub puste i `lFlags` jest `WBEM_FLAG_DEEP`, zwraca wszystkie klasy w przestrzeni nazw.

`lFlags`\
[in] Kombinacja flag, które mają wpływ na zachowanie tej funkcji. Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Jeśli zestaw, funkcja pobiera poprawionych kwalifikatorów, przechowywane w zlokalizowanych nazw ustawień regionalnych bieżącego połączenia. <br/> W przeciwnym razie zestawu, funkcja pobiera kwalifikatory przechowywanych w bezpośrednim przestrzeni nazw. |
| `WBEM_FLAG_DEEP` | 0 | Wyliczenie zawiera podklasami w hierarchii, ale nie tej klasy. |
| `WBEM_FLAG_SHALLOW` | 1 | Wyliczenie zawiera tylko czyste wystąpienia tej klasy i nie obejmuje wszystkich wystąpień podklas, które dostarczają właściwości nie można odnaleźć w tej klasie. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje, że wywołanie półsynchronicznej. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkcja zwraca tylko do przodu modułu wyliczającego. Zwykle tylko do przodu moduły wyliczające są realizowane szybciej i używać mniej pamięci niż moduły wyliczające konwencjonalnych, ale nie zezwalają na wywołania [klonowania](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI zachowuje wskaźników do obiektów w wyliczeniu, dopóki ich wydaniu. |

Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` uzyskać najlepszą wydajność.

`pCtx`\
[in] Ta wartość jest zazwyczaj `null`. W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy.

`ppEnum`\
[out] Otrzymuje wskaźnik do modułu wyliczającego.

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
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` nie istnieje. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI został prawdopodobnie zatrzymane i ponowne uruchamianie. Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [metodę IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) metody.

Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils.idl

**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)