---
title: "CorDebugNGenPolicy — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugNGenPolicy
helpviewer_keywords: CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89767da7178319ed1add3dda0620062893487bfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy — Wyliczenie
Zawiera wartość, która określa, czy debuger ładuje obrazów natywnych (NGen) z pamięci podręcznej obrazów natywnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|W [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikacji, użyj obrazów z pamięci podręcznej obrazów natywnych lokalnej jest wyłączona. W aplikacji komputerowej to ustawienie nie ma żadnego skutku.|  
  
## <a name="remarks"></a>Uwagi  
 `CorDebugNGENPolicy` Wyliczenie jest używany przez [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metody. Wyłączanie korzystania z obrazów z pamięci podręcznej obrazów natywnych lokalnej zapewnia spójne środowisko debugowania przez zapewnienie, że debuger ładuje możliwością debugowania kompilacji JIT obrazów zamiast zoptymalizowane obrazów macierzystych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
