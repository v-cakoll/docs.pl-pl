---
title: ICorDebugEval2, interfejs
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
ms.openlocfilehash: e69b32430651edd0222db874e2659bd959f89549
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788706"
---
# <a name="icordebugeval2-interface"></a>ICorDebugEval2, interfejs

Rozszerza "ICorDebugEval", aby zapewnić obsługę typów ogólnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CallParameterizedFunction, metoda](icordebugeval2-callparameterizedfunction-method.md)|Konfiguruje wywołanie do określonego elementu "ICorDebugFunction", który może być zagnieżdżony wewnątrz typu, którego Konstruktor pobiera parametry typu, lub sam może przyjmować parametry typu.|  
|[CreateValueForType, metoda](icordebugeval2-createvaluefortype-method.md)|Pobiera wskaźnik do nowego elementu "ICorDebugValue" określonego typu z początkową wartością null lub zero.|  
|[NewParameterizedArray, metoda](icordebugeval2-newparameterizedarray-method.md)|Przypisuje nową tablicę określonego typu elementu i wymiarów.|  
|[NewParameterizedObject, metoda](icordebugeval2-newparameterizedobject-method.md)|Tworzy wystąpienie nowego obiektu typu sparametryzowanego i wywołuje metodę konstruktora obiektu.|  
|[NewParameterizedObjectNoConstructor, metoda](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Tworzy wystąpienie nowego obiektu typu sparametryzowanego określonej klasy bez próby wywołania metody konstruktora|  
|[NewStringWithLength, metoda](icordebugeval2-newstringwithlength-method.md)|Tworzy nowy ciąg o określonej długości z określoną zawartością.|  
|[RudeAbort, metoda](icordebugeval2-rudeabort-method.md)|Przerywa Obliczanie wykonywane przez tę `ICorDebugEval2`.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
