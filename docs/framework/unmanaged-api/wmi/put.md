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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa629c2d07fb25db035cd80aba3c74413070e6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798400"
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
podczas Nazwa właściwości. Ten parametr nie może `null`być.

`lFlags`\
podczas Rezerwacj. Ten parametr musi być równy 0.

`pVal`\
podczas Wskaźnik do prawidłowego `VARIANT` , który będzie nową wartością właściwości. Jeśli `pVal` jest `null` lub `null`wskazuje `VARIANT` na typ `VT_NULL`, właściwość jest ustawiona na.

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
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | Dla wystąpień: Wskazuje, `pVal` że dla właściwości `VARIANT` wskazuje niewłaściwy typ. <br/> Definicje klas: Właściwość już istnieje w klasie nadrzędnej, a nowy typ modelu COM różni się od starego typu COM. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .

Ta funkcja zawsze zastępuje bieżącą wartość właściwości nową. Jeśli [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazuje definicję klasy, `Put` tworzy lub aktualizuje wartość właściwości. Gdy [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazuje na wystąpienie CIM, `Put` aktualizuje tylko wartość właściwości. `Put` nie można utworzyć wartości właściwości.

Właściwość `__CLASS` systemowa jest tylko do zapisu podczas tworzenia klasy, gdy nie powinna pozostać pusta. Wszystkie inne właściwości systemu są tylko do odczytu.

Użytkownik nie może tworzyć właściwości o nazwach zaczynających się lub kończących znakiem podkreślenia ("_"). Jest to zarezerwowane dla klas systemowych i właściwości.

Jeśli właściwość ustawiona przez `Put` funkcję istnieje w klasie nadrzędnej, wartość domyślna właściwości jest zmieniana, chyba że typ właściwości jest niezgodny z typem klasy nadrzędnej. Jeśli właściwość nie istnieje i nie jest to niezgodność typów, zostanie utworzona właściwość.

Użyj parametru `vtType` tylko wtedy, gdy tworzysz nowe właściwości w definicji klasy CIM i `pVal` `VARIANT` jest `null` lub wskazuje typ `VT_NULL`. W tym przypadku `vType` parametr określa typ CIM właściwości. W każdym innym przypadku `vtType` należy mieć wartość 0. `vtType`musi również mieć wartość 0, jeśli obiekt źródłowy jest wystąpieniem (nawet `Val` Jeśli `null`jest), ponieważ typ właściwości jest ustalony i nie można go zmienić.

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem, zobacz [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** WMINet_Utils.idl

**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
