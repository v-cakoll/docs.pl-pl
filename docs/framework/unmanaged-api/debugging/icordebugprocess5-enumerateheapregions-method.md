---
title: ICorDebugProcess5::EnumerateHeapRegions — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
ms.openlocfilehash: 8070b0693b5718ad8b4cbeb9bf5792cb7f4a0a85
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792404"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions — Metoda
Pobiera moduł wyliczający dla zakresów pamięci zarządzanej sterty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppRegions`  
 określoną Wskaźnik do adresu obiektu interfejsu [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) , który jest modułem wyliczającym dla zakresów pamięci, w których obiekty znajdują się w zarządzanym stosie.  
  
## <a name="remarks"></a>Uwagi  
 Przed wywołaniem metody `ICorDebugProcess5::EnumerateHeapRegions` należy wywołać metodę [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) i sprawdzić wartość pola `areGCStructuresValid` zwróconego obiektu [COR_HEAPINFO](cor-heapinfo-structure.md) , aby upewnić się, że sterta wyrzucania elementów bezużytecznych w bieżącym stanie jest wyliczalna. Ponadto Metoda `ICorDebugProcess5::EnumerateHeapRegions` zwraca `E_FAIL`, jeśli dołączysz zbyt wcześnie w okresie istnienia procesu, przed utworzeniem regionów pamięci.  
  
 Ta metoda gwarantuje Wyliczenie wszystkich regionów pamięci, które mogą zawierać obiekty zarządzane, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w tych regionach. Obiekt kolekcji [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) może zawierać puste lub zarezerwowane regiony pamięci.  
  
 Obiekt interfejsu [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) to standardowy moduł wyliczający pochodzący z interfejsu ICorDebugEnum, który umożliwia Wyliczenie [COR_SEGMENT](cor-segment-structure.md) obiektów. Każdy obiekt [COR_SEGMENT](cor-segment-structure.md) zawiera informacje o zakresie pamięci określonego segmentu oraz o generowaniu obiektów w tym segmencie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess5, interfejs](icordebugprocess5-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
