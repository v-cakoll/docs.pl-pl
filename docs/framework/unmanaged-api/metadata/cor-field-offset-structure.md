---
title: COR_FIELD_OFFSET — Struktura
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 70fb637cd1edf81be140b0e3306e3b0a483653a6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007991"
---
# <a name="cor_field_offset-structure"></a>COR_FIELD_OFFSET — Struktura
Zapisuje przesunięcie w obrębie klasy w określonym polu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`ridOfField`|`mdFieldDef`Token metadanych reprezentujący pole.|  
|`ulOffset`|Przesunięcie pola w swojej klasie.|  
  
## <a name="remarks"></a>Uwagi  
 [IMetaDataImport:: GetClassLayout —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) i [IMetaDataEmit:: SetClassLayout —](imetadataemit-setclasslayout-method.md) Metoda przyjmuje parametr typu `COR_FIELD_OFFSET` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h, CorProf. idl  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury metadanych](metadata-structures.md)
- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
