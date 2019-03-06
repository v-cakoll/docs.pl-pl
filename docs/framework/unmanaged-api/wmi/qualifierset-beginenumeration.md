---
title: Funkcja QualifierSet_BeginEnumeration (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_BeginEnumeration resetuje moduł wyliczający kwalifikatory obiektu.
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
ms.openlocfilehash: f663434d3e3d44dc0c406e71592651493bd8f8dc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375418"
---
# <a name="qualifiersetbeginenumeration-function"></a>QualifierSet_BeginEnumeration — funkcja

Resetuje moduł wyliczający kwalifikatory obiektu na początku tego wyliczenia.

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
[in] Ten parametr jest nieużywany.

`ptr`\
[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.

`lFlags`\
[in] Bitowa kombinacja wartości opisanych w lub flag [uwagi](#remarks) sekcja, która określa kwalifikatory do uwzględnienia w wyliczeniu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` Parametr jest nieprawidłowy. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Drugie wywołanie `QualifierSet_BeginEnumeration` został utworzony bez interwencyjnego wywołania [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) metody.

Wyliczono wszystkie kwalifikatory dla obiektu, ta metoda musi zostać wywołana przed pierwszym wywołaniu [QualifierSet_Next](qualifierset-next.md). Kolejność, w którym są wyliczane kwalifikatory może być inwariantny dla danego wyliczenia.

Flagi, które mogą być przekazywane jako `lEnumFlags` argument są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|  | 0 | Zwraca nazwy wszystkich kwalifikatorów. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Zwróć tylko nazwy kwalifikatory określonych do bieżącej właściwości lub obiektu. <br/> Dla właściwości: Zwróć tylko kwalifikatory określone dla właściwości (w tym zastąpień), a nie kwalifikatory propagowane z poziomu definicji klasy. <br/> W przypadku wystąpienia: Zwróć tylko nazwy kwalifikator danego wystąpienia. <br/> Dla klasy: Zwróć tylko kwalifikatory określonej klasy pochodnej jest.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Zwróć tylko nazwy kwalifikatory propagowane z innego obiektu. <br/> Dla właściwości: Zwróć tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości. <br/> W przypadku wystąpienia: Zwróć tylko tych kwalifikatory propagowane z poziomu definicji klasy. <br/> Dla klasy: Zwróć tylko nazwy kwalifikator dziedziczone z klasy nadrzędnej. |

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils.idl

**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)