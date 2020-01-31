---
title: ICorDebugStaticFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: b50b9c8435f19e1a77229f01dc85514f5f75c9f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791805"
---
# <a name="icordebugstaticfieldsymbol-interface"></a>ICorDebugStaticFieldSymbol, interfejs
Przedstawia informacje o symbolu debugowania dla pola statycznego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAddress, metoda](icordebugstaticfieldsymbol-getaddress-method.md)|Pobiera adres pola statycznego.|  
|[GetName, metoda](icordebugstaticfieldsymbol-getname-method.md)|Pobiera nazwę pola statycznego.|  
|[GetSize, metoda](icordebugstaticfieldsymbol-getsize-method.md)|Pobiera rozmiar w bajtach pola statycznego.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugStaticFieldSymbol` służy do pobierania informacji o symbolach debugowania dla pola statycznego.  
  
> [!NOTE]
> Ten interfejs jest dostępny tylko dla .NET Native. W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugInstanceFieldSymbol, interfejs](icordebuginstancefieldsymbol-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
