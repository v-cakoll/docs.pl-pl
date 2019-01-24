---
title: ICorProfilerThreadEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25a6baea0cdd92d6d214ab8a697b0c00c44c42bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664580"
---
# <a name="icorprofilerthreadenumnext-method"></a>ICorProfilerThreadEnum::Next — Metoda
Pobiera określoną liczbę wątków sąsiadujących z sekwencyjną kolekcją wątków, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba wątków do pobierania.  
  
 `ids`  
 [out] Tablica `ThreadID` wartości, z których każdy reprezentuje pobrane wątku.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby wątków rzeczywistego zwrotu w `ids` tablicy.  
  
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
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerThreadEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
