---
title: CorSetENC — Wyliczenie
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2796be32154275387da891683cc5053095f534af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772324"
---
# <a name="corsetenc-enumeration"></a>CorSetENC — Wyliczenie
Zawiera wartości używane do wywierania wpływu na zachowanie podczas generowania metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`MDUpdateENC`|Wskazuje, że może zostać uaktualnione metadane, tokeny nie mogą być przenoszone.|  
|`MDUpdateFull`|Wskazuje, że tokeny mogą być przenoszone podczas aktualizacji.|  
|`MDUpdateExtension`|Wskazuje, że aktualizacje może składać się tylko z dodatków. Nie można przenieść tokenów.|  
|`MDUpdateIncremental`|Wskazuje, że kompilacja jest przyrostowe.|  
|`MDUpdateDelta`|Wskazuje, że powinny być zapisywane tylko zmienione metadane.|  
|`MDUpdateMask`|Obejmuje `MDUpdateENC`, `MDUpdateFull` i `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
