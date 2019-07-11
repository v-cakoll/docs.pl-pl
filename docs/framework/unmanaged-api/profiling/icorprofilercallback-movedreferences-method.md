---
title: ICorProfilerCallback::MovedReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c037f2509aaa0a5e4c3f7a844614742b6f21bec3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769138"
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences — Metoda
Wywołuje się, aby zgłosić nowy układ obiektów w stercie wyniku kompaktowania wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 [in] Liczba bloków ciągłych obiektów, które przeniesione w wyniku kompaktowania wyrzucania elementów bezużytecznych. Oznacza to, że wartość `cMovedObjectIDRanges` jest całkowity rozmiar `oldObjectIDRangeStart`, `newObjectIDRangeStart`, i `cObjectIDRangeLength` tablic.  
  
 Następne trzy argumenty `MovedReferences` są tablicami równoległych. Innymi słowy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, i `cObjectIDRangeLength[i]` dotyczą wszystkich jeden blok ciągłych obiektów.  
  
 `oldObjectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest stary (wstępne wyrzucania elementów bezużytecznych) początkowy adres bloku ciągłych, obiekty aktywne w pamięci.  
  
 `newObjectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest nowy adres początkowy (po wyrzucania elementów bezużytecznych), bloku ciągłych, obiekty aktywne w pamięci.  
  
 `cObjectIDRangeLength`  
 [in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku ciągłych obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, w której podano odwołanie w `oldObjectIDRangeStart` i `newObjectIDRangeStart` tablic.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  Ta metoda zgłasza rozmiary jako `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych. Aby uzyskać rozmiar obiektów, które są większe niż 4 GB, użyj [icorprofilercallback4::movedreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metody zamiast tego.  
  
 Kompaktowania moduł odśmiecania pamięci odzyskuje pamięć zajęta przez obiekty martwe i kompaktuje, które zwolnienie miejsca. W rezultacie obiekty na żywo mogą być przeniesione w stosie, i `ObjectID` wartości rozdzielonych powiadomienia mogą ulec zmianie.  
  
 Przyjęto założenie, że istniejące `ObjectID` wartość (`oldObjectID`) znajduje się w następującym zakresie:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 W tym przypadku przesunięcie od początku zakresu do rozpoczęcia obiektu jest następująca:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Dla dowolnej wartości `i` znajdujący się w następującym zakresie:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 można obliczyć nową `ObjectID` w następujący sposób:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Żaden z `ObjectID` wartości przekazanych przez `MovedReferences` obowiązują podczas wywołania zwrotnego, ponieważ wyrzucania elementów bezużytecznych może być w trakcie przenoszenia obiektów z lokalizacji starej do nowej lokalizacji. W związku z tym, profilowania nie należy próbować Zbadaj obiekty podczas `MovedReferences` wywołania. A [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wywołania zwrotnego wskazuje, że wszystkie obiekty zostały przeniesione do ich nowych lokalizacji i inspekcji mogą być wykonywane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [MovedReferences2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
