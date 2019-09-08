---
title: QualifierSet_BeginEnumeration — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_BeginEnumeration resetuje moduł wyliczający kwalifikatorów obiektu.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b75c51ebddd78e447fed57b22a96c2d5c35004e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798347"
---
# <a name="qualifierset_beginenumeration-function"></a>QualifierSet_BeginEnumeration, funkcja

Resetuje moduł wyliczający kwalifikatorów obiektu na początku wyliczenia.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
podczas Ten parametr jest nieużywany.

`ptr`\
podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`lFlags`\
podczas Bitowa kombinacja flag lub wartości opisanych w sekcji [uwagi](#remarks) , która określa kwalifikatory do uwzględnienia w wyliczeniu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` Parametr jest nieprawidłowy. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Drugie wywołanie `QualifierSet_BeginEnumeration` zostało wykonane bez wywołania wywołującego do [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby rozpocząć nowe Wyliczenie. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemQualifierSet:: beingenumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) .

Aby wyliczyć wszystkie kwalifikatory obiektu, należy wywołać tę metodę przed pierwszym wywołaniem do [QualifierSet_Next](qualifierset-next.md). Kolejność, w której są wyliczane kwalifikatory, jest gwarantowany jako niezmienna dla danego wyliczenia.

Flagi, które mogą być przesyłane jako `lEnumFlags` argument, są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie.

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|  | 0 | Zwróć nazwy wszystkich kwalifikatorów. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Zwraca tylko nazwy kwalifikatorów specyficzne dla bieżącej właściwości lub obiektu. <br/> Dla właściwości: Zwróć tylko kwalifikatory charakterystyczne dla właściwości (w tym przesłonięć), a nie te kwalifikatory, które zostały przekazane z definicji klasy. <br/> Dla wystąpienia: Zwróć tylko nazwy kwalifikatorów specyficznych dla wystąpienia. <br/> Dla klasy: Zwróć tylko kwalifikatory charakterystyczne dla klasy pochodnej.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Zwraca tylko nazwy kwalifikatorów, które zostały przekazane z innego obiektu. <br/> Dla właściwości: Zwróć tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości. <br/> Dla wystąpienia: Zwraca tylko te kwalifikatory, które zostały przekazane z definicji klasy. <br/> Dla klasy: Zwróć tylko te nazwy kwalifikatorów dziedziczone z klas nadrzędnych. |

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** WMINet_Utils.idl

**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
