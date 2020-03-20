---
title: ICorDebugStaticFieldSymbol::Metoda GetName
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: b1f5ca266f51df730dfb840c7bf003c47f31ece9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178516"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a>ICorDebugStaticFieldSymbol::Metoda GetName
Pobiera nazwę pola statycznego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 [w] Liczba znaków w `szName` buforze.  
  
 `pcchName`  
 [na zewnątrz] Wskaźnik do liczby znaków faktycznie zapisane `szName` w buforze.  
  
 `szName`  
 [na zewnątrz] Tablica znaków, która przechowuje zwróconą nazwę.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko w przypadku platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugStaticFieldSymbol, interfejs](icordebugstaticfieldsymbol-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
