---
title: EndMethodEnumeration, funkcja (odwołanie do interfejsu API niezarządzanego)
description: EndMethodEnumeration Funkcja kończy sekwencję wyliczenia metody.
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 63667d0668f905ded2aedd961be0d1831faf838c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175008"
---
# <a name="endmethodenumeration-function"></a>EndMethodEnumeration, funkcja
Kończy sekwencję wyliczenia rozpoczętą wywołaniem [funkcji BeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | 0x8004101d | Wystąpił błąd wewnętrzny. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemClassObject::EndMethodEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration)

Wywołujący rozpoczyna sekwencję wyliczenia za pomocą [funkcji BeginMethodEnumeration](beginmethodenumeration.md), a następnie `WBEM_S_NO_MORE_DATA`wywołuje funkcję [NextMethod,](nextmethod.md )dopóki metoda nie zwróci . Wywołujący opcjonalnie kończy sekwencję `EndMethodEnumeration`przez wywołanie . Wywołujący może zakończyć wyliczenie wcześnie, wywołując `EndMethodEnumeration` w dowolnym momencie.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
