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
ms.openlocfilehash: 1572c206f4a5a5fe0fd189ca84d0bcda2249c6d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007653"
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr — Wyliczenie
Zawiera wartości opisujące relacje między metodą a skojarzoną właściwością lub zdarzeniem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`msSetter`|Określa, że metoda jest `set` akcesorem dla właściwości.|  
|`msGetter`|Określa, że metoda jest `get` akcesorem dla właściwości.|  
|`msOther`|Określa, że metoda ma relację z właściwością lub zdarzeniem innym niż zdefiniowane w tym miejscu.|  
|`msAddOn`|Określa, że Metoda dodaje metody obsługi dla zdarzenia.|  
|`msRemoveOn`|Określa, że metoda usuwa metody obsługi dla zdarzenia.|  
|`msFire`|Określa, że metoda wywołuje zdarzenie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
