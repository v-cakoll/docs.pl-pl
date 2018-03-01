---
title: "CorSetENC — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f39a1481361377fce3f6b55cf6c7daf8c075ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corsetenc-enumeration"></a>CorSetENC — Wyliczenie
Zawiera wartości używane do wpływają na zachowanie podczas generowania metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDSetENCOn`|Nieaktualne.|  
|`MDSetENCOff`|Nieaktualne.|  
|`MDUpdateENC`|Wskazuje, że metadane mogą zostać uaktualnione, tokenów nie może zostać przeniesiona.|  
|`MDUpdateFull`|Wskazuje, że tokeny mogą być przenoszone podczas aktualizacji.|  
|`MDUpdateExtension`|Wskazuje, że aktualizacje może składać się tylko z dodatków. Nie można przenieść tokenów.|  
|`MDUpdateIncremental`|Wskazuje, czy kompilacja jest przyrostowe.|  
|`MDUpdateDelta`|Wskazuje, że ma zostać zapisany tylko metadane zmienione.|  
|`MDUpdateMask`|Obejmuje `MDUpdateENC`, `MDUpdateFull` i `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
