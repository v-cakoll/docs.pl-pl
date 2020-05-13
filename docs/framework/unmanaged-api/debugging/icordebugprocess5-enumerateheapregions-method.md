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
ms.openlocfilehash: 50b0859d6727a25906f2c8b0f3fe96da228ab886
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213559"
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
 Przed wywołaniem `ICorDebugProcess5::EnumerateHeapRegions` metody należy wywołać metodę [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) i sprawdzić wartość `areGCStructuresValid` pola zwróconego obiektu [COR_HEAPINFO](cor-heapinfo-structure.md) , aby upewnić się, że sterta wyrzucania elementów bezużytecznych w bieżącym stanie jest wyliczalna. Ponadto `ICorDebugProcess5::EnumerateHeapRegions` Metoda zwraca, `E_FAIL` Jeśli dołączysz zbyt wcześnie w okresie istnienia procesu, przed utworzeniem regionów pamięci.  
  
 Ta metoda gwarantuje Wyliczenie wszystkich regionów pamięci, które mogą zawierać obiekty zarządzane, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w tych regionach. Obiekt kolekcji [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) może zawierać puste lub zarezerwowane regiony pamięci.  
  
 Obiekt interfejsu [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) to standardowy moduł wyliczający pochodzący z interfejsu ICorDebugEnum, który umożliwia Wyliczenie [COR_SEGMENT](cor-segment-structure.md) obiektów. Każdy obiekt [COR_SEGMENT](cor-segment-structure.md) zawiera informacje o zakresie pamięci określonego segmentu oraz o generowaniu obiektów w tym segmencie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugProcess5 — Interfejs](icordebugprocess5-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
