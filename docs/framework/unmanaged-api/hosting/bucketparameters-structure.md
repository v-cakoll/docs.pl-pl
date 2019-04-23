---
title: BucketParameters — Struktura
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5998ce684726b2386d8f1e05eb7eaeccf455747c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110459"
---
# <a name="bucketparameters-structure"></a>BucketParameters — Struktura
Przechowuje nazwę typu zdarzenia i parametry dla bieżącego wyjątku, który jest skojarzony ze zdarzeniem.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`fInited`|`true`, jeśli pozostałą część tej struktury jest prawidłowy; w przeciwnym razie `false`.|  
|`pszEventTypeName`|Nazwa typu zdarzenia.|  
|`pszParams`|Tablica ciągów, z których każdy określa parametr dla bieżącego wyjątku skojarzonego ze zdarzeniem.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
