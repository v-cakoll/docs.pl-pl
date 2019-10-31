---
title: CompareTo — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja CompareTo porównuje obiekt z innym obiektem WMI.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0d210795016cd2e0179b902a224ca0c62f4ac01f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128700"
---
# <a name="compareto-function"></a>CompareTo, funkcja

Porównuje obiekt z innym obiektem zarządzania systemem Windows.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
podczas Ten parametr jest nieużywany.

`ptr`\
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`flags`\
podczas Bitowa kombinacja flag, które określają właściwości obiektu, które należy wziąć pod uwagę w porównaniu z porównaniem. Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji.

`pCompareTo`\
podczas Obiekt do porównania. `pCompareTo` musi być prawidłowym wystąpieniem [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ; nie może być `null`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Drugie wywołanie `BeginEnumeration` zostało wykonane bez interwencji wywołującego do [`EndEnumeration`](endenumeration.md). |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Obiekty są różne. |
| `WBEM_S_SAME` | 0 | Obiekty są takie same, w zależności od flag porównania. |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) .

Flagi, które mogą być przesyłane jako argument `lEnumFlags`, są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie. Można określić poszczególne cechy, które są wykorzystywane w porównaniu, określając bitową kombinację następujących flag:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Zignoruj źródło (serwer i przestrzeń nazw, z których pochodzą). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignoruj wszystkie kwalifikatory (w tym **klucz** i **dynamiczny**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Ignoruj wartości domyślne właściwości. Ta flaga ma zastosowanie tylko do porównania klas. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Ignoruj typy kwalifikatorów. Ta flaga nadal przyjmuje kwalifikatory do konta, ale ignoruje różnice wersji, takie jak reguły propagacji i ograniczenia przesłonięć. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Ignoruj wielkość liter podczas porównywania wartości ciągu. Dotyczy to zarówno ciągów, jak i wartości kwalifikatorów. Porównanie nazw właściwości i kwalifikatora jest zawsze rozróżniana wielkość liter niezależnie od tego, czy flaga jest ustawiona. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Załóżmy, że porównywane obiekty są wystąpieniami tej samej klasy. W związku z tym flaga porównuje tylko informacje związane z wystąpieniem. Użyj tych flag, aby zoptymalizować wydajność. Jeśli obiekty nie należą do tej samej klasy, wyniki są niezdefiniowane. |

Lub można określić pojedynczą flagę złożoną w następujący sposób:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Należy wziąć pod uwagę wszystkie funkcje w porównaniu. |

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils. idl

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
