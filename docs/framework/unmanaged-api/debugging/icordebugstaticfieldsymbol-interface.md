---
title: ICorDebugStaticFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: f9b82f0f98a668555a8096d7575c049c31cae93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379442"
---
# <a name="icordebugstaticfieldsymbol-interface"></a>ICorDebugStaticFieldSymbol, interfejs
Przedstawia informacje o symbolu debugowania dla pola statycznego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAddress — Metoda](icordebugstaticfieldsymbol-getaddress-method.md)|Pobiera adres pola statycznego.|  
|[GetName — Metoda](icordebugstaticfieldsymbol-getname-method.md)|Pobiera nazwę pola statycznego.|  
|[GetSize — Metoda](icordebugstaticfieldsymbol-getsize-method.md)|Pobiera rozmiar w bajtach pola statycznego.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugStaticFieldSymbol`Interfejs jest używany do pobierania informacji o symbolach debugowania dla pola statycznego.  
  
> [!NOTE]
> Ten interfejs jest dostępny tylko dla .NET Native. W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugInstanceFieldSymbol, interfejs](icordebuginstancefieldsymbol-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
