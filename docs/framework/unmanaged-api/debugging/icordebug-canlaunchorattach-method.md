---
title: "ICorDebug::CanLaunchOrAttach — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62ebdb178ef7aaa16bcc163e42662e1d69f1f6f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach — Metoda
Zwraca wartość wskazującą, czy jest możliwe w kontekście bieżącej konfiguracji komputera i środowiska uruchomieniowego uruchamianie nowego procesu lub dołączanie do określonego istniejącego procesu HRESULT.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwProcessId`  
 [in] Identyfikator istniejącego procesu.  
  
 `win32DebuggingEnabled`  
 [in] Przekazywanie `true` Jeśli jest planowane uruchamianie z włączonym debugowaniem Win32 lub dołączyć z debugowaniem Win32 włączone; w przeciwnym razie przekazania `false`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK Jeśli usług debugowania określić uruchamianie nowego procesu lub dołączanie do procesu danego jest to możliwe, podane informacje o bieżącej konfiguracji komputera i środowiska uruchomieniowego. Możliwe wartości HRESULT to:  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wyłącznie informacyjne. Interfejs nie zakończy uruchomienie lub dołączanie do procesu, niezależnie od wartości zwróconych przez `CanLaunchOrAttach`.  
  
 Jeśli planujesz uruchamianie z włączonym debugowaniem Win32 lub Dołącz z włączonym debugowaniem Win32, Przekaż `true` dla `win32DebuggingEnabled`. HRESULT zwrócony przez `CanLaunchOrAttach` mogą różnić się w przypadku użycia tej opcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
