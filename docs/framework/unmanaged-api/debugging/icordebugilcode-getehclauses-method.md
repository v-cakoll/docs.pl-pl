---
title: Metoda ICorDebugILCode::GetEHClauses
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e890629f307e3d3cff11dabdb2db90a5e88ece5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995556"
---
# <a name="icordebugilcodegetehclauses-method"></a>Metoda ICorDebugILCode::GetEHClauses
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zwraca wskaźnik do listy wyjątków, obsługa klauzule (EH), które są zdefiniowane dla tego języka pośredniego (IL).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cClauses`  
 [in] Pojemność magazynu `clauses` tablicy. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `pcClauses`  
 [out] Liczba klauzul, o których informacje są zapisywane `clauses` tablicy.  
  
 Klauzule  
 [out] Tablica [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) obiektów, które zawierają informacje dotyczące klauzul zdefiniowane dla tego IL obsługi wyjątków.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `cClauses` wynosi 0 i `pcClauses` ma wartość inną niż**null**, `pcClauses` jest ustawiona na liczbę dostępnych obsługi klauzulach wyjątków. Jeśli `cClauses` jest różna od zera, reprezentuje pojemność magazynu `clauses` tablicy. Po powrocie z metody `clauses` może zawierać maksymalnie `cClauses` elementów, a `pcClauses` jest ustawienie liczby klauzul rzeczywiście zapisanych na `clauses` tablicy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILCode, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [CorDebugEHClause, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
