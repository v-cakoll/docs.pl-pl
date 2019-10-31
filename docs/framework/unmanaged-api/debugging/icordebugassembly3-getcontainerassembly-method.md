---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 39f8dd042ea785258dfe5c048ebc348852be6892
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095392"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>Metoda ICorDebugAssembly3::GetContainerAssembly
Zwraca zestaw kontenerów tego obiektu `ICorDebugAssembly3`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppAssembly`  
 Wskaźnik do adresu obiektu ICorDebugAssembly, który reprezentuje zestaw kontenerów, lub **wartość null** , jeśli wywołanie metody nie powiedzie się.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`, jeśli wywołanie metody powiodło się; w przeciwnym razie `S_FALSE`i `ppAssembly` ma **wartość null**.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ten zestaw został scalony z innymi wewnątrz jednego zestawu kontenerów, Metoda ta zwraca zestaw kontenerów. Aby uzyskać więcej informacji i terminologii, zobacz temat [Metoda ICorDebugProcess6:: EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) .  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugAssembly3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
