---
title: ICorDebugHeapEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 2c84112984e9cb7dec2a492ac16af00e14770806
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782492"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next — Metoda
Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](cor-heapobject-structure.md) , które zawierają informacje o obiektach na zarządzanym stosie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 celt  
 podczas Liczba obiektów do pobrania.  
  
 — obiekty  
 określoną Tablica wskaźników, z których każdy wskazuje obiekt [COR_HEAPOBJECT](cor-heapobject-structure.md) , który zawiera informacje na temat obiektu na zarządzanym stosie.  
  
 pceltFetched  
 określoną Wskaźnik do liczby obiektów [COR_HEAPOBJECT](cor-heapobject-structure.md) faktycznie zwróconych w `objects`. Ta wartość może być `null`, jeśli `celt` wynosi 1.  
  
## <a name="remarks"></a>Uwagi  
 Pole `COR_HEAPOBJECT.type` jest identyfikatorem zagnieżdżonego, odwołującego się interfejsu COM. To odwołanie musi zostać wydane przez obiekt wywołujący `ICorDebugHeapEnum::Next`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugHeapEnum, interfejs](icordebugheapenum-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
