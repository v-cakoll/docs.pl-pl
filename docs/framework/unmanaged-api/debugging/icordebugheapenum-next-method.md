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
ms.openlocfilehash: f5af8e559b4fbfeb60530372185ca10104ade987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178851"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next — Metoda
Pobiera określoną liczbę [COR_HEAPOBJECT](cor-heapobject-structure.md) wystąpień, które zawierają informacje o obiektach na zarządzanym stosie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 Celt  
 [w] Liczba obiektów do pobrania.  
  
  — obiekty  
 [na zewnątrz] Tablica wskaźników, z których każdy wskazuje [na obiekt COR_HEAPOBJECT,](cor-heapobject-structure.md) który zawiera informacje o obiekcie na zarządzanym stosie.  
  
 pceltFetched  
 [na zewnątrz] Wskaźnik do liczby [obiektów COR_HEAPOBJECT](cor-heapobject-structure.md) faktycznie zwróconych `objects`w . Ta wartość `null` może `celt` być, jeśli jest 1.  
  
## <a name="remarks"></a>Uwagi  
 Pole `COR_HEAPOBJECT.type` jest identyfikatorem zagnieżdżonego interfejsu COM zliczanym odwołaniem. To odwołanie musi zostać zwolnione `ICorDebugHeapEnum::Next`przez wywołującego .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugHeapEnum, interfejs](icordebugheapenum-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
