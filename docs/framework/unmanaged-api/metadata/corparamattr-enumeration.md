---
title: CorParamAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
ms.openlocfilehash: e8afcb972cab9757458c7032c3678d45c6418fac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007575"
---
# <a name="corparamattr-enumeration"></a>CorParamAttr — Wyliczenie
Zawiera wartości opisujące metadane parametru metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`pdIn`|Określa, że parametr jest przesyłany do wywołania metody.|  
|`pdOut`|Określa, że parametr jest przesyłany z zwracanej metody.|  
|`pdOptional`|Określa, że parametr jest opcjonalny.|  
|`pdReservedMask`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`pdHasDefault`|Określa, że parametr ma wartość domyślną.|  
|`pdHasFieldMarshal`|Określa, że parametr ma informacje o kierowaniu.|  
|`pdUnused`|Nieużywany.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
