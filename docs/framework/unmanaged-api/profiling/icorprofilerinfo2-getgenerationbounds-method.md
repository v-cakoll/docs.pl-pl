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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19288b5631fea8865530f936ac6d77c0286ee169
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110381"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds — Metoda
Pobiera regiony pamięci, które są segmenty stosu, które składają się na różnych generacji wyrzucania elementów w kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cObjectRanges`  
 [in] Liczba elementów przydzielonej przez obiekt wywołujący, aby uzyskać `ranges` tablicy.  
  
 `pcObjectRanges`  
 [out] Wskaźnik do liczby całkowitej określający łączna liczba zakresów, niektóre lub wszystkie z nich zostaną zwrócone w `ranges` tablicy.  
  
 `ranges`  
 [out] Tablica [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktur, z których każdy zawiera opis zakresu (czyli bloku) pamięci w generacji, która jest w trakcie wyrzucania elementów bezużytecznych.  
  
## <a name="remarks"></a>Uwagi  
 `GetGenerationBounds` Metodę można wywołać z dowolnego wywołania zwrotnego profilera, pod warunkiem, że wyrzucanie elementów bezużytecznych nie jest w toku. Oznacza to, mogą być wywoływane z dowolnego wywołania zwrotnego, z wyjątkiem tych, które mają miejsce między [icorprofilercallback2::garbagecollectionstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) i [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
 Większość przesunięcie pokoleń ma miejsce podczas wyrzucania elementów bezużytecznych. Generacje może rosnąć między operacjami, ale zwykle nie zmieniają położenie. W związku z tym, najbardziej interesujących miejsc do wywołania `GetGenerationBounds` znajdują się w `ICorProfilerCallback2::GarbageCollectionStarted` i `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Podczas uruchamiania programu niektóre obiekty są przydzielane przez środowisko uruchomieniowe języka wspólnego (CLR), zwykle w generacjach 3 i 0. W związku z tym według czasu, w kodzie zarządzanym rozpoczyna wykonywanie, generacje te będą już zawierać obiekty. Zwykle jest pusta, z wyjątkiem fikcyjnego obiektów, które są generowane przez moduł odśmiecania pamięci generacji 1 i 2. (Rozmiar obiektów zastępczy jest 12-bajtowy we wdrożeniach 32-bitowe środowisko CLR; rozmiar jest większy we wdrożeniach 64-bitowych). Może być również wyświetlany zakresów generacji 2, które znajdują się w modułach produkowane przez Native Image Generator (NGen.exe). W tym przypadku są obiekty w generacji 2 *mrożone obiekty*, które są przydzielane po uruchomieniu NGen.exe, a nie przez moduł odśmiecania pamięci.  
  
 Ta funkcja używa bufory przypisane do obiektu wywołującego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
