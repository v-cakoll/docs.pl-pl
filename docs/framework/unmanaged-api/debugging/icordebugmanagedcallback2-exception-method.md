---
title: ICorDebugManagedCallback2::Exception — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d46dcd43ffe6963d1177a395b855a287182cdff0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685636"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception — Metoda
Powiadamia debuger rozpoczęto wyszukiwania dla obsługi wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą wątku, na którym wystąpił wyjątek.  
  
 `pThread`  
 [in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, na którym wystąpił wyjątek.  
  
 `pFrame`  
 [in] Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę, zgodnie z ustaleniami `dwEventType` parametru. Aby uzyskać więcej informacji zobacz tabelę w sekcji uwag.  
  
 `nOffset`  
 [in] Liczba całkowita, która określa przesunięcie, zgodnie z ustaleniami `dwEventType` parametru. Aby uzyskać więcej informacji zobacz tabelę w sekcji uwag.  
  
 `dwEventType`  
 [in] Wartość cordebugexceptioncallbacktype — wyliczenie, który określa typ to wywołanie zwrotne wyjątku.  
  
 `dwFlags`  
 [in] Wartość [cordebugexceptionflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wyliczenie, które określa dodatkowe informacje o wyjątku  
  
## <a name="remarks"></a>Uwagi  
 `Exception` Wywołanie zwrotne jest wywoływane na różnych etapach procesu obsługi wyjątków w fazie wyszukiwania. Oznacza to jego może być wywoływana więcej niż jeden raz podczas odwijanie wyjątków.  
  
 Wyjątek przetwarzane można pobrać z zawiera odwołanie do obiektu ICorDebugThread `pThread` parametru.  
  
 Ramki określonego i przesunięcia, są określane przez `dwEventType` parametru w następujący sposób:  
  
|Wartość `dwEventType`|Wartość `pFrame`|Wartość `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Ramka, która zgłosiła wyjątek.|Wskaźnik instrukcji w ramce.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Ramka kod użytkownika najbliższy punkt zgłoszony wyjątek.|Wskaźnik instrukcji w ramce.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Ramki, który zawiera program obsługi catch.|Microsoft intermediate language (MSIL) Przesunięcie początku obsługi catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Nie zdefiniowano.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugManagedCallback2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
