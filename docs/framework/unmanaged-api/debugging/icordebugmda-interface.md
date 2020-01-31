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
ms.openlocfilehash: a147aee1ebba57b86dbbf8a7648456b8d7494936
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793194"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA — Interfejs
Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDescription, metoda](icordebugmda-getdescription-method.md)|Pobiera ciąg zawierający opis tego elementu MDA.|  
|[GetFlags, metoda](icordebugmda-getflags-method.md)|Pobiera flagi skojarzone z tym zdarzeniem MDA.|  
|[GetName, metoda](icordebugmda-getname-method.md)|Pobiera ciąg zawierający nazwę tego elementu MDA.|  
|[GetOSThreadId, metoda](icordebugmda-getosthreadid-method.md)|Pobiera identyfikator wątku systemu operacyjnego, na którym jest wykonywane zdarzenie MDA.|  
|[GetXML, metoda](icordebugmda-getxml-method.md)|Pobiera pełny strumień XML skojarzony z tym MDA.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
