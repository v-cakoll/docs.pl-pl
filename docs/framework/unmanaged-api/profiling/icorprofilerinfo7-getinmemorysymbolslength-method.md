---
title: Metoda ICorProfilerInfo7::GetInMemorySymbolsLength
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03c70b97e7af9fdc76c579c5940e2436232f6bc2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748651"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>Metoda ICorProfilerInfo7::GetInMemorySymbolsLength
[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]  
  
 Zwraca długość strumienia symboli w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, zawierająca strumień w pamięci.  
  
 pCountSymbolBytes  
 [out] Wskaźnik do `DWORD` wartość, gdy metoda zwróci wartość, zawiera długość strumienia w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `S_OK` Jeśli długość strumienia pamięci można ustalić, nawet jeśli ma wartość zero (0).  
  
 Metoda ta zwraca `CORPROF_E_MODULE_IS_DYNAMIC` Jeśli metoda został utworzony przy użyciu <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli moduł zawiera symbole w pamięci, długość strumienia jest umieszczany w `pCountSymbolBytes`. Jeśli moduł nie ma symboli w pamięci, `*pCountSymbolBytes = 0`.  
  
> [!NOTE]
>  Bieżąca implementacja nie obsługuje Reflection.Emit. Jeśli moduł został utworzony przy użyciu Reflection.Emit, metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
