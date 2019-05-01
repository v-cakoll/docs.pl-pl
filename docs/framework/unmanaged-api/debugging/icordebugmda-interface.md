---
title: ICorDebugMDA — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cea8f6827d3e361b3f6498e6612d8b11a2357285
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916672"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA — Interfejs
Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDescription, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Pobiera ciąg zawierający opis to zdarzenie MDA.|  
|[GetFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|Pobiera flagi skojarzone z tego MDA.|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Pobiera ciąg zawierający nazwę to zdarzenie MDA.|  
|[GetOSThreadId, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Pobiera identyfikator wątku systemu operacyjnego, na którym jest wykonywane to zdarzenie MDA.|  
|[GetXML, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|Pobiera pełną strumień XML skojarzony z tego MDA.|  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
