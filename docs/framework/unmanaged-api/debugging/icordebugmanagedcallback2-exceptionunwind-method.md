---
title: ICorDebugManagedCallback2::ExceptionUnwind — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: 482afd09ce370fb1247864b9ac2032ee7e3a1dca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788276"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind — Metoda
Udostępnia powiadomienie o stanie podczas procesu odwracania wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą wątek, w którym został zgłoszony wyjątek.  
  
 `pThread`  
 podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym został zgłoszony wyjątek.  
  
 `dwEventType`  
 podczas Wartość wyliczenia CorDebugExceptionUnwindCallbackType —, która określa zdarzenie, które jest sygnalizowane przez wywołanie zwrotne w fazie unwind.  
  
 `dwFlags`  
 podczas Wartość wyliczenia [CorDebugExceptionFlags —](cordebugexceptionflags-enumeration.md) , która określa dodatkowe informacje o wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `ExceptionUnwind` jest wywoływana w różnych punktach w fazie unwind procesu obsługi wyjątków. `ExceptionUnwind` może być wywoływana więcej niż jeden raz podczas odwinięcia pojedynczego wyjątku.  
  
 Jeśli `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, wskaźnik instrukcji będzie znajdować się w ramce liścia wątku, w punkcie sekwencji przed (może to być kilka instrukcji przed) instrukcją, która doprowadziła do wyjątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback2, interfejs](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interfejs](icordebugmanagedcallback-interface.md)
