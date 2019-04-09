---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes Method
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103e724c37ae356729dd5bba3ff66c0f443f6eaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170238"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a>ICorDebugSymbolProvider::GetAssemblyImageBytes Method
Odczytuje dane z zestawu scalonych podane względnych adresów wirtualnych (RVA) w zestawie scalone.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `rva`  
 [in] Względny adres wirtualny (RVA) w zestawie scalone.  
  
 `length`  
 Liczba bajtów do odczytania z zestawu scalonych.  
  
 `ppMemoryBuffer`  
 Wskaźnik na adres [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obiektu, który zawiera informacje o wartość bufora pamięci z metadanych zestawu scalonych.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugSymbolProvider, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
