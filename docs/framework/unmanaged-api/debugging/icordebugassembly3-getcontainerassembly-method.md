---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 969cca6d5613670fc4b26fc973785b4874c3684c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778071"
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
  
## <a name="return-value"></a>Wartość zwrócona  
 `S_OK`, jeśli wywołanie metody powiodło się; w przeciwnym razie `S_FALSE`i `ppAssembly` ma **wartość null**.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ten zestaw został scalony z innymi wewnątrz jednego zestawu kontenerów, Metoda ta zwraca zestaw kontenerów. Aby uzyskać więcej informacji i terminologii, zobacz temat [Metoda ICorDebugProcess6:: EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) .  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugAssembly3, interfejs](icordebugassembly3-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
