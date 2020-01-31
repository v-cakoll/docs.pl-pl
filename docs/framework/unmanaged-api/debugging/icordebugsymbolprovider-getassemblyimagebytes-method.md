---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageBytes, Metoda'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: b7a8f942d493b7b775a31dce5ab4d351a77cfe5f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791676"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a>ICorDebugSymbolProvider:: GetAssemblyImageBytes, Metoda
Odczytuje dane z scalonego zestawu, uwzględniając względny adres wirtualny (RVA) w scalonym zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `rva`  
 podczas Względny adres wirtualny (RVA) w scalonym zestawie.  
  
 `length`  
 Liczba bajtów do odczytania ze scalonego zestawu.  
  
 `ppMemoryBuffer`  
 Wskaźnik do adresu obiektu [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) , który zawiera informacje o buforze pamięci ze scalonymi metadanymi zestawu.  
  
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
