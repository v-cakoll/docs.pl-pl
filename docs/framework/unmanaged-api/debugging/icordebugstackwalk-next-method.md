---
title: ICorDebugStackWalk::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eee75bc16f46ba5ea58fc42c570e48b09ab9a2e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553233"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next — Metoda
Przenosi [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu do następnej ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Środowisko uruchomieniowe pomyślnie odwinięty do następnej ramki (zobacz Uwagi).|  
|E_FAIL|`ICorDebugStackWalk` Nie może kontynuować obiektu.|  
|CORDBG_S_AT_END_OF_STACK|Koniec stosu został osiągnięty w wyniku tego unwind.|  
|CORDBG_E_PAST_END_OF_STACK|Wskaźnik ramki jest już na końcu stosu; w związku z tym są dostępne nie dodatkowe ramki.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 `Next` Postępu metoda `ICorDebugStackWalk` obiekt wywołujący ramki, tylko wtedy, gdy środowisko uruchomieniowe może unwind bieżącej ramki. W przeciwnym razie obiekt przechodzi do następnej ramki środowiska uruchomieniowego jest w stanie unwind.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugStackWalk, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
