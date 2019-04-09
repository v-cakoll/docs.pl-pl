---
title: CorSerializationType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15b1f6be2dac6bc7566852791ac22e495949521c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179634"
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType — Wyliczenie
Określa, jak obiekt jest serializowany przez środowisko uruchomieniowe języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|Serializacja obiektu nie jest zdefiniowana.|  
|`SERIALIZATION_TYPE_BOOLEAN`|Obiekt jest serializowany jako typu Boolean|  
|`SERIALIZATION_TYPE_CHAR`|Obiekt jest serializowany jako typ znaku.|  
|`SERIALIZATION_TYPE_I1`|Obiekt jest serializowany jako liczba całkowita ze znakiem 1-bajtowe.|  
|`SERIALIZATION_TYPE_U1`|Obiekt jest serializowany jako liczba całkowita bez znaku 1-bajtowe.|  
|`SERIALIZATION_TYPE_I2`|Obiekt jest serializowany jako liczba całkowita ze znakiem 2-bajtowych.|  
|`SERIALIZATION_TYPE_U2`|Obiekt jest serializowany jako liczba całkowita bez znaku 2-bajtowych.|  
|`SERIALIZATION_TYPE_I4`|Obiekt jest serializowany jako liczbę całkowitą 4-bajtowych ze znakiem.|  
|`SERIALIZATION_TYPE_U4`|Obiekt jest serializowany jako liczba całkowita bez znaku 4-bajtowe.|  
|`SERIALIZATION_TYPE_I8`|Obiekt jest serializowany jako liczba całkowita 8-bajtowych ze znakiem.|  
|`SERIALIZATION_TYPE_U8`|Obiekt jest serializowany jako liczba całkowita 8 bajtów bez znaku.|  
|`SERIALIZATION_TYPE_R4`|Obiekt jest serializowany jako 4-bajtowych zmiennoprzecinkowych.|  
|`SERIALIZATION_TYPE_R8`|Obiekt jest serializowany jako 8-bajtowych wartości zmiennoprzecinkowych.|  
|`SERIALIZATION_TYPE_STRING`|Obiekt jest serializowany jako typ System.String.|  
|`SERIALIZATION_TYPE_SZARRAY`|Obiekt jest serializowany jako jednowymiarowe, zerowego dolną granicę tablicy.|  
|`SERIALIZATION_TYPE_TYPE`|Obiekt jest serializowany jako typu ogólnego.|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|Obiekt jest serializowany jako obiekt oznakowane.|  
|`SERIALIZATION_TYPE_FIELD`|Obiekt jest serializowany jako pole.|  
|`SERIALIZATION_TYPE_PROPERTY`|Obiekt jest serializowany jako właściwość.|  
|`SERIALIZATION_TYPE_ENUM`|Obiekt jest serializowany jako wyliczenie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
