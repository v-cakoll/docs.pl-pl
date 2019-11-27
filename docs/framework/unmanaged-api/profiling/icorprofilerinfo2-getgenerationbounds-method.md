---
title: ICorProfilerInfo2::GetGenerationBounds — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
ms.openlocfilehash: 11157bca2d0f0be2b9b9bc36c382188a43db22a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433126"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds — Metoda
Pobiera obszary pamięci, które są segmentami sterty, które tworzą różne generacje wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cObjectRanges`  
 podczas Liczba elementów przyznanych przez obiekt wywołujący dla tablicy `ranges`.  
  
 `pcObjectRanges`  
 określoną Wskaźnik do liczby całkowitej, która określa łączną liczbę zakresów, część lub wszystkie zostaną zwrócone w tablicy `ranges`.  
  
 `ranges`  
 określoną Tablica struktur [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) , z których każdy opisuje zakres (czyli blok) pamięci w ramach generacji, która nie powoduje wyrzucania elementów bezużytecznych.  
  
## <a name="remarks"></a>Uwagi  
 Metodę `GetGenerationBounds` można wywołać z dowolnego wywołania zwrotnego profilera, pod warunkiem, że odzyskiwanie pamięci nie jest w toku.

 Większość przesunięć generacji odbywa się podczas odzyskiwania pamięci. Generacji mogą wzrosnąć między kolekcjami, ale zazwyczaj nie można ich przenosić. W związku z tym najbardziej interesujące miejsca do wywołania `GetGenerationBounds` są `ICorProfilerCallback2::GarbageCollectionStarted` i `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Podczas uruchamiania programu niektóre obiekty są przydzielone przez środowisko uruchomieniowe języka wspólnego (CLR), zazwyczaj w generacjach 3 i 0. W rezultacie przez kod zarządzany przez czas, te generacje zawierają już obiekty. Generacje 1 i 2 zwykle będą puste, z wyjątkiem obiektów fikcyjnych generowanych przez moduł wyrzucania elementów bezużytecznych. (Rozmiar fikcyjnych obiektów to 12 bajtów w 32-bitowych implementacjach środowiska CLR; rozmiar jest większy w przypadku implementacji 64-bitowych). Możesz również zobaczyć zakresy generacji 2, które znajdują się w modułach wytwarzanych przez generator obrazu natywnego (NGen. exe). W takim przypadku obiekty w generacji 2 są *obiektami zablokowanymi*, które są przydzielone podczas uruchamiania programu Ngen. exe, a nie przez moduł wyrzucania elementów bezużytecznych.  
  
 Ta funkcja używa buforów przyznanych przez obiekt wywołujący.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
