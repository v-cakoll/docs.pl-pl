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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62e70a2fe421651aac9a4921ca885c53c864c4f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101806"
---
# <a name="icorprofilerfunctionenumnext-method"></a>ICorProfilerFunctionEnum::Next — Metoda
Pobiera określoną liczbę funkcji ciągłego z sekwencyjną kolekcją funkcji, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba funkcji do pobrania.  
  
 `ids`  
 [out] Tablica `COR_PRF_FUNCTION` wartości, z których każdy reprezentuje funkcję pobrane.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby rzeczywistego zwrotu w funkcji `ids` tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`celt` elementy zostały zwrócone.|  
|S_FALSE|Mniej niż `celt` zwróconych elementów, co oznacza, że wyliczanie zostało zakończone.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerFunctionEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
