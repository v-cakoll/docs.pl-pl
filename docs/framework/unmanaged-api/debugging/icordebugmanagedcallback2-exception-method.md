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
ms.openlocfilehash: e7125d923fb1d3757bb4ca53f5a7db806b241dd9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781532"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception — Metoda
Powiadamia debugera o rozpoczęciu wyszukiwania programu obsługi wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą wątek, w którym został zgłoszony wyjątek.  
  
 `pThread`  
 podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym został zgłoszony wyjątek.  
  
 `pFrame`  
 podczas Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę określoną przez parametr `dwEventType`. Aby uzyskać więcej informacji, zobacz tabelę w sekcji uwagi.  
  
 `nOffset`  
 podczas Liczba całkowita, która określa przesunięcie, zgodnie z parametrem `dwEventType`. Aby uzyskać więcej informacji, zobacz tabelę w sekcji uwagi.  
  
 `dwEventType`  
 podczas Wartość wyliczenia CorDebugExceptionCallbackType —, która określa typ tego wywołania zwrotnego wyjątku.  
  
 `dwFlags`  
 podczas Wartość wyliczenia [CorDebugExceptionFlags —](cordebugexceptionflags-enumeration.md) , która określa dodatkowe informacje o wyjątku  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie zwrotne `Exception` jest wywoływane w różnych punktach w fazie wyszukiwania procesu obsługi wyjątków. Oznacza to, że może być wywoływana więcej niż jeden raz podczas odwinięcia wyjątku.  
  
 Przetwarzany wyjątek można pobrać z obiektu ICorDebugThread, do którego odwołuje się parametr `pThread`.  
  
 Konkretna ramka i przesunięcie są określane przez parametr `dwEventType` w następujący sposób:  
  
|Wartość `dwEventType`|Wartość `pFrame`|Wartość `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Ramka, która wywołała wyjątek.|Wskaźnik instrukcji w ramce.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Ramka kodu użytkownika najbliżej punktu zgłoszonego wyjątku.|Wskaźnik instrukcji w ramce.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Ramka, która zawiera procedurę obsługi catch.|Przesunięcie języka pośredniego firmy Microsoft (MSIL) od początku procedury obsługi catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Definicji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback2, interfejs](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interfejs](icordebugmanagedcallback-interface.md)
