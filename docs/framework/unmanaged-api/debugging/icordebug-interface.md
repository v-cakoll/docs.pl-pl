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
ms.openlocfilehash: 0ca66f001d04bc86b64e0fe2d1cd37559e4fc633
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785115"
---
# <a name="icordebug-interface"></a>ICorDebug — Interfejs
Zapewnia metody, które umożliwiają deweloperom debugowanie aplikacji w środowisku uruchomieniowym języka wspólnego (CLR).  
  
> [!NOTE]
> Debugowanie w trybie mieszanym (kod zarządzany i natywny) nie jest obsługiwane w systemach Windows 95, Windows 98 lub Windows ME ani na platformach innych niż x86 (takich jak IA64 i AMD64).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanLaunchOrAttach, metoda](icordebug-canlaunchorattach-method.md)|Określa, czy ma być uruchamiany nowy proces, czy dołączany do danego procesu jest możliwy w kontekście bieżącego komputera i konfiguracji środowiska uruchomieniowego.|  
|[CreateProcess, metoda](icordebug-createprocess-method.md)|Uruchamia proces i jego główny wątek pod kontrolą debugera.|  
|[DebugActiveProcess, metoda](icordebug-debugactiveprocess-method.md)|Dołącza debuger do istniejącego procesu.|  
|[EnumerateProcesses, metoda](icordebug-enumerateprocesses-method.md)|Pobiera moduł wyliczający dla procesów, które są debugowane.|  
|[GetProcess, metoda](icordebug-getprocess-method.md)|Zwraca obiekt "ICorDebugProcess" z danym IDENTYFIKATORem procesu.|  
|[Initialize, metoda](icordebug-initialize-method.md)|Inicjuje obiekt `ICorDebug`.|  
|[SetManagedHandler, metoda](icordebug-setmanagedhandler-method.md)|Określa obiekt obsługi zdarzeń dla zdarzeń zarządzanych.|  
|[SetUnmanagedHandler, metoda](icordebug-setunmanagedhandler-method.md)|Określa obiekt obsługi zdarzeń dla zdarzeń niezarządzanych.|  
|[Terminate, metoda](icordebug-terminate-method.md)|Kończy działanie obiektu `ICorDebug`.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebug` reprezentuje pętlę przetwarzania zdarzeń dla procesu debugera. Debuger musi oczekiwać na wywołanie zwrotne [ICorDebugManagedCallback:: ExitProcess —](icordebugmanagedcallback-exitprocess-method.md) ze wszystkich procesów, które są debugowane przed zwolnieniem tego interfejsu.  
  
 Obiekt `ICorDebug` jest początkowym obiektem, który kontroluje wszystkie inne zarządzane debugowanie. W .NET Framework wersje 1,0 i 1,1 ten obiekt był obiektem `CoClass` utworzonym na podstawie modelu COM. W .NET Framework w wersji 2,0 ten obiekt nie jest już obiektem `CoClass`. Musi być utworzony przez funkcję [CreateDebuggingInterfaceFromVersion —](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) , która jest większa od wersji. Ta nowa funkcja tworzenia umożliwia klientom uzyskanie konkretnej implementacji `ICorDebug`, która również emuluje określoną wersję interfejsu API debugowania.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
