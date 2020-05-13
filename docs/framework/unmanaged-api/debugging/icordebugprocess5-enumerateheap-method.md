---
title: ICorDebugProcess5::EnumerateHeap — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: 9386c77cc98df17d797d5886e1603ffc4824b6dc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205234"
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap — Metoda
Pobiera moduł wyliczający dla obiektów na zarządzanym stosie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppObject`  
 określoną Wskaźnik do adresu obiektu interfejsu [ICorDebugHeapEnum](icordebugheapenum-interface.md) , który jest modułem wyliczającym dla obiektów, które znajdują się na zarządzanym stosie.  
  
## <a name="remarks"></a>Uwagi  
 Przed wywołaniem `ICorDebugProcess5::EnumerateHeap` metody należy wywołać metodę [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) i sprawdzić wartość `areGCStructuresValid` pola zwróconego obiektu [COR_HEAPINFO](cor-heapinfo-structure.md) , aby upewnić się, że sterta wyrzucania elementów bezużytecznych w bieżącym stanie jest wyliczalna. Ponadto `ICorDebugProcess5::EnumerateHeap` zwraca wartość, `E_FAIL` Jeśli dołączysz zbyt wcześnie w okresie istnienia procesu, zanim zostanie przypisana pamięć zarządzanego stosu.  
  
 Obiekt interfejsu [ICorDebugHeapEnum](icordebugheapenum-interface.md) to standardowy moduł wyliczający pochodzący z interfejsu ICorDebugEnum, który umożliwia Wyliczenie [COR_HEAPOBJECT](cor-heapobject-structure.md) obiektów. Ta metoda wypełnia obiekt kolekcji [ICorDebugHeapEnum](icordebugheapenum-interface.md) z wystąpieniami [COR_HEAPOBJECT](cor-heapobject-structure.md) , które zawierają informacje o wszystkich obiektach. Kolekcja może również zawierać [COR_HEAPOBJECT](cor-heapobject-structure.md) wystąpienia, które dostarczają informacji o obiektach, które nie są odblokowane przez żaden obiekt, ale nie zostały jeszcze zebrane przez moduł wyrzucania elementów bezużytecznych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugProcess5 — Interfejs](icordebugprocess5-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
