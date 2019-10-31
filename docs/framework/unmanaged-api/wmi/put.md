---
title: Put — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja Put przypisuje nową wartość do nazwanej właściwości.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f1bb8aa09a269e3b8fd23f393d63a275d308a77c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127402"
---
# <a name="put-function"></a>Put — funkcja

Ustawia nazwę właściwości nazwanej na nową wartość.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
podczas Ten parametr jest nieużywany.

`ptr`\
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
podczas Nazwa właściwości. Ten parametr nie może być `null`.

`lFlags`\
podczas Rezerwacj. Ten parametr musi być równy 0.

`pVal`\
podczas Wskaźnik do prawidłowego `VARIANT`, który będzie nową wartością właściwości. Jeśli `pVal` jest `null` lub wskazuje `VARIANT` typu `VT_NULL`, właściwość zostanie ustawiona na `null`.

`vtType`\
podczas Typ `VARIANT` wskazywany przez `pVal`. Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Co najmniej jeden parametr jest nieprawidłowy. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Nie rozpoznano typu właściwości. Ta wartość jest zwracana podczas tworzenia wystąpień klas, jeśli Klasa już istnieje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | W przypadku wystąpień: wskazuje, że `pVal` wskazuje `VARIANT` nieprawidłowego typu dla właściwości. <br/> W przypadku definicji klas: właściwość już istnieje w klasie nadrzędnej, a nowy typ COM różni się od starego typu COM. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .

Ta funkcja zawsze zastępuje bieżącą wartość właściwości nową. Jeśli [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazuje definicję klasy, `Put` tworzy lub aktualizuje wartość właściwości. Gdy [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazuje na wystąpienie modelu wspólnych informacji, `Put` aktualizuje tylko wartość właściwości. `Put` nie może utworzyć wartości właściwości.

Właściwość systemu `__CLASS` jest tylko do zapisu podczas tworzenia klasy, gdy nie powinna być pusta. Wszystkie inne właściwości systemu są tylko do odczytu.

Użytkownik nie może tworzyć właściwości o nazwach zaczynających się lub kończących znakiem podkreślenia ("_"). Jest to zarezerwowane dla klas systemowych i właściwości.

Jeśli właściwość ustawiona przez funkcję `Put` istnieje w klasie nadrzędnej, wartość domyślna właściwości jest zmieniana, chyba że typ właściwości jest niezgodny z typem klasy nadrzędnej. Jeśli właściwość nie istnieje i nie jest to niezgodność typów, zostanie utworzona właściwość.

`vtType` parametru należy używać tylko podczas tworzenia nowych właściwości w definicji klasy CIM i `pVal` jest `null` lub wskazuje `VARIANT` typu `VT_NULL`. W tym przypadku parametr `vType` określa typ CIM właściwości. W każdym innym przypadku `vtType` musi wynosić 0. `vtType` musi również mieć wartość 0, jeśli obiekt źródłowy jest wystąpieniem (nawet jeśli `Val` jest `null`), ponieważ typ właściwości jest ustalony i nie można go zmienić.

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem, zobacz [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils. idl

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
