---
title: "CeeSectionAttr — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CeeSectionAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CeeSectionAttr
helpviewer_keywords: CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f0c87c0e5703f13cf843ca5a4213440af71bd12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ceesectionattr-enumeration"></a>CeeSectionAttr — Wyliczenie
Zawiera wartości, które określają atrybuty sekcji na potrzeby używania przez [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`sdNone`|Sekcja nie ma żadnych atrybutów.|  
|`sdReadOnly`|Sekcja zawiera zainicjowane dane, które mogą być tylko odczytywane, nie zaktualizowano.|  
|`sdReadWrite`|Sekcja zawiera zainicjowane dane, które można odczytać lub zaktualizować.|  
|`sdExecute`|Sekcja zawiera kod wykonywalny, który może być do odczytu i wykonywane.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
