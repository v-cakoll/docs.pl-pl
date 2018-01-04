---
title: "CorSerializationType — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSerializationType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSerializationType
helpviewer_keywords: CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e43151b1611f5b9b8218d30ba46a9143f463c193
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
|`SERIALIZATION_TYPE_BOOLEAN`|Serializowany jest obiekt jako typ Boolean|  
|`SERIALIZATION_TYPE_CHAR`|Serializowany jest obiekt jako typ znaków.|  
|`SERIALIZATION_TYPE_I1`|Serializowany jest obiekt jako całkowita 1-bajtowego.|  
|`SERIALIZATION_TYPE_U1`|Serializowany jest obiekt jako liczba całkowita bez znaku 1-bajtowego.|  
|`SERIALIZATION_TYPE_I2`|Serializowany jest obiekt jako całkowita 2-bajtowych.|  
|`SERIALIZATION_TYPE_U2`|Serializowany jest obiekt jako liczba całkowita bez znaku 2-bajtowych.|  
|`SERIALIZATION_TYPE_I4`|Serializowany jest obiekt jako 4-bajtowych liczbę całkowitą ze znakiem.|  
|`SERIALIZATION_TYPE_U4`|Serializowany jest obiekt jako liczba całkowita bez znaku 4-bajtowych.|  
|`SERIALIZATION_TYPE_I8`|Serializowany jest obiekt jako całkowita 8-bajtowych.|  
|`SERIALIZATION_TYPE_U8`|Serializowany jest obiekt jako liczba całkowita bez znaku 8-bajtowych.|  
|`SERIALIZATION_TYPE_R4`|Serializowany jest obiekt jako 4-bajtowych zmiennoprzecinkowych.|  
|`SERIALIZATION_TYPE_R8`|Serializowany jest obiekt jako 8-bajtowych wartości zmiennoprzecinkowych.|  
|`SERIALIZATION_TYPE_STRING`|Serializowany jest obiekt jako typu System.String.|  
|`SERIALIZATION_TYPE_SZARRAY`|Serializowany jest obiekt jako jednowymiarowe, zero dolna granica tablicy.|  
|`SERIALIZATION_TYPE_TYPE`|Serializowany jest obiekt jako typu ogólnego.|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|Jako obiekt oznakowanych serializowany jest obiekt.|  
|`SERIALIZATION_TYPE_FIELD`|Serializowany jest obiekt jako pole.|  
|`SERIALIZATION_TYPE_PROPERTY`|Jako właściwość serializowany jest obiekt.|  
|`SERIALIZATION_TYPE_ENUM`|Jako wyliczenie serializowany jest obiekt.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
