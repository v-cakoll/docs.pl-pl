---
title: ICorProfilerFunctionEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
ms.openlocfilehash: 9c7fa25712858d1119b45fc742a5d23454b55273
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864470"
---
# <a name="icorprofilerfunctionenumnext-method"></a>ICorProfilerFunctionEnum::Next — Metoda
Pobiera określoną liczbę funkcji ciągłych z sekwencyjnego zbioru funkcji, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba funkcji do pobrania.  
  
 `ids`  
 określoną Tablica wartości `COR_PRF_FUNCTION`, z których każdy reprezentuje pobraną funkcję.  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby funkcji faktycznie zwracanych w tablicy `ids`.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|zwrócono `celt` elementów.|  
|S_FALSE|Zwrócono mniej niż `celt` elementów, co oznacza, że Wyliczenie zostało zakończone.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerFunctionEnum, interfejs](icorprofilerfunctionenum-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
