---
title: CorMethodSemanticsAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e36cb91c3ef741badb04b54e2b62158ecf6ced1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134501"
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr — Wyliczenie
Zawiera wartości, które opisują relację między metodą i skojarzonej właściwości lub zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`msSetter`|Określa, że metoda jest `set` akcesora dla właściwości.|  
|`msGetter`|Określa, że metoda jest `get` akcesora dla właściwości.|  
|`msOther`|Określa, że metoda ma relację z właściwości lub zdarzenia inne niż te zdefiniowane w tym miejscu.|  
|`msAddOn`|Określa, że metoda dodaje metody obsługi zdarzeń.|  
|`msRemoveOn`|Określa, że metoda usuwa metody obsługi zdarzeń.|  
|`msFire`|Określa, że metoda wywołuje zdarzenie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
