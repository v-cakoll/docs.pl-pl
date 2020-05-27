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
ms.openlocfilehash: 649a9159f99afa64615c40c23a98a80318ae0d7f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009174"
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType — Wyliczenie
Określa, jak obiekt jest serializowany przez środowisko uruchomieniowe języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|Serializacja obiektu jest niezdefiniowana.|  
|`SERIALIZATION_TYPE_BOOLEAN`|Obiekt jest serializowany jako typ Boolean|  
|`SERIALIZATION_TYPE_CHAR`|Obiekt jest serializowany jako typ znaku.|  
|`SERIALIZATION_TYPE_I1`|Obiekt jest serializowany jako 1-bajtowa liczba całkowita ze znakiem.|  
|`SERIALIZATION_TYPE_U1`|Serializacja obiektu jest serializowana jako 1-bajtowa liczba całkowita bez znaku.|  
|`SERIALIZATION_TYPE_I2`|Obiekt jest serializowany jako 2-bajtowa liczba całkowita ze znakiem.|  
|`SERIALIZATION_TYPE_U2`|Serializacja obiektu jest serializowana jako 2-bajtowa liczba całkowita bez znaku.|  
|`SERIALIZATION_TYPE_I4`|Serializacja obiektu jest serializowana jako 4-bajtowa liczba całkowita.|  
|`SERIALIZATION_TYPE_U4`|Serializacja obiektu jest serializowana jako 4-bajtowa liczba całkowita bez znaku.|  
|`SERIALIZATION_TYPE_I8`|Obiekt jest serializowany jako 8-bajtowa liczba całkowita ze znakiem.|  
|`SERIALIZATION_TYPE_U8`|Serializacja obiektu jest serializowana jako 8-bajtowa liczba całkowita bez znaku.|  
|`SERIALIZATION_TYPE_R4`|Serializacja obiektu jest serializowana jako 4-bajtowy zmiennoprzecinkowy.|  
|`SERIALIZATION_TYPE_R8`|Serializacja obiektu jest serializowana jako 8-bajtowy zmiennoprzecinkowy.|  
|`SERIALIZATION_TYPE_STRING`|Obiekt jest serializowany jako typ System. String.|  
|`SERIALIZATION_TYPE_SZARRAY`|Serializacja obiektu jest serializowana jako tablica Jednowymiarowa o zerowej granicy.|  
|`SERIALIZATION_TYPE_TYPE`|Serializacja obiektu jest typem ogólnym.|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|Obiekt jest serializowany jako obiekt otagowany.|  
|`SERIALIZATION_TYPE_FIELD`|Obiekt jest serializowany jako pole.|  
|`SERIALIZATION_TYPE_PROPERTY`|Obiekt jest serializowany jako właściwość.|  
|`SERIALIZATION_TYPE_ENUM`|Obiekt jest serializowany jako Wyliczenie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
