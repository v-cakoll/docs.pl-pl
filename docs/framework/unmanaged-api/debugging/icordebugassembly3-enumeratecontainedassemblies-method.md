---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 616675f839e562227558ece440bdfdf497747572
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784564"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppAssemblies`  
 określoną Wskaźnik do adresu obiektu interfejsu ICorDebugAssemblyEnum, który jest modułem wyliczającym.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `S_OK`, jeśli ten obiekt `ICorDebugAssembly3` jest kontenerem; w przeciwnym razie `S_FALSE`i Wyliczenie jest puste.  
  
## <a name="remarks"></a>Uwagi  
 Symbole są konieczne do wyliczenia zawartych zestawów. Jeśli nie są one obecne, metoda zwraca `S_FALSE`i nie podano prawidłowego modułu wyliczającego.  
  
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
