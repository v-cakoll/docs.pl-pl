---
title: ICorDebugGCReferenceEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: d87f414e9dfd05a519b60efc7ecdd5328a6dd86f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178863"
---
# <a name="icordebuggcreferenceenumnext-method"></a>ICorDebugGCReferenceEnum::Next — Metoda
Pobiera określoną liczbę [COR_GC_REFERENCE](cor-gc-reference-structure.md) wystąpień, które zawierają informacje o obiektach, które będą zbierane śmieci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 Celt  
 [w] Liczba katalogów głównych do pobrania.  
  
 Korzenie  
 [na zewnątrz] Tablica wskaźników, z których każdy wskazuje [na obiekt COR_GC_REFERENCE,](cor-gc-reference-structure.md) który reprezentuje katalog główny obiektu, który ma być zbierane od śmieci.  
  
 pceltFetched  
 [na zewnątrz] Wskaźnik do liczby [obiektów COR_GC_REFERENCE](cor-gc-reference-structure.md) faktycznie zwróconych w `roots`. Ta wartość `null` może `celt` być, jeśli jest 1.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugGCReferenceEnum, interfejs](icordebuggcreferenceenum-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
