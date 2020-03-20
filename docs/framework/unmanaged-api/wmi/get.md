---
title: Pobierz funkcję (odwołanie do interfejsu API niezarządzanego)
description: Funkcja Pobierz pobiera określoną wartość właściwości.
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
ms.openlocfilehash: 67fcfb301eebfcf4ed4fdcaa5c9ddf85c47a6073
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174982"
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
[w] Ten parametr jest nieużywane.

`ptr`\
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszName`\
[w] Nazwa właściwości.

`lFlags`\
[w] Zastrzeżone. Ten parametr musi być 0.

`pVal`\
[na zewnątrz] Jeśli funkcja zwraca pomyślnie, zawiera `wszName` wartość właściwości. Argument `pval` jest przypisany poprawny typ i wartość kwalifikatora.

`pvtType`\
[na zewnątrz] Jeśli funkcja zwraca pomyślnie, zawiera [stałą typu CIM,](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) która wskazuje typ właściwości. Jego wartość może `null`być również .

`plFlavor`\
[na zewnątrz] Jeśli funkcja zwraca pomyślnie, odbiera informacje o pochodzeniu właściwości. Jego wartość `null`może być , lub jeden z następujących WBEM_FLAVOR_TYPE stałych zdefiniowanych w pliku nagłówka *WbemCli.h:*

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Właściwość jest standardową właściwością systemową. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Dla klasy: Właściwość jest dziedziczona z klasy nadrzędnej. <br> Dla wystąpienia: Właściwość, gdy dziedziczone z klasy nadrzędnej, nie został zmodyfikowany przez wystąpienie.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Dla klasy: Właściwość należy do klasy pochodnej. <br> Na wystąpienie: Właściwość jest modyfikowana przez wystąpienie; oznacza to, że wartość została dostarczona lub kwalifikator został dodany lub zmodyfikowany. |

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpiła ogólna porażka. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Co najmniej jeden parametr jest nieprawidłowy. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonej właściwości. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do ukończenia operacji. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) metody.

Funkcja `Get` może również zwracać właściwości systemu.

Argumentowi `pVal` jest przypisywany poprawny typ i wartość kwalifikatora i funkcji COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówek:** WMINet_Utils.idl

 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
