---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 662863ec69e464dafe893552f1d81755313acc75
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153325"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Obsługiwane w [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] i nowszych wersjach]  
  
 Odczytuje bajtów ze strumienia symboli w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, zawierająca strumień w pamięci.  
  
 `symbolsReadOffset`  
 [in] Przesunięcie w strumieniu w pamięci, w którym ma zostać rozpoczęte odczytywanie bajtów.  
  
 `pSymbolBytes`  
 [out] Wskaźnik do buforu, do którego zostaną skopiowane dane. Rozmiar buforu powinien mieć `countSymbolBytes` dostępnego miejsca.  
  
 `countSymbolBytes`  
 [in] Liczba bajtów do skopiowania.  
  
 `pCountSymbolBytesRead`  
 [out] Gdy metoda zwróci wartość, zawiera rzeczywista liczba odczytanych bajtów.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`, jeśli zostały wczytane niezerową liczbę bajtów.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, jeśli moduł został utworzony przy użyciu <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Uwagi  
 `ReadInMemorySymbols` Metoda podejmuje próbę odczytu `countSymbolBytes` danych, rozpoczynając od przesunięcia `symbolsReadOffset` w strumieniu w pamięci. Dane są kopiowane do `pSymbolBytes`, które powinny mieć `countSymbolBytes` dostępnego miejsca.     `pCountSymbolsBytesRead` zawiera rzeczywista liczba bajtów odczytanych, który może być mniejsza niż `countSymbolBytes` Jeśli osiągnięty zostanie koniec strumienia.  
  
> [!NOTE]
>  Bieżąca implementacja nie obsługuje Reflection.Emit. Jeśli moduł został utworzony przy użyciu Reflection.Emit, metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
