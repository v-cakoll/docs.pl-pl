---
title: ICorDebugLoadedModule::GetBaseAddress — metoda
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 190c9114cffa537ba162b19abdf30d5a6aee87f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788443"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a>ICorDebugLoadedModule::GetBaseAddress — metoda
Pobiera adres podstawowy załadowanego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAddress`  
 określoną Wskaźnik na adres podstawowy załadowanego modułu.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugLoadedModule, interfejs](icordebugloadedmodule-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
