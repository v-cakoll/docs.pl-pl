---
title: Metoda ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58649a0fc12ce63a1307af5d831dbf5e0d5a776a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136984"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a>Metoda ICorDebugMemoryBuffer::GetStartAddress
Pobiera adres początkowy bufora pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 [out] Wskaźnik do adres początkowy bufora pamięci.  
  
## <a name="remarks"></a>Uwagi  
  
> [!WARNING]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMemoryBuffer, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
