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
ms.openlocfilehash: a662185bb84e9a66573b43b26ffcd256ecb943f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909851"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA — Interfejs
Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDescription, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Pobiera ciąg zawierający opis tego elementu MDA.|  
|[GetFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|Pobiera flagi skojarzone z tym zdarzeniem MDA.|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Pobiera ciąg zawierający nazwę tego elementu MDA.|  
|[GetOSThreadId, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Pobiera identyfikator wątku systemu operacyjnego, na którym jest wykonywane zdarzenie MDA.|  
|[GetXML, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|Pobiera pełny strumień XML skojarzony z tym MDA.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
