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
ms.openlocfilehash: 028207486f43e35086ed2e515eb3ae6bca304491
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866081"
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
 podczas Rozmiar tablic `classIds` i `cObjects`.  
  
 `classIds`  
 podczas Tablica identyfikatorów klasy, gdzie każdy identyfikator Określa klasę z co najmniej jednym wystąpieniem.  
  
 `cObjects`  
 podczas Tablica liczb całkowitych, gdzie każda liczba całkowita określa liczbę wystąpień odpowiadającej klasie w tablicy `classIds`.  
  
## <a name="remarks"></a>Uwagi  
 Tablice `classIds` i `cObjects` są tablicami równoległymi. Na przykład `classIds[i]` i `cObjects[i]` odwoływać się do tej samej klasy. Jeśli żadne wystąpienie klasy nie zostało utworzone od czasu wcześniejszego wyrzucania elementów bezużytecznych, Klasa zostanie pominięta. Wywołanie zwrotne `ObjectsAllocatedByClass` nie będzie raportować obiektów przyznanych w stercie dużego obiektu.  
  
 Liczby raportowane przez `ObjectsAllocatedByClass` są tylko Szacowana. Aby uzyskać dokładne liczby, użyj [ICorProfilerCallback:: ObjectAllocated —](icorprofilercallback-objectallocated-method.md).  
  
 Tablica `classIds` może zawierać jeden lub więcej wpisów o wartości null, Jeśli odpowiednia tablica `cObjects` ma typy, które są zwalniane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
