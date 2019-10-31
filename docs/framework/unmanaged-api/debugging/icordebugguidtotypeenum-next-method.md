---
title: ICorDebugGuidToTypeEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: f6f190cd5b2f208df5a4ed88b650af671f2e6c5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138520"
---
# <a name="icordebugguidtotypeenumnext-method"></a>ICorDebugGuidToTypeEnum::Next — Metoda
Pobiera określoną liczbę wystąpień [CorDebugGuidToTypeMapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , które MAPUJĄ identyfikatory GUID na informacje o typie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba obiektów mapowania GUID-to-Type do pobrania.  
  
 `values`  
 określoną Tablica wskaźników, z których każdy wskazuje obiekt [CorDebugGuidToTypeMapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , który MAPUJE identyfikator GUID środowisko wykonawcze systemu Windows do odpowiadającego mu obiektu ICorDebugType.  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby obiektów [CorDebugGuidToTypeMapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) faktycznie zwróconych w `values`.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** środowisko wykonawcze systemu Windows  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugGuidToTypeEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
