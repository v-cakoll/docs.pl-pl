---
title: 'ICorDebugInstanceFieldSymbol:: GetName — Metoda'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: 05914863dfbc2aca608a5d74f298f81c64345fe8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782388"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a>ICorDebugInstanceFieldSymbol:: GetName — Metoda
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
 podczas Liczba znaków w buforze `szName`.  
  
 `pcchName`  
 określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w buforze `szName`.  
  
 `szName`  
 określoną Tablica znaków przechowująca zwróconą nazwę.  
  
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
