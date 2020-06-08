---
title: ICorProfilerCallback::ObjectsAllocatedByClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: 7176c0f88daad64f793131aca8c6d9fa592a878c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503279"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass — Metoda
Powiadamia profiler o liczbie wystąpień każdej określonej klasy, które zostały utworzone od czasu ostatniego wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cClassCount`  
 podczas Rozmiar `classIds` `cObjects` tablic i.  
  
 `classIds`  
 podczas Tablica identyfikatorów klasy, gdzie każdy identyfikator Określa klasę z co najmniej jednym wystąpieniem.  
  
 `cObjects`  
 podczas Tablica liczb całkowitych, gdzie każda liczba całkowita określa liczbę wystąpień odpowiadającej klasie w `classIds` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 `classIds`Tablice i `cObjects` są tablicami równoległymi. Na przykład, `classIds[i]` i `cObjects[i]` odwoływać się do tej samej klasy. Jeśli żadne wystąpienie klasy nie zostało utworzone od czasu wcześniejszego wyrzucania elementów bezużytecznych, Klasa zostanie pominięta. `ObjectsAllocatedByClass`Wywołanie zwrotne nie będzie zgłaszać obiektów przyznanych w stercie dużego obiektu.  
  
 Liczby raportowane przez `ObjectsAllocatedByClass` są tylko Szacowana. Aby uzyskać dokładne liczby, użyj [ICorProfilerCallback:: ObjectAllocated —](icorprofilercallback-objectallocated-method.md).  
  
 `classIds`Tablica może zawierać jeden lub więcej wpisów o wartości null, Jeśli odpowiednia `cObjects` Tablica zawiera typy, które są zwalniane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
