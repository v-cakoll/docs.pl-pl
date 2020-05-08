---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 068a08d70f2443edfe0970ec1ffb8cba9953c6b9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894851"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>Metoda ICorDebugAssembly3::GetContainerAssembly
Zwraca zestaw kontenerów tego `ICorDebugAssembly3` obiektu.  
  
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
 `S_OK`Jeśli wywołanie metody powiodło się; `S_FALSE`w przeciwnym razie, `ppAssembly` i ma **wartość null**.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ten zestaw został scalony z innymi wewnątrz jednego zestawu kontenerów, Metoda ta zwraca zestaw kontenerów. Aby uzyskać więcej informacji i terminologii, zobacz temat [Metoda ICorDebugProcess6:: EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) .  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejs ICorDebugAssembly3](icordebugassembly3-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
