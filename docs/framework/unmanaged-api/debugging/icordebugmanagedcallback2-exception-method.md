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
ms.openlocfilehash: faefff879142d66c4c596f1b30a25e349a4014b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421804"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception — Metoda
Powiadamia debuger rozpoczęto wyszukiwanie obsługi wyjątków.  
  
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
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające wątku, w którym został zgłoszony wyjątek.  
  
 `pThread`  
 [in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, w którym został zgłoszony wyjątek.  
  
 `pFrame`  
 [in] Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę, zgodnie z ustaleniami `dwEventType` parametru. Aby uzyskać więcej informacji zobacz tabelę w sekcji uwag.  
  
 `nOffset`  
 [in] Liczba całkowita, która określa przesunięcie, zgodnie z ustaleniami `dwEventType` parametru. Aby uzyskać więcej informacji zobacz tabelę w sekcji uwag.  
  
 `dwEventType`  
 [in] Wartość wyliczenia CorDebugExceptionCallbackType, który określa typ wywołania zwrotnego tego wyjątku.  
  
 `dwFlags`  
 [in] Wartość [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wyliczenia, która określa dodatkowe informacje o wyjątku  
  
## <a name="remarks"></a>Uwagi  
 `Exception` Wywołania zwrotnego jest wywoływana w różnych punktach w fazie wyszukiwania procesu obsługi wyjątków. Oznacza to, że jego można wywołać więcej niż raz podczas rozwinięcia Wystąpił wyjątek.  
  
 Wyjątek przetwarzanych mogą być pobierane z obiektu ICorDebugThread odwołuje się `pThread` parametru.  
  
 Klatek i przesunięcie są określane przez `dwEventType` parametru w następujący sposób:  
  
|Wartość `dwEventType`|Wartość `pFrame`|Wartość `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Ramka, która zgłosiła wyjątek.|Wskaźnik instrukcji w ramce.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Kod użytkownika ramka najbliższy punkt zwrócony wyjątek.|Wskaźnik instrukcji w ramce.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Ramki, która zawiera obsługi catch.|Przesunięcie język pośredni (MSIL) firmy Microsoft na początku obsługi catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Niezdefiniowana.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugManagedCallback2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
