---
title: ICorProfilerModuleEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
ms.openlocfilehash: 695a4386d9399a079df41f11f52a3185083784ed
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861388"
---
# <a name="icorprofilermoduleenumnext-method"></a>ICorProfilerModuleEnum::Next — Metoda
Pobiera określoną liczbę modułów ciągłych z sekwencyjnego zbioru modułów, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba modułów do pobrania.  
  
 `ids`  
 określoną Tablica wartości `ModuleID`, z których każdy reprezentuje pobrany moduł.  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby elementów faktycznie zwracanych w tablicy `ids`.  
  
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

- [ICorProfilerModuleEnum, interfejs](icorprofilermoduleenum-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
