---
title: ICorProfilerInfo2::EnumModuleFrozenObjects — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
ms.openlocfilehash: 27b3037459ac4f995e37515f6e96c28449c80a4f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862948"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a>ICorProfilerInfo2::EnumModuleFrozenObjects — Metoda
Pobiera moduł wyliczający, który umożliwia iterację w odniesieniu do zablokowanych obiektów w określonym module. Ta metoda jest przestarzała.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 podczas Identyfikator modułu zawierającego zamrożone obiekty, które mają zostać wyliczone.  
  
 `ppEnum`  
 określoną Wskaźnik do adresu interfejsu [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) , który wylicza zamrożone obiekty.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 3,5, 3,0 sp1, 3,0, 2,0 SP1, 2,0  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
