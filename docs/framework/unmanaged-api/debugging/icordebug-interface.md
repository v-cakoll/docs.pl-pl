---
title: ICorDebug — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74c5036bdc8a4a75e5711c6dc1d34d8f2c21128f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebug-interface"></a>ICorDebug — Interfejs
Udostępnia metody, które umożliwiają deweloperom debugowanie aplikacji w środowisku środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.  
  
> [!NOTE]
>  Debugowanie trybu mieszanego (kodu zarządzanego i natywnego) nie jest obsługiwane w systemie Windows 95, Windows 98 lub Windows ME lub na platformach innych niż x86 (na przykład IA64 i AMD64).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanLaunchOrAttach, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Określa, czy uruchamianie nowego procesu lub dołączanie do procesu danego jest możliwe w kontekście bieżącej konfiguracji komputera i środowiska uruchomieniowego.|  
|[CreateProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Uruchamia proces i jego podstawowym wątku pod kontrolą debugera.|  
|[DebugActiveProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Dołącza debuger do istniejącego procesu.|  
|[EnumerateProcesses, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Pobiera moduł wyliczający dla procesów, które są debugowane.|  
|[GetProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Zwraca obiekt "ICorDebugProcess" z identyfikatorem danego procesu.|  
|[Initialize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|Inicjuje `ICorDebug` obiektu.|  
|[SetManagedHandler, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Określa obiekt programu obsługi zdarzeń dla zdarzeń zarządzanych.|  
|[SetUnmanagedHandler, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Określa obiekt programu obsługi zdarzeń dla niezarządzanego zdarzeń.|  
|[Terminate, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|Kończy `ICorDebug` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebug` reprezentuje pętli przetwarzania zdarzeń dla procesu debugera. Debuger musi czekać, aż [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) wywołania zwrotnego od wszystkich procesów debugowany przed wydaniem tego interfejsu.  
  
 `ICorDebug` Obiekt jest obiektem początkowej do sterowania wszystkie dalsze zarządzane debugowania. W wersji systemu .NET Framework 1.0 i 1.1, ten obiekt był `CoClass` obiektu utworzone na podstawie modelu COM. W programie .NET Framework w wersji 2.0, ten obiekt nie jest już `CoClass` obiektu. Musi być utworzony przez [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkcji, która jest bardziej wersji obsługujących. Ta nowa funkcja tworzenia umożliwia klientom uzyskanie określonej implementacji `ICorDebug`, które również emuluje określoną wersję interfejsu API debugowania.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
