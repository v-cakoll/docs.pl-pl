---
title: "ICorProfilerObjectEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum
helpviewer_keywords: ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b46f33485a63404f11dc0606e420ec9c3c43f1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum — Interfejs
Udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji zablokowane obiekty, które są generowane przez [Ngen.exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|Pobiera wskaźnika interfejsu kopię `ICorProfilerObjectEnum` interfejsu.|  
|[GetCount — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|Pobiera całkowitą liczbę obiektów zablokowane w kolekcji.|  
|[Next — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|Pobiera określoną liczbę obiektów ciągłe z sekwencyjną kolekcją obiektów, zaczynając od modułu wyliczającego bieżącej pozycji w sekwencji.|  
|[Reset — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|Przesuwa kursor ten moduł wyliczający pozycji początkowej sekwencji.|  
|[SKIP — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|Przesuwa kursor tego modułu wyliczającego z jego bieżącym położeniu, dzięki czemu określoną liczbę elementów są pomijane.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorProfilerObjectEnum` Interfejs jest moduł wyliczający. Umożliwia odbiorcy tablicy do ściągania elementów od nadawcy szybkością, który jest odpowiedni dla odbiornika. Innymi słowy odbiorca jest w stanie jawnie sterowanie przepływem elementów tablicy, zapobiegając problemy związane z przekazywanie dużych tablic jako parametrów metody.  
  
 Użyj [ICorProfilerInfo2::EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md) uzyskać wskaźnik do `ICorProfilerObjectEnum` interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumModuleFrozenObjects — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
