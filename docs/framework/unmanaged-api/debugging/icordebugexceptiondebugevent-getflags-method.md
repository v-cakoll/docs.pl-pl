---
title: 'ICorDebugExceptionDebugEvent:: GetFlags — Metoda'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: aaf137b1d851d0de86bde697c9e3a512f34d2aa9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782918"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a>ICorDebugExceptionDebugEvent:: GetFlags — Metoda
Pobiera flagę wskazującą, czy wyjątek może być przechwytywany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwFlags`  
 określoną Wskaźnik do wartości [CorDebugExceptionFlags —](cordebugexceptionflags-enumeration.md) , który wskazuje, czy można przechwycić wyjątek.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugExceptionDebugEvent, interfejs](icordebugexceptiondebugevent-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
