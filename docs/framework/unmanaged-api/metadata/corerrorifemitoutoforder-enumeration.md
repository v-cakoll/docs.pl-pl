---
title: CorErrorIfEmitOutOfOrder — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: 57460ba30a8ce974b5ca89f76796c4dcf49ffecf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443587"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder — Wyliczenie
Zawiera wartości flag, które wskazują warunki, w których komunikat o błędzie powinien zostać wygenerowany, gdy metadane są emitowane poza kolejnością.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|Wskazuje zachowanie domyślne, które nie generuje komunikatów o błędach.|  
|`MDErrorOutOfOrderNone`|Wskazuje, że kompilator nie powinien generować komunikatów o błędach.|  
|`MDErrorOutOfOrderAll`|Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy pole, właściwość, zdarzenie, metoda lub parametr są emitowane poza kolejnością.|  
|`MDMethodOutOfOrder`|Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy metoda jest emitowana poza kolejnością.|  
|`MDFieldOutOfOrder`|Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy pole jest emitowane poza kolejnością.|  
|`MDParamOutOfOrder`|Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy parametr jest emitowany poza kolejnością.|  
|`MDPropertyOutOfOrder`|Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy właściwość jest emitowana poza kolejnością.|  
|`MDEventOutOfOrder`|Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy zdarzenie jest emitowane poza kolejnością.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
