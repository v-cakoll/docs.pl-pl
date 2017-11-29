---
title: "ICorDebug::EnumerateProcesses — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.EnumerateProcesses
api_location: mscordbi.dll
api_type: COM
f1_keywords: EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e48bc47945bc6c77758eeaa8597ad0ce57b72689
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugenumerateprocesses-method"></a>ICorDebug::EnumerateProcesses — Metoda
Pobiera moduł wyliczający dla procesów, które są debugowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppProcess`  
 Wskaźnik do adresu ICorDebugProcessEnum obiektu, który moduł wyliczający dla procesów debugowany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
