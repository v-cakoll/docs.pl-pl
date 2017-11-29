---
title: "CorErrorIfEmitOutOfOrder — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorErrorIfEmitOutOfOrder
api_location: mscoree.dll
api_type: COM
f1_keywords: CorErrorIfEmitOutOfOrder
helpviewer_keywords: CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2cf80375622912c6bb9a59696f37aed2d594253
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder — Wyliczenie
Zawiera wartości flagi, które określają warunki, w których ma być generowany metadanych jest emitowany poza kolejnością komunikat o błędzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`MDErrorOutOfOrderDefault`|Wskazuje zachowanie domyślne, który nie generuje komunikaty o błędach.|  
|`MDErrorOutOfOrderNone`|Wskazuje, że kompilator nie powinna generować komunikaty o błędach.|  
|`MDErrorOutOfOrderAll`|Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy pola, właściwości, zdarzenia, metody lub parametru jest emitowany poza kolejnością.|  
|`MDMethodOutOfOrder`|Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy metoda jest emitowany poza kolejnością.|  
|`MDFieldOutOfOrder`|Wskazuje, że kompilator powinien generować komunikat o błędzie, jeśli pole jest emitowany poza kolejnością.|  
|`MDParamOutOfOrder`|Wskazuje, że kompilator powinien generować komunikat o błędzie, jeśli parametr jest emitowany poza kolejnością.|  
|`MDPropertyOutOfOrder`|Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy właściwość jest emitowany poza kolejnością.|  
|`MDEventOutOfOrder`|Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy zdarzenie jest emitowany poza kolejnością.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
