---
title: GetObjectText, funkcja (odwołanie do niezarządzanego interfejsu API)
description: Funkcja GetObjectText zwraca teksturowane renderowanie obiektu w składni MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6881125760e0f1dc38e6b01917d5829edc95e3ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176789"
---
# <a name="getobjecttext-function"></a>GetObjectText, funkcja
Zwraca teksturowane renderowanie obiektu w składni formatu obiektów zarządzanych (MOF).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[w] Normalnie 0. Jeśli `WBEM_FLAG_NO_FLAVORS` (lub 0x1) jest określony, kwalifikatory są uwzględniane bez propagacji lub informacji o smaku.

`pstrObjectText`[na zewnątrz] Wskaźnik do `null` wpisu przy wprowadzaniu. Po zwrocie nowo `BSTR` przydzielone, który zawiera renderowania składni MOF obiektu.  

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpiła ogólna porażka. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do ukończenia operacji. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemClassObject::GetObjectText.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)

Zwrócony tekst MOF nie zawiera wszystkich informacji o obiekcie, ale tylko wystarczającą ilość informacji dla kompilatora MOF, aby móc odtworzyć oryginalny obiekt. Na przykład nie propagowane kwalifikatorów lub właściwości klasy nadrzędnej są uwzględniane.

Następujący algorytm jest używany do rekonstrukcji tekstu parametrów metody:

1. Parametry są ponownie sekwencjonowane w kolejności ich wartości identyfikatorów.
1. Parametry, które `[in]` są `[out]` określone jako i są łączone w jeden parametr.

`pstrObjectText`musi być wskaźnikiem `null` do, gdy funkcja jest wywoływana; nie może wskazywać na ciąg, który jest prawidłowy przed wywołaniem metody, ponieważ wskaźnik nie zostanie cofnięty.

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
