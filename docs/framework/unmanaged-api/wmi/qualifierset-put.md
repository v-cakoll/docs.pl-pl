---
title: QualifierSet_Put — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_Put zapisuje nazwany kwalifikator i jego wartość.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40688a0e4273233245d00fcd927f95945a43f712
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798275"
---
# <a name="qualifierset_put-function"></a>QualifierSet_Put, funkcja

Zapisuje nazwany kwalifikator i wartość. Nowy kwalifikator zastępuje poprzednią wartość tej samej nazwy. Jeśli kwalifikator nie istnieje, zostanie utworzony.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
podczas Ten parametr jest nieużywany.

`ptr`\
podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName`\
podczas Nazwa kwalifikatora do zapisu.

`pVal`\
podczas Wskaźnik do prawidłowego `VARIANT` , który zawiera kwalifikator do zapisu. Ten parametr nie może `null`być.

`lFlavor`\
podczas Jedna z następujących stałych, która definiuje odpowiednie typy kwalifikatorów dla tego kwalifikatora. Wartość domyślna to `WBEM_FLAVOR_OVERRIDABLE` (0).

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Kwalifikator można zastąpić w klasie pochodnej lub w wystąpieniu. **Jest to wartość domyślna.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | Kwalifikator jest propagowany do wystąpień. |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Kwalifikator jest propagowany do klas pochodnych. |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | Kwalifikator nie może zostać zastąpiony w klasie pochodnej lub w wystąpieniu. |
| `WBEM_FLAVOR_AMENDED` | 0x80 | Kwalifikator jest zlokalizowany. |

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Wystąpiła niedozwolona próba określenia kwalifikatora **klucza** dla właściwości, która nie może być kluczem. Klucze są określone w definicji klasy dla obiektu i nie można ich zmienić dla poszczególnych wystąpień. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal` Parametr nie jest dozwolonym typem kwalifikatora. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Nie można wywołać `QualifierSet_Put` metody w kwalifikatorze, ponieważ obiekt będący właścicielem nie zezwala na zastępowanie. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemQualifierSet::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) .

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** WMINet_Utils.idl

**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
