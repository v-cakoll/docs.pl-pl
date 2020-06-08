---
title: ICorProfilerObjectEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum
helpviewer_keywords:
- ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type:
- apiref
ms.openlocfilehash: 5ebe99dd8d1d7ec73cd140991a4b13dfa381791d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494647"
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum — Interfejs
Zapewnia metody sekwencyjnej iteracji przez kolekcję zamrożonych obiektów, które są generowane przez program [Ngen. exe (Generator obrazu natywnego)](../../tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone — Metoda](icorprofilerobjectenum-clone-method.md)|Pobiera wskaźnik interfejsu do kopii tego `ICorProfilerObjectEnum` interfejsu.|  
|[GetCount — Metoda](icorprofilerobjectenum-getcount-method.md)|Pobiera łączną liczbę zablokowanych obiektów w kolekcji.|  
|[Next — Metoda](icorprofilerobjectenum-next-method.md)|Pobiera określoną liczbę obiektów ciągłego z kolekcji sekwencyjnej obiektów, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.|  
|[Reset — Metoda](icorprofilerobjectenum-reset-method.md)|Przenosi ten wskaźnik modułu wyliczającego do początkowego położenia sekwencji.|  
|[Skip — Metoda](icorprofilerobjectenum-skip-method.md)|Przesuwa kursor tego modułu wyliczającego z jego bieżącej pozycji, tak aby określona liczba elementów została pominięta.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorProfilerObjectEnum`Interfejs jest modułem wyliczającym. Umożliwia odbiorcom tablicy ściąganie elementów od nadawcy według stawki, która jest odpowiednia dla odbiornika. Innymi słowy, odbiorca może jawnie kontrolować przepływ elementów tablicy, co pozwala uniknąć problemów związanych z przekazywaniem dużych tablic jako parametrów metody.  
  
 Użyj [ICorProfilerInfo2:: EnumModuleFrozenObjects —](icorprofilerinfo2-enummodulefrozenobjects-method.md) , aby uzyskać wskaźnik do `ICorProfilerObjectEnum` interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [EnumModuleFrozenObjects, metoda](icorprofilerinfo2-enummodulefrozenobjects-method.md)
