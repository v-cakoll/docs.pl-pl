---
title: ICorDebugAppDomain4::GetObjectForCCW — metoda
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 10d32314e46aba4f030b294cadc3cbb36e8742f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179047"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>ICorDebugAppDomain4::GetObjectForCCW — metoda
Pobiera obiekt zarządzany ze wskaźnika otoki wywoływanej com (CCW).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ccwPointer`  
 [w] Wskaźnik otoki wywoływanej com (CCW).  
  
 `ppManagedObject`  
 [na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje obiekt zarządzany, który odpowiada podanemu wskaźnikowi CCW.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugAppDomain4, interfejs](icordebugappdomain4-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
