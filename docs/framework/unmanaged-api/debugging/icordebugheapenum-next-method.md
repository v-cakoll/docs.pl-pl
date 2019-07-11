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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aef821c10b8b44e54967245aaab3956c16ea15b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757385"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next — Metoda
Pobiera określoną liczbę [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obiektów na stosie zarządzanym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba obiektów, które mają zostać pobrane.  
  
 — obiekty  
 [out] Tablica wskaźników, z których każdy wskazuje [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektu, który zawiera informacje dotyczące obiektu na stosie zarządzanym.  
  
 pceltFetched  
 [out] Wskaźnik do liczby [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiekty, które faktycznie są zwracane w `objects`. Ta wartość może być `null` Jeśli `celt` 1.  
  
## <a name="remarks"></a>Uwagi  
 `COR_HEAPOBJECT.type` Pola jest identyfikatorem zagnieżdżonego interfejsu COM zliczonych odwołań. Ta dokumentacja muszą zostać zwolnione przez obiekt wywołujący `ICorDebugHeapEnum::Next`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugHeapEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
