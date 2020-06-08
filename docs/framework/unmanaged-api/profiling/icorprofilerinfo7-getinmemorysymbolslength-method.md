---
title: 'ICorProfilerInfo7:: GetInMemorySymbolsLength, Metoda'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 43d6bdeae5f522bd73b0bdf3a5c403ec69ee384c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495441"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7:: GetInMemorySymbolsLength, Metoda
[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]  
  
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
 podczas Identyfikator modułu zawierającego strumień znajdujący się w pamięci.  
  
 pCountSymbolBytes  
 określoną Wskaźnik do `DWORD` wartości, która, gdy zwraca metodę, zawiera długość strumienia w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `S_OK` , jeśli długość strumienia pamięci można ustalić, nawet jeśli jest równa zero (0).  
  
 Metoda zwraca, `CORPROF_E_MODULE_IS_DYNAMIC` Jeśli metoda została utworzona przy użyciu <xref:System.Reflection.Emit?displayProperty=nameWithType> .  
  
## <a name="remarks"></a>Uwagi  
 Jeśli moduł zawiera symbole w pamięci, długość strumienia jest umieszczana w `pCountSymbolBytes` . Jeśli moduł nie zawiera symboli w pamięci, `*pCountSymbolBytes = 0` .  
  
> [!NOTE]
> Bieżąca implementacja nie obsługuje odbicia. emisji. Jeśli moduł został utworzony przy użyciu odbicia. Emituj, metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo7, interfejs](icorprofilerinfo7-interface.md)
