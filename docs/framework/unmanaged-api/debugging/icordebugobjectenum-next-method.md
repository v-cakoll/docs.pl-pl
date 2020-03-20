---
title: ICorDebugObjectEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: e9b32980a5606629676549905d3c9956633f25b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178700"
---
# <a name="icordebugobjectenumnext-method"></a>ICorDebugObjectEnum::Next — Metoda
Pobiera względne adresy wirtualne (RVA) określonej liczby obiektów z wyliczenia, począwszy od bieżącej pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [w] Liczba obiektów do pobrania.  
  
 `objects`  
 [na zewnątrz] Tablica wskaźników, z których każdy wskazuje na obiekt CORDB_ADDRESS.  
  
 `pceltFetched`  
 [na zewnątrz] Wskaźnik do liczby obiektów faktycznie zwróconych. Ta wartość może `celt` być null, jeśli jest jednym.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też
