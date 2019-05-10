---
title: ICorDebug::CanLaunchOrAttach — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c109bab2ecd14e2b698a9b24dace56e986ad5e58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593519"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach — Metoda
Zwraca wartość HRESULT, która wskazuje, czy uruchamianie nowego procesu lub dołączanie do określonego istniejącego procesu jest możliwe w kontekście bieżącej konfiguracji komputera i środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwProcessId`  
 [in] Identyfikator istniejącego procesu.  
  
 `win32DebuggingEnabled`  
 [in] Przekaż `true` Jeśli planujesz uruchomić z włączonym debugowaniem Win32 lub dołączyć Win32 debugowania włączone; w przeciwnym razie należy przekazać `false`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli debugowanie usługi określić uruchamianie nowego procesu lub dołączanie do danego procesu jest możliwe, podane informacje o bieżącej konfiguracji komputera i środowiska uruchomieniowego. Możliwe wartości HRESULT to:  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wyłącznie informacyjne. Interfejs nie spowoduje zatrzymania można uruchomić lub dołączanie do procesu, niezależnie od wartości zwracane przez `CanLaunchOrAttach`.  
  
 Jeśli planujesz uruchomić z włączonym debugowaniem Win32 lub dołączyć z włączonym debugowaniem Win32, przekazać `true` dla `win32DebuggingEnabled`. HRESULT zwracane przez `CanLaunchOrAttach` mogą się różnić w przypadku użycia tej opcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
