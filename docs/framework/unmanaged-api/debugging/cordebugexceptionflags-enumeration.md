---
title: "CorDebugExceptionFlags — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionFlags
helpviewer_keywords: CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35444a73a5d3b5d71a1aa991dbebc3e7da705292
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags — Wyliczenie
Zawiera dodatkowe informacje o wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|Nie ma żadnych wyjątków.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|Wyjątek stanowi interceptable.<br /><br /> Czas wyjątku może nadal być w taki sposób, że debuger nie może przechwycić go. Na przykład jeśli nie istnieje żaden kod zarządzany poniżej bieżącego wywołania zwrotnego lub zdarzenie wyjątku jest wynikiem just in time (JIT) załącznika, wyjątek nie może zostać przechwycone.|  
  
## <a name="remarks"></a>Uwagi  
 Nowe wartości mogą zostać dodane do tego wyliczenia w nowszych wersjach, więc należy przygotować kodu korzystającego z `CorDebugExceptionFlags` nieoczekiwane wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie — wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
