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
ms.openlocfilehash: 66b50bad0e8d2622922da96c213643ac3be83a9e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895374"
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
|[GetProcess — Metoda](icordebug-getprocess-method.md)|Zwraca obiekt "ICorDebugProcess" z danym IDENTYFIKATORem procesu.|  
|[Initialize — Metoda](icordebug-initialize-method.md)|Inicjuje `ICorDebug` obiekt.|  
|[SetManagedHandler, metoda](icordebug-setmanagedhandler-method.md)|Określa obiekt obsługi zdarzeń dla zdarzeń zarządzanych.|  
|[SetUnmanagedHandler, metoda](icordebug-setunmanagedhandler-method.md)|Określa obiekt obsługi zdarzeń dla zdarzeń niezarządzanych.|  
|[Terminate — Metoda](icordebug-terminate-method.md)|Kończy `ICorDebug` obiekt.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebug`reprezentuje pętlę przetwarzania zdarzeń dla procesu debugera. Debuger musi oczekiwać na wywołanie zwrotne [ICorDebugManagedCallback:: ExitProcess —](icordebugmanagedcallback-exitprocess-method.md) ze wszystkich procesów, które są debugowane przed zwolnieniem tego interfejsu.  
  
 `ICorDebug` Obiekt jest początkowym obiektem, który kontroluje wszystkie inne zarządzane debugowanie. W .NET Framework wersje 1,0 i 1,1 ten obiekt był `CoClass` obiektem utworzonym na podstawie modelu com. W .NET Framework w wersji 2,0 ten obiekt nie jest już `CoClass` obiektem. Musi być utworzony przez funkcję [CreateDebuggingInterfaceFromVersion —](../hosting/createdebugginginterfacefromversion-function.md) , która jest większa od wersji. Ta nowa funkcja tworzenia umożliwia klientom uzyskanie określonej implementacji programu `ICorDebug`, która również emuluje określoną wersję interfejsu API debugowania.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
