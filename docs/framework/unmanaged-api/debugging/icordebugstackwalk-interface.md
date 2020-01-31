---
title: ICorDebugStackWalk — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: a6283d699263dc9b79e457010f31923f77443129
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791880"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk — Interfejs
Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetContext, metoda](icordebugstackwalk-getcontext-method.md)|Zwraca kontekst dla bieżącej ramki w obiekcie `ICorDebugStackWalk`.|  
|[SetContext, metoda](icordebugstackwalk-setcontext-method.md)|Ustawia bieżący kontekst obiektu `ICorDebugStackWalk` na prawidłowy kontekst dla wątku.|  
|[Next, metoda](icordebugstackwalk-next-method.md)|Przenosi `ICorDebugStackWalk` obiektu do następnej ramki.|  
|[GetFrame, metoda](icordebugstackwalk-getframe-method.md)|Pobiera bieżącą ramkę w obiekcie `ICorDebugStackWalk`.|  
  
## <a name="remarks"></a>Uwagi  
  
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
