---
title: Metoda ICorDebugDataTarget2::GetSymbolProviderForImage
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 7800630be0ed9afb321d607046be308088781388
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976450"
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
 podczas Wartość [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , która reprezentuje adres podstawowy modułu.  
  
 `ppSymProvider`  
 określoną Wskaźnik do adresu obiektu [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) .  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejs ICorDebugDataTarget2](icordebugdatatarget2-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
