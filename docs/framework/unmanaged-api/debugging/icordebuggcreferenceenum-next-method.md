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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ef4ced1abd5b37af204ab3511a7cf8259303e8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755547"
---
# <a name="icordebuggcreferenceenumnext-method"></a>ICorDebugGCReferenceEnum::Next — Metoda
Pobiera określoną liczbę [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) wystąpień, które zawierają informacje o obiektach, których będzie jesdnostką zbierającą śmieci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba głównych do pobrania.  
  
 elementy główne  
 [out] Tablica wskaźników, z których każdy wskazuje [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekt, który reprezentuje katalog główny obiekt można było zebranych elementów bezużytecznych.  
  
 pceltFetched  
 [out] Wskaźnik do liczby [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekty, które faktycznie są zwracane w `roots`. Ta wartość może być `null` Jeśli `celt` 1.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugGCReferenceEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
