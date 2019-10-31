---
title: QualifierSet_GetNames — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_GetNames pobiera nazwy kwalifikatorów z obiektu lub właściwości.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: bd0a67987dd8ffa825114726d066249aed40cf05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141692"
---
# <a name="qualifierset_getnames-function"></a>QualifierSet_GetNames, funkcja

Pobiera nazwy wszystkich kwalifikatorów lub niektórych kwalifikatorów, które są dostępne z bieżącego obiektu lub właściwości.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
podczas Ten parametr jest nieużywany.

`ptr`\
podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`lFlags`\
podczas Jedna z następujących flag lub wartości, które określają, które nazwy mają być uwzględnione w wyliczeniu.

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|  | 0 | Zwróć nazwy wszystkich kwalifikatorów. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Zwraca tylko nazwy kwalifikatorów specyficzne dla bieżącej właściwości lub obiektu. <br/> Dla właściwości: zwracają tylko kwalifikatory charakterystyczne dla właściwości (w tym przesłonięć), a nie te kwalifikatory propagowane z definicji klasy. <br/> Dla wystąpienia: Zwróć tylko nazwy kwalifikatorów specyficznych dla wystąpienia. <br/> Dla klasy: zwracają tylko kwalifikatory charakterystyczne dla klasy pochodnej.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Zwraca tylko nazwy kwalifikatorów, które zostały przekazane z innego obiektu. <br/> Dla właściwości: Zwróć tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości. <br/> Dla wystąpienia: Zwróć tylko te kwalifikatory, które zostały przekazane z definicji klasy. <br/> Dla klasy: Zwróć tylko te nazwy kwalifikatorów dziedziczone z klas nadrzędnych. |

`pstrNames`\
określoną Nowy `SAFEARRAY` zawierający żądane nazwy. Tablica może zawierać 0 elementów. Jeśli wystąpi błąd, nowy `SAFEARRAY` nie zostanie zwrócony.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby rozpocząć nowe Wyliczenie. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemQualifierSet:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) .

Po pobraniu nazw kwalifikatorów możesz uzyskać dostęp do każdego kwalifikatora według nazwy, wywołując funkcję [QualifierSet_Get](qualifierset-get.md) .

Nie jest to błąd dla danego obiektu, aby mieć kwalifikatory zerowe, więc liczba ciągów w `pstrNames` on return może wynosić 0, mimo że funkcja zwraca `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils. idl

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
