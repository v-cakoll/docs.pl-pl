---
title: DELETE — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja DELETE Usuwa określoną właściwość i wszystkie jej kwalifikatory z definicji klasy CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6b8f287be831702dd31a8335f9b2f6447bcee540
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127666"
---
# <a name="delete-function"></a>Delete, funkcja

Usuwa określoną właściwość i wszystkie jej kwalifikatory z definicji klasy CIM.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
podczas Ten parametr jest nieużywany.

`ptr`\
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
podczas Nazwa właściwości do usunięcia. `wszName` musi być wskaźnikiem do prawidłowej `LPCWSTR`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Nie można usunąć właściwości. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` jest nieprawidłowy. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Określona właściwość nie istnieje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci, aby ukończyć operację. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | Właściwość jest dziedziczona z klasy bazowej. |
| `WBEM_E_SYSTEM_PROPERTY` | | Właściwość jest właściwością systemową. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | Funkcja usunęła wartość domyślną przesłonięcia dla bieżącej klasy. Wartość domyślna tej właściwości w klasie nadrzędnej została ponownie aktywowana. |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject::D Usuń](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) .

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils. idl

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
