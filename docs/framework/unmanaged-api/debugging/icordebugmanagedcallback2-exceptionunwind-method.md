---
title: "ICorDebugManagedCallback2::ExceptionUnwind — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ExceptionUnwind
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45b9f5838e4bc98e3f269a2cebd575abfe998a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind — Metoda
Udostępnia powiadomienia o stanie podczas procesu odwijaniem wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające wątku, w którym został zgłoszony wyjątek.  
  
 `pThread`  
 [in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, w którym został zgłoszony wyjątek.  
  
 `dwEventType`  
 [in] Wartość wyliczenia CorDebugExceptionUnwindCallbackType określający sygnalizowane trwa przez wywołanie zwrotne w fazie unwind zdarzenia.  
  
 `dwFlags`  
 [in] Wartość [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wyliczenia, która określa dodatkowe informacje o wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `ExceptionUnwind`jest wywoływana w różnych punktach w fazie unwind procesu obsługi wyjątków. `ExceptionUnwind`można wywołać więcej niż raz podczas rozwinięcia jeden wyjątek.  
  
 Jeśli `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, wskaźnik instrukcji będą znajdować się w wątku, w momencie sekwencji przed ramki typu liść (może to być kilka instrukcje przed) instrukcji, które spowodowało wyjątek.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugManagedCallback2 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
