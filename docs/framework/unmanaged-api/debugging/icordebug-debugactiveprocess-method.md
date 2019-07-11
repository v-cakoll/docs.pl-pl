---
title: ICorDebug::DebugActiveProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe94203d315c32b62a191adf294a9c1310fe28e0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738261"
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess — Metoda
Dołącza debuger do istniejącego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator procesu, do którego ma zostać dołączony debuger.  
  
 `win32Attach`  
 [in] Wartość logiczna, która jest równa `true` Jeśli debuger powinien zachowywać się jak debugera Win32 dla procesu i wysyłania niezarządzanych wywołań zwrotnych; w przeciwnym razie `false`.  
  
 `ppProcess`  
 [out] Wskaźnik na adres obiektu "ICorDebugProcess", który reprezentuje proces, do którego został dołączony debuger.  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie międzyoperacyjne nie jest obsługiwane na platformach Win9x i innych x86, takich jak IA-64 i komputerów z procesorem AMD64 platform.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
