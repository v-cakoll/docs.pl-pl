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
ms.openlocfilehash: 01e52385f1a94ffb9682bdbe92e5c95e9870611e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416806"
---
# <a name="icordebuggcreferenceenumnext-method"></a>ICorDebugGCReferenceEnum::Next — Metoda
Pobiera określoną liczbę [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) wystąpień, które zawierają informacje o obiektach, które mają być zbierane z pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba głównych, które mają zostać pobrane.  
  
 elementy główne  
 [out] Tablicy wskaźników, z których każdy wskazuje [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekt, który reprezentuje katalog główny obiekt, aby być zbierane z pamięci.  
  
 pceltFetched  
 [out] Wskaźnik do liczby [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekty zwrócone faktycznie w `roots`. Ta wartość może być `null` Jeśli `celt` 1.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugGCReferenceEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
