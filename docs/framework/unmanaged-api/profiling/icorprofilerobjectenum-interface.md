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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92370751b38029435b12c177b75cd4d9402369b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597209"
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum — Interfejs
Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji zamrożone obiekty, które są generowane przez [Ngen.exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|Pobiera wskaźnik interfejsu do kopii tego `ICorProfilerObjectEnum` interfejsu.|  
|[GetCount, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|Pobiera całkowitą liczbę zamrożone obiekty w kolekcji.|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|Pobiera określoną liczbę obiektów sąsiadujących z sekwencyjną kolekcją obiektów, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|Przenosi kursor ten moduł wyliczający pozycji początkowej sekwencji.|  
|[Skip, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|Przesuwa kursor tego modułu wyliczającego z jego bieżącej pozycji, dzięki czemu są pomijane przez określoną liczbę elementów.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorProfilerObjectEnum` Interfejs jest moduł wyliczający. Umożliwia odbiorcy tablicy do ściągnięcia elementów od nadawcy szybkością, która jest odpowiednia dla odbiorcy. Innymi słowy odbiornik jest w stanie jawnie sterowania przepływem elementów tablicy, zapobiegając w ten sposób problemy związane z przekazywania dużych tablic jako parametrów metody.  
  
 Użyj [icorprofilerinfo2::enummodulefrozenobjects —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md) uzyskać wskaźnik do `ICorProfilerObjectEnum` interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumModuleFrozenObjects, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
