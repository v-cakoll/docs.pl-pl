---
title: CorDebugMDAFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac4a8a0c13ba6aa0d5c65ec7fa1aa3b771c964eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404862"
---
# <a name="cordebugmdaflags-enumeration"></a>CorDebugMDAFlags — Wyliczenie
Określa stan wątku, na którym jest uruchamiany zarządzany Asystent debugowania (MDA).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|Wątek, na którym zostało zainicjowane MDA jest przesuwane, ponieważ MDA zostało zainicjowane.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy stos wywołań nie opisano, gdzie MDA pierwotnie został zgłoszony, wątek jest uważany za *poślizgiem*. Jest to rzadko okoliczności spowodowanych wykonanie wątku Nieprawidłowa operacja podczas zamykania programu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
