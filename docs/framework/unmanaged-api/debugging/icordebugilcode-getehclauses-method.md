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
ms.openlocfilehash: ac9a4e4b54b302afeae4ede1dd574c15ded3ff12
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788601"
---
# <a name="icordebugilcodegetehclauses-method"></a>Metoda ICorDebugILCode::GetEHClauses
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zwraca wskaźnik do listy klauzul obsługi wyjątków (EH), które są zdefiniowane dla tego języka pośredniego (IL).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cClauses`  
 podczas Pojemność magazynu tablicy `clauses`. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `pcClauses`  
 określoną Liczba klauzul, na których informacje są zapisywane w tablicy `clauses`.  
  
 warunki  
 określoną Tablica obiektów [CorDebugEHClause](cordebugehclause-structure.md) , które zawierają informacje na temat klauzul obsługi wyjątków zdefiniowane dla tego Il.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `cClauses` ma wartość 0, a `pcClauses` ma**wartość**różną od null, `pcClauses` jest ustawiona na liczbę dostępnych klauzul obsługi wyjątków. Jeśli `cClauses` jest różna od zera, reprezentuje pojemność magazynu `clauses` tablicy. Gdy metoda zwraca, `clauses` zawiera maksymalnie `cClauses` elementów, a `pcClauses` jest ustawiona na liczbę klauzul, które faktycznie Zapisano do tablicy `clauses`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILCode, interfejs](icordebugilcode-interface.md)
- [CorDebugEHClause, struktura](cordebugehclause-structure.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
