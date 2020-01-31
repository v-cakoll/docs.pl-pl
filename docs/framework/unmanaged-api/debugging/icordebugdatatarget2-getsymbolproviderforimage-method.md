---
title: Metoda ICorDebugDataTarget2::GetSymbolProviderForImage
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: bada60295c3a9b3a702aa674e06f8f5cf6ac0a24
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788829"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a>Metoda ICorDebugDataTarget2::GetSymbolProviderForImage
Zwraca dostawcę symboli dla modułu z adresu podstawowego tego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `imageBaseAddress`  
 podczas Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje adres podstawowy modułu.  
  
 `ppSymProvider`  
 określoną Wskaźnik do adresu obiektu [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) .  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget2, interfejs](icordebugdatatarget2-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
