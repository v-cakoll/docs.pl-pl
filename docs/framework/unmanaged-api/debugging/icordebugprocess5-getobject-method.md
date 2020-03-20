---
title: ICorDebugProcess5::GetObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: 4b48132ee60bcaebb218d8f583de6558372f5055
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178607"
---
# <a name="icordebugprocess5getobject-method"></a>ICorDebugProcess5::GetObject — Metoda
Konwertuje adres obiektu na obiekt "ICorDebugObjectValue".  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `addr`  
 [w] Adres obiektu.  
  
 `ppObject`  
 [na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugObjectValue".  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `addr` nie wskazuje prawidłowego obiektu `GetObject` zarządzanego, metoda zwraca `E_FAIL`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugProcess5, interfejs](icordebugprocess5-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
