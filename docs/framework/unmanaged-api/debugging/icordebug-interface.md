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
ms.openlocfilehash: 193232ce1006a9cf209db9330343386404948440
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786337"
---
# <a name="icordebug-interface"></a>ICorDebug — Interfejs
Udostępnia metody, które umożliwiają deweloperom debugowanie aplikacji w środowisku uruchomieniowym języka wspólnego (CLR).  
  
> [!NOTE]
>  Debugowanie trybu mieszanego (kodu zarządzanego i natywnego) nie jest obsługiwana na Windows 95, Windows 98 lub Windows ME lub na platformach innych niż x86 (na przykład IA64 i AMD64).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanLaunchOrAttach, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Określa, czy uruchamianie nowego procesu lub dołączanie do danego procesu jest możliwe w kontekście bieżącej konfiguracji komputera i środowiska uruchomieniowego.|  
|[CreateProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Uruchamia proces i jego podstawowym wątku pod kontrolą debugera.|  
|[DebugActiveProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Dołącza debuger do istniejącego procesu.|  
|[EnumerateProcesses, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Pobiera moduł wyliczający dla procesów, które są debugowane.|  
|[GetProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Zwraca obiekt "ICorDebugProcess" o identyfikatorze danego procesu.|  
|[Initialize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|Inicjuje `ICorDebug` obiektu.|  
|[SetManagedHandler, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Określa obiekt programu obsługi zdarzeń dla zdarzeń zarządzanych.|  
|[SetUnmanagedHandler, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Określa obiekt programu obsługi zdarzeń dla zdarzenia niezarządzane.|  
|[Terminate, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|Kończy `ICorDebug` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebug` reprezentuje pętlę przetwarzania zdarzeń dla procesu, debuger. Debuger musi czekać [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) wywołania zwrotnego od wszystkich procesów debugowany przed wydaniem tego interfejsu.  
  
 `ICorDebug` Obiekt jest obiektem początkowej do kontrolowania wszystkich dalszych zarządzanych debugowania. W .NET Framework w wersji 1.0 i 1.1, ten obiekt był `CoClass` obiektu utworzonego na podstawie modelu COM. W .NET Framework w wersji 2.0, ten obiekt nie jest już `CoClass` obiektu. Musi ona zostać utworzona przez [createdebugginginterfacefromversion —](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkcji, która jest bardziej rozpoznający wersje. Ta nowa funkcja tworzenia pozwala klientom na pobieranie określonej implementacji `ICorDebug`, które również emuluje określoną wersję interfejsu API debugowania.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
