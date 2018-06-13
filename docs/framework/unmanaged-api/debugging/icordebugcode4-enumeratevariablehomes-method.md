---
title: ICorDebugCode4::EnumerateVariableHomes — metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e1c8157d5a5e4a1bd52f187de7c1d3bfcc4e66d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410923"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a>ICorDebugCode4::EnumerateVariableHomes — metoda
Pobiera moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 Wskaźnik do adresu [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) obiektu interfejsu, który moduł wyliczający dla zmiennych lokalnych i argumenty w funkcji.  
  
## <a name="remarks"></a>Uwagi  
 [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) obiekt interfejsu jest standardowy moduł pochodzące z interfejsu "ICorDebugEnum", która umożliwia wyliczyć [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektów. Kolekcja może zawierać wielu [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektów dla tego samego miejsca lub argumentu indeksu, jeśli mają inną domach w różnych punktach w funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugCode4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
