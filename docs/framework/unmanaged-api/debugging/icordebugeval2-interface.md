---
title: ICorDebugEval2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4315c9f5296e8c3ffc9d8241b929c71c2448db6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965868"
---
# <a name="icordebugeval2-interface"></a>ICorDebugEval2 — Interfejs

Rozszerza "ICorDebugEval" w celu zapewnienia obsługi typów ogólnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CallParameterizedFunction, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|Konfiguruje wywołanie do określonego "ICorDebugFunction", które mogą być zagnieżdżone wewnątrz typu, w której Konstruktor przyjmuje parametry typu lub może zająć się parametry typu.|  
|[CreateValueForType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|Pobiera wskaźnik do nowego "ICorDebugValue" określonego typu o wartości początkowej wartości null lub wartość zero.|  
|[NewParameterizedArray, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|Przydziela nową tablicę typu określonego elementu i wymiary.|  
|[NewParameterizedObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|Tworzy nowy obiekt typ sparametryzowany i wywołuje metodę do konstruktora obiektu.|  
|[NewParameterizedObjectNoConstructor, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Tworzy nowy typ sparametryzowany obiekt określonej klasy bez próby wywołania metody konstruktora|  
|[NewStringWithLength, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|Tworzy nowy ciąg o określonej długości, przy użyciu określonej zawartości.|  
|[RudeAbort, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|Przerywa obliczeń że `ICorDebugEval2` Trwa wykonywanie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
