---
title: "COR_VERSION — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_VERSION
helpviewer_keywords: COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd4a878b51685befb39eb486097be2e2f2c1d409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corversion-structure"></a>COR_VERSION — Struktura
Przechowuje numer wersji czteroczęściową standardowe środowisko uruchomieniowe języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`dwMajor`|Główny numer wersji.|  
|`dwMinor`|Pomocniczy numer wersji.|  
|`dwBuild`|Numer kompilacji.|  
|`dwSubBuild`|Numer kompilacji podrzędnych.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli numer wersji jest 1.0.3705.288, główny numer wersji jest 1, 0 jest podrzędny numer wersji 3705 jest numer kompilacji i 288 jest numer kompilacji podrzędnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
