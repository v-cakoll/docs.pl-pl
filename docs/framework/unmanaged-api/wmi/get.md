---
title: Get — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja Get pobiera określoną wartość właściwości.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 60f29b91000fd3c07efea88dcc319eb283a4af78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120329"
---
# <a name="get-function"></a>Get, funkcja

Pobiera określoną wartość właściwości, jeśli istnieje.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
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

`wszName`\
podczas Nazwa właściwości.

`lFlags`\
podczas Rezerwacj. Ten parametr musi być równy 0.

`pVal`\
określoną Jeśli funkcja zwróci się pomyślnie, zawiera wartość właściwości `wszName`. Do argumentu `pval` jest przypisany prawidłowy typ i wartość dla kwalifikatora.

`pvtType`\
określoną Jeśli funkcja zwróci się pomyślnie, zawiera [stałą typu CIM](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) , która wskazuje typ właściwości. Jego wartość może być również `null`. 

`plFlavor`\
określoną Jeśli funkcja zwróci się pomyślnie, otrzymuje informacje o pochodzeniu właściwości. Jej wartość może być `null`lub jedna z następujących stałych WBEM_FLAVOR_TYPE zdefiniowanych w pliku nagłówkowym *WbemCli. h* : 

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Właściwość jest standardową właściwością systemu. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Dla klasy: właściwość jest dziedziczona z klasy nadrzędnej. <br> Dla wystąpienia: właściwość, podczas gdy dziedziczy z klasy nadrzędnej, nie została zmodyfikowana przez wystąpienie.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Dla klasy: właściwość należy do klasy pochodnej. <br> Dla wystąpienia: właściwość jest modyfikowana przez wystąpienie; oznacza to, że została podana wartość lub kwalifikator został dodany lub zmodyfikowany. |

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Co najmniej jeden parametr jest nieprawidłowy. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonej właściwości. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) .

Funkcja `Get` może również zwracać właściwości systemu.

Do argumentu `pVal` jest przypisany prawidłowy typ i wartość kwalifikatora oraz funkcja COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówek:** WMINet_Utils. idl

 **Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
