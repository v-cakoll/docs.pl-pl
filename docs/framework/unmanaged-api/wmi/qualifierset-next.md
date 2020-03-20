---
title: funkcja QualifierSet_Next (odwołanie do interfejsu API niezarządzanego)
description: Funkcja QualifierSet_Next pobiera następny kwalifikator w wyliczeniu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174878"
---
# <a name="qualifierset_next-function"></a>QualifierSet_Next funkcja
Pobiera następny kwalifikator w wyliczeniu, który rozpoczął się od wywołania funkcji [QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md)

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>Parametry

`vFunc`[w] Ten parametr jest nieużywane.

`ptr`[w] Wskaźnik do [wystąpienia IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

`lFlags`[w] Zastrzeżone. Ten parametr musi być 0.

`pstrName`[na zewnątrz] Nazwa kwalifikatora. Jeśli `null`ten parametr jest ignorowany; w `pstrName` przeciwnym razie nie `BSTR` należy wskazywać prawidłowego lub przeciek pamięci występuje. Jeśli nie jest null, funkcja `BSTR` zawsze przydziela `WBEM_S_NO_ERROR`nowy, gdy zwraca .

`pVal`[na zewnątrz] Po pomyślnym, wartość kwalifikatora. Jeśli funkcja nie `VARIANT` powiedzie `pVal` się, wskazał przez nie jest modyfikowany. Jeśli ten `null`parametr jest , parametr jest ignorowany.

`plFlavor`[na zewnątrz] Wskaźnik do LONG, który otrzymuje smak kwalifikatora. Jeśli informacje o smaku nie są `null`pożądane, parametr ten może być .

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Dzwoniący nie zadzwonił [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna, aby rozpocząć nowe wyliczenie. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | W wyliczeniu nie ma już żadnych kwalifikatorów. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) metody.

Wywołanie `QualifierSet_Next` funkcji wielokrotnie wyliczyć wszystkie kwalifikatory, `WBEM_S_NO_MORE_DATA`aż funkcja powróci . Aby zakończyć wyliczenie wcześniej, należy wywołać funkcję [QualifierSet_EndEnumeration.](qualifierset-endenumeration.md)

Kolejność kwalifikatorów zwróconych podczas wyliczenia jest niezdefiniowana.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
