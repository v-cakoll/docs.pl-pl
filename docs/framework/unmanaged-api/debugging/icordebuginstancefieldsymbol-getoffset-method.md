---
title: 'ICorDebugInstanceFieldSymbol:: GetOffset — Metoda'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: f7c13d397b39698bdf1a22f14820680e1fd0a25f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782293"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a>ICorDebugInstanceFieldSymbol:: GetOffset — Metoda
Pobiera przesunięcie w bajtach tego pola wystąpienia w jego klasie nadrzędnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pcbOffset`  
 Wskaźnik do liczby bajtów, które to pole wystąpienia jest przesunięte w swojej klasie nadrzędnej.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugInstanceFieldSymbol, interfejs](icordebuginstancefieldsymbol-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
