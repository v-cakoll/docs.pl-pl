---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageMetadata, Metoda'
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: 3ee80c18d3091406bf0bbd5b22c5f6021888906d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791657"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a>ICorDebugSymbolProvider:: GetAssemblyImageMetadata, Metoda
Zwraca metadane z scalonego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppMemoryBuffer`  
 określoną Wskaźnik do adresu obiektu [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) , który zawiera informacje o rozmiarze i adresie metadanych scalonego zestawu.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugSymbolProvider, interfejs](icordebugsymbolprovider-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
