---
title: ICorDebugValueEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: db1721fed6414310556ceac493275e069a781ac8
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397141"
---
# <a name="icordebugvalueenumnext-method"></a>ICorDebugValueEnum::Next — Metoda
Pobiera określoną liczbę wystąpień "ICorDebugValue" z wyliczenia, rozpoczynając od bieżącego położenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba `ICorDebugValue` wystąpień do pobrania.  
  
 `values`  
 określoną Tablica wskaźników, z których każdy wskazuje `ICorDebugValue` obiekt.  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby `ICorDebugValue` faktycznie zwróconych wystąpień. Ta wartość może być równa null, jeśli `celt` jest taka.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
