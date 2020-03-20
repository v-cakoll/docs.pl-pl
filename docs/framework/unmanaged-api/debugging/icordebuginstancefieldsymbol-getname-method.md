---
title: ICorDebugInstanceFieldSymbol::Metoda GetName
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: dd925cc213ed8a6c5d1def85b3e6335751c1b594
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178762"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a>ICorDebugInstanceFieldSymbol::Metoda GetName
Pobiera nazwę pola wystąpienia.  
  
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

- [ICorDebugInstanceFieldSymbol, interfejs](icordebuginstancefieldsymbol-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
