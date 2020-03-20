---
title: InheritsFrom, funkcja (odwołanie do interfejsu API niezarządzanego)
description: InheritsFrom Funkcja określa, czy klasa lub wystąpienie pochodzi z określonej klasy nadrzędnej.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c735c01c45beda8a1ba988a5c580e6b04ae46312
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174943"
---
# <a name="inheritsfrom-function"></a>InheritsFrom, funkcja
Określa, czy bieżąca klasa lub wystąpienie pochodzi od określonej klasy nadrzędnej.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszAncestor`  
[w] Nazwa klasy. `wszAncestor`musi wskazywać prawidłowe `LPCWSTR`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | Bieżący obiekt dziedziczy z pliku `wszAncestor`.  |
| `WBEM_S_FALSE` | 1 | Bieżący obiekt nie `wszAncestor`dziedziczy po pliku . |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr `wszAncestor` ma wartość `null`. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemClassObject::InheritsFrom.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom)

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
