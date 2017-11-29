---
title: "ICorDebugManagedCallback::ControlCTrap — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ControlCTrap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df6aab0f8f220e53c8aab0d40a8b300d95822068
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a>ICorDebugManagedCallback::ControlCTrap — Metoda
Powiadamia debugera, że w procesie, który jest debugowany jest kolor CTRL + C.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProcess`  
 [in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, w którym jest kolor CTRL + C.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Debuger będzie obsługiwać pułapki klawisze CTRL + C.|  
|WARTOŚCI S_FALSE|Debuger nie będzie obsługiwać pułapki klawisze CTRL + C.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkich domen aplikacji w ramach procesu zostały zatrzymane dla tego wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugManagedCallback — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
