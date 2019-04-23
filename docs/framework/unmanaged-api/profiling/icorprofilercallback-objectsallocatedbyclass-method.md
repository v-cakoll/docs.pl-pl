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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f5d2c08abbcab6bc1a6d0569b8e70d7c919def
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195868"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass — Metoda
Powiadamia program profilujący o liczbę wystąpień każdej określonej klasy, które zostały utworzone od najnowszych wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cClassCount`  
 [in] Rozmiar `classIds` i `cObjects` tablic.  
  
 `classIds`  
 [in] Tablica identyfikatorów, w którym każdy identyfikator Określa klasę z co najmniej jednego wystąpienia klasy.  
  
 `cObjects`  
 [in] Tablica liczb całkowitych, gdzie każda liczba całkowita określa liczbę wystąpień dla odpowiedniej klasy w `classIds` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 `classIds` i `cObjects` tablic są tablicami równoległych. Na przykład `classIds[i]` i `cObjects[i]` odwoływać się do tej samej klasy. Jeśli żadne wystąpienie klasy został utworzony od czasu poprzedniego wyrzucania elementów bezużytecznych, klasa jest pomijana. `ObjectsAllocatedByClass` Wywołanie zwrotne nie będą zgłaszać obiekty przydzielone w stosie dużego obiektu.  
  
 Liczby zgłoszonych przez `ObjectsAllocatedByClass` są jedynie do oszacowania. Dokładna liczba użyć [icorprofilercallback::objectallocated —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).  
  
 `classIds` Macierzy może zawierać co najmniej jeden wpis o wartości null, jeśli odpowiedni `cObjects` tablica zawiera typy, które są zwalniane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
