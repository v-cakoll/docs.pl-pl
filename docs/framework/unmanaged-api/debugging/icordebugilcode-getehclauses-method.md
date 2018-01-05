---
title: Metoda ICorDebugILCode::GetEHClauses
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode.GetEHClauses
api_location: mscordbi.dll
api_type: COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32b3a7bf7edaf15e44ea65e2d3b4f5037add8d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcodegetehclauses-method"></a>Metoda ICorDebugILCode::GetEHClauses
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zwraca wskaźnik do listy klauzule (EH), które są zdefiniowane dla tego języka pośrednim (IL) obsługi wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cClauses`  
 [in] Pojemność `clauses` tablicy. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `pcClauses`  
 [out] Liczba klauzul, o których informacje są zapisywane w `clauses` tablicy.  
  
 klauzule  
 [out] Tablica [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) obiektów, które zawierają informacje na temat zdefiniowane dla tego IL klauzule obsługi wyjątków.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `cClauses` 0 i `pcClauses` ma wartość inną niż**null**, `pcClauses` wynosi liczba dostępnych klauzule obsługi wyjątków. Jeśli `cClauses` jest różna od zera, reprezentuje pojemność `clauses` tablicy. Gdy metoda zwróci wartość, `clauses` może zawierać maksymalnie `cClauses` elementów, i `pcClauses` ma ustawioną wartość liczba klauzul faktycznie zapisane `clauses` tablicy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugILCode, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [CorDebugEHClause, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
