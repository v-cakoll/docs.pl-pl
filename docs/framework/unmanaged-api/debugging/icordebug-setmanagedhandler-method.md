---
title: "ICorDebug::SetManagedHandler — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.SetManagedHandler
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06f0989058ed21e736fde0aee5f1cd1dd66e0ca8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler — Metoda
Określa obiekt programu obsługi zdarzeń dla zdarzeń zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallback`  
 [in] Wskaźnik do [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) obiektu, który jest obiektem programu obsługi zdarzeń.  
  
## <a name="remarks"></a>Uwagi  
 `SetManagedHandler`musi zostać wywołana w czasie tworzenia.  
  
 Jeśli `ICorDebugManagedCallback` implementacji nie zawiera wystarczających interfejsy do obsługi zdarzeń debugowania dla aplikacji, która jest debugowana, `SetManagedHandler` zwraca HRESULT E_NOINTERFACE.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
