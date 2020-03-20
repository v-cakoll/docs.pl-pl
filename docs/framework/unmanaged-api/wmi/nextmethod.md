---
title: NextMethod, funkcja (odwołanie do interfejsu API niezarządzanego)
description: NextMethod Funkcja pobiera następną metodę w wyliczenia.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 36acd6135110a8865bd8efdda628c352c01b4f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174930"
---
# <a name="nextmethod-function"></a>NextMetoda, funkcja
Pobiera następną metodę w wyliczeniu, która rozpoczyna się od wywołania [BeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[w] Zastrzeżone. Ten parametr musi być 0.

`pName`  
[na zewnątrz] Wskaźnik wskazujący `null` przed wywołaniem. Gdy funkcja zwraca, adres nowego, `BSTR` który zawiera nazwę metody.

`ppSignatureIn`  
[na zewnątrz] Wskaźnik, który odbiera wskaźnik do [IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) który zawiera `in` parametry dla metody.

`ppSignatureOut`  
[na zewnątrz] Wskaźnik, który odbiera wskaźnik do [IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) który zawiera `out` parametry dla metody.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Nie było żadnego [`BeginEnumeration`](beginenumeration.md) wywołania funkcji. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Nie ma więcej właściwości w wyliczeniu. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemClassObject::NextMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)

Wywołujący rozpoczyna sekwencję wyliczenia, wywołując [BeginMethodEnumeration,](beginmethodenumeration.md) a następnie wywołuje funkcję [NextMethod], aż funkcja powróci `WBEM_S_NO_MORE_DATA`. Opcjonalnie wywołujący kończy sekwencję, wywołując [EndMethodEnumeration](endmethodenumeration.md). Wywołujący może zakończyć wyliczenie wcześnie wywołując [EndMethodEnumeration](endmethodenumeration.md) w dowolnym momencie.

## <a name="example"></a>Przykład

Przykład C++ można znaleźć w metodzie [IWbemClassObject::NextMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
