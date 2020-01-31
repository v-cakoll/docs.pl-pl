---
title: ICorDebugThread4 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 0bb25d060853abb20316a344bae3755b2f8b4dc7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791338"
---
# <a name="icordebugthread4-interface"></a>ICorDebugThread4 — Interfejs
Dostarcza informacje o blokowaniu wątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBlockingObjects, metoda](icordebugthread4-getblockingobjects-method.md)|Udostępnia uporządkowane Wyliczenie struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) , które dostarczają informacje o blokowaniu wątku.|  
|[HadUnhandledException, metoda](icordebugthread4-hadunhandledexception-method.md)|Wskazuje, czy wątek kiedykolwiek miał nieobsługiwany wyjątek.|  
|[GetCurrentCustomDebuggerNotification, metoda](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|Pobiera bieżący obiekt [ICorDebugManagedCallback3:: CustomNotification —](icordebugmanagedcallback3-customnotification-method.md) w bieżącym wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest logicznym rozszerzeniem interfejsów ICorDebugThread, ICorDebugThread2 i [ICorDebugThread3](icordebugthread3-interface.md) .  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
