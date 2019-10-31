---
title: Next — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja Next pobiera następną właściwość w wyliczeniu.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 587e085f6fe9f6c19d3605c673cd3bd6f68162f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127380"
---
# <a name="next-function"></a>Next — funkcja
Pobiera następną właściwość w wyliczeniu, która rozpoczyna się od wywołania do [beingenumeration](beginenumeration.md).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
podczas Ten parametr jest nieużywany.

`ptr`\
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`\
podczas Rezerwacj. Ten parametr musi być równy 0.

`pstrName`\
określoną Nowy `BSTR`, który zawiera nazwę właściwości. Można ustawić ten parametr, aby `null`, jeśli nazwa nie jest wymagana.

`pVal`\
określoną `VARIANT` wypełnione wartością właściwości. Można ustawić ten parametr, aby `null`, jeśli wartość nie jest wymagana. Jeśli funkcja zwraca kod błędu, `VARIANT` przeszedł do `pVal` nie został zmodyfikowany.

`pvtType`\
określoną Wskaźnik do zmiennej `CIMTYPE` (`LONG`, do której zostanie umieszczony typ właściwości). Wartość tej właściwości może być `VT_NULL_VARIANT`, w tym przypadku jest to konieczne do określenia rzeczywistego typu właściwości. Ten parametr może być również `null`.

`plFlavor`\
[out] `null`lub wartość, która odbiera informacje w pochodzeniu właściwości. Zapoznaj się z sekcją [spostrzeżenia], aby poznać możliwe wartości.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Brak wywołania funkcji [`BeginEnumeration`](beginenumeration.md) . |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby rozpocząć nowe Wyliczenie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Zdalne wywołanie procedury między bieżącym procesem a programem Windows Management nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Nie ma więcej właściwości w wyliczeniu. |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do metody [IWbemClassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) .

Ta metoda zwraca również właściwości systemowe.

Jeśli typ podstawowy właściwości jest ścieżką obiektu, datą lub godziną lub innym typem specjalnym, zwracany typ nie zawiera wystarczającej ilości informacji. Obiekt wywołujący musi sprawdzić `CIMTYPE` dla określonej właściwości, aby określić, czy właściwość jest odwołaniem do obiektu, datą lub godziną lub innym typem specjalnym.

Jeśli `plFlavor` nie `null`, wartość `LONG` otrzymuje informacje o pochodzeniu właściwości w następujący sposób:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Właściwość jest standardową właściwością systemu. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Dla klasy: właściwość jest dziedziczona z klasy nadrzędnej. <br> Dla wystąpienia: właściwość, podczas gdy dziedziczy z klasy nadrzędnej, nie została zmodyfikowana przez wystąpienie.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Dla klasy: właściwość należy do klasy pochodnej. <br> Dla wystąpienia: właściwość jest modyfikowana przez wystąpienie; oznacza to, że została podana wartość lub kwalifikator został dodany lub zmodyfikowany. |

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils. idl

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
