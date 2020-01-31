---
title: ICorDebugDataTarget3::GetLoadedModules — metoda
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: d4c22146422085daa4dc9d90ae5b3735a12500c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793557"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>ICorDebugDataTarget3::GetLoadedModules — metoda
Pobiera listę modułów, które zostały wcześniej załadowane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cRequestedModules`  
 podczas Liczba modułów, dla których żądane są informacje.  
  
 `pcFetchedModules`  
 określoną Wskaźnik do liczby modułów, na których zwrócono informacje.  
  
 `pLoadedModules`  
 określoną Wskaźnik do tablicy obiektów [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) , które zawierają informacje o załadowanych modułach.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget3, interfejs](icordebugdatatarget3-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
