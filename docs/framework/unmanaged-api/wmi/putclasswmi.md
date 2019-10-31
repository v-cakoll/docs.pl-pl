---
title: PutClassWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja PutClassWmi tworzy nową klasę lub aktualizuje istniejącą.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 95a5e1f6339bde9dfe5c5ad9f989fc06e10fa7f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101792"
---
# <a name="putclasswmi-function"></a>PutClassWmi, funkcja

Tworzy nową klasę lub aktualizuje istniejącą.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>Parametry

`pObject`\
podczas Wskaźnik do prawidłowej definicji klasy. Należy ją poprawnie zainicjować przy użyciu wszystkich wymaganych wartości właściwości.

`lFlags`\
podczas Kombinacja flag mających wpływ na zachowanie tej funkcji. Poniższe wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Jeśli ta wartość jest ustawiona, usługa WMI nie przechowuje żadnych kwalifikatorów z zmienionym elementem. <br> Jeśli nie zostanie ustawiona, zakłada się, że ten obiekt nie jest zlokalizowany i wszystkie kwalifikatory są przechowywane z tym wystąpieniem. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Utwórz klasę, jeśli nie istnieje, lub Zastąp ją, jeśli już istnieje. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Zaktualizuj klasę. Klasa musi istnieć, aby wywołanie powiodło się. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Utwórz klasę. Wywołanie zakończy się niepowodzeniem, jeśli Klasa już istnieje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje wywołanie półsynchronicznej. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Dostawcy wypychania muszą określać tę flagę podczas wywoływania `PutClassWmi`, aby wskazać, że ta klasa uległa zmianie. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Umożliwia zaktualizowanie klasy, jeśli nie ma klas pochodnych i nie ma wystąpień tej klasy. Pozwala także na aktualizacje we wszystkich przypadkach, gdy zmiana dotyczy tylko nieistotnych kwalifikatorów, takich jak kwalifikator opisu. Jeśli klasa ma wystąpienia lub zmiany są istotnymi kwalifikatorami, aktualizacja kończy się niepowodzeniem. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Zezwala na aktualizacje klas, nawet jeśli istnieją klasy podrzędne, o ile zmiana nie powoduje żadnych konfliktów z klasami podrzędnymi. Na przykład ta flaga umożliwia dodanie nowej właściwości do klasy podstawowej, która nie została wcześniej wymieniona w żadnej z klas podrzędnych. Jeśli klasa ma wystąpienia, aktualizacja kończy się niepowodzeniem. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | wymusza aktualizacje klas, gdy istnieją sprzeczne klasy podrzędne. Na przykład ta flaga wymusza aktualizację, jeśli kwalifikator klasy jest zdefiniowany w klasie podrzędnej, a Klasa bazowa próbuje dodać ten sam kwalifikator, który powoduje konflikt z istniejącym elementem. W trybie wymuszania konflikt TIS jest rozwiązywany przez usunięcie kwalifikatora powodującego konflikt w klasie podrzędnej. |

`pCtx`\
podczas Zazwyczaj ta wartość jest `null`. W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane klasy.

`ppCallResult`\
określoną Jeśli `null`, ten parametr jest nieużywany. Jeśli `lFlags` zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja wraca bezpośrednio z `WBEM_S_NO_ERROR`. Parametr `ppCallResult` odbiera wskaźnik do nowego obiektu [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Użytkownik nie ma uprawnienia do tworzenia lub modyfikowania klas. |
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Określona Klasa jest nieprawidłowa. Zazwyczaj oznacza to, że `pObject` określa obiekt wystąpienia. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | Określona nazwa klasy jest nieprawidłowa. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Podjęto próbę dokonania zmiany, która spowodowałaby unieważnienie podklasy. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | Określono flagę `WBEM_FLAG_CREATE_ONLY`, ale Klasa już istnieje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` określono w `lFlags`i nie znaleziono klasy. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | Nie wszystkie wymagane właściwości dla klas. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona. Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemServices::P utclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) .

Użytkownik nie może tworzyć klas o nazwach zaczynających się lub kończących znakiem podkreślenia.

Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils. idl

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
