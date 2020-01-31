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
ms.openlocfilehash: 53c01d2db44f4d0adf1ba5b9cc225ab49581aa5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868346"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]  
  
 Odczytuje bajty z strumienia symboli w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Identyfikator modułu zawierającego strumień znajdujący się w pamięci.  
  
 `symbolsReadOffset`  
 podczas Przesunięcie w strumieniu w pamięci, od którego ma zostać rozpoczęte odczytywanie bajtów.  
  
 `pSymbolBytes`  
 określoną Wskaźnik do buforu, do którego zostaną skopiowane dane. Bufor powinien mieć `countSymbolBytes` dostępnego miejsca.  
  
 `countSymbolBytes`  
 podczas Liczba bajtów do skopiowania.  
  
 `pCountSymbolBytesRead`  
 określoną Gdy metoda zwraca, zawiera rzeczywistą liczbę odczytanych bajtów.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `S_OK`, jeśli odczytano różną od zera liczbę bajtów.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, jeśli moduł został utworzony przy użyciu <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `ReadInMemorySymbols` próbuje odczytać `countSymbolBytes` danych, zaczynając od przesunięcia `symbolsReadOffset` w strumieniu w pamięci. Dane są kopiowane do `pSymbolBytes`, które powinny mieć `countSymbolBytes` dostępnego miejsca.     `pCountSymbolsBytesRead` zawiera rzeczywistą liczbę odczytanych bajtów, która może być mniejsza niż `countSymbolBytes`, jeśli osiągnięto koniec strumienia.  
  
> [!NOTE]
> Bieżąca implementacja nie obsługuje odbicia. emisji. Jeśli moduł został utworzony przy użyciu odbicia. Emituj, metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo7, interfejs](icorprofilerinfo7-interface.md)
