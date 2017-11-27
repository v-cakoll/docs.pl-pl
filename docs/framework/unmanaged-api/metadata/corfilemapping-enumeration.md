---
title: "CorFileMapping — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFileMapping
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFileMapping
helpviewer_keywords: CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6736f154ef6b03c0bfe34d16a419955324316273
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping — Wyliczenie
Zawiera wartości, które opisują typ mapowania pliku, która jest zwracana w wyniku wywołania [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`fmFlat`|Plik jest mapowany jako plik danych. Oznacza to `SEC_IMAGE` flagi nie został przekazany do Microsoft Win32 `CreateFileMapping` funkcji.|  
|`fmExecutableImage`|Plik jest zamapowana do wykonania, za pomocą `LoadLibrary` funkcji lub `CreateFileMapping` działać z `SEC_IMAGE` flagi.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [GetFileMapping — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
