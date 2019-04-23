---
title: ICorDebugProcess2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b3bb51f307093ea1cc8cc45064d5c405974822
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178025"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2, interfejs
Logiczne rozszerzenie icordebugprocess — interfejs, który reprezentuje proces uruchamiania kodu zarządzanego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|Usuwa punkt przerwania od określonego przesunięcia, która została ustawiona przez podczas wcześniejszego wywołania `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[GetDesiredNGENCompilerFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|Pobiera flagi, które musi być ustawiona dla środowisko uruchomieniowe języka wspólnego (CLR) w celu załadowania obrazu w procesie przywoływane przez to `ICorDebugProcess2`.|  
|[GetReferenceValueFromGCHandle, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|Pobiera wskaźnik odwołania do określonego obiektu zarządzanego, który ma obsługiwać wyrzucania elementów bezużytecznych.|  
|[GetThreadForTaskID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|Pobiera wątku, na którym jest wykonywane zadanie o podanym identyfikatorze.|  
|[GetVersion, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|Pobiera wersję środowiska CLR, w którym jest uruchomiony debugowanego procesu.|  
|[SetDesiredNGENCompilerFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|Ustawia flagi, które są wymagane przez kompilator just-in-time (JIT) do załadowania obrazu do debugowanego procesu.|  
|[SetUnmanagedBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|Ustawia niezarządzany punkt przerwania w przesunięciu określonego obrazu natywnego.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
