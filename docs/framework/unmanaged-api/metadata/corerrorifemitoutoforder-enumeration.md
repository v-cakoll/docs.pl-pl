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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16f6d7bf6fa1730d50cfe81526817e492a453dad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781987"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder — Wyliczenie
Zawiera wartości flagi, które określają warunki, w których mają być generowane metadanych jest emitowane poza kolejnością komunikat o błędzie.  
  
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
|`MDErrorOutOfOrderDefault`|Wskazuje zachowanie domyślne, które generują komunikaty o błędach.|  
|`MDErrorOutOfOrderNone`|Wskazuje, że kompilator nie powinna generować komunikaty o błędach.|  
|`MDErrorOutOfOrderAll`|Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy pola, właściwości, zdarzenia, metody lub parametru jest emitowane poza kolejnością.|  
|`MDMethodOutOfOrder`|Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy metoda jest emitowane poza kolejnością.|  
|`MDFieldOutOfOrder`|Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy pole jest emitowane poza kolejnością.|  
|`MDParamOutOfOrder`|Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy parametr jest emitowane poza kolejnością.|  
|`MDPropertyOutOfOrder`|Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy właściwość jest emitowana poza kolejnością.|  
|`MDEventOutOfOrder`|Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy zdarzenie jest emitowane poza kolejnością.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
