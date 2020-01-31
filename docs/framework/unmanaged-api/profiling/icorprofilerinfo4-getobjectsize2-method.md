---
title: ICorProfilerInfo4::GetObjectSize2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: 441f7743ba01884592393ce9382348fbecaeaa9d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861882"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a>ICorProfilerInfo4::GetObjectSize2 — Metoda
Zwraca rozmiar określonego obiektu. Zastępuje metodę [ICorProfilerInfo:: GetObjectSize —](icorprofilerinfo-getobjectsize-method.md) przez raportowanie rozmiarów obiektów, które są większe niż to, co może być wyrażone w `ULONG`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 podczas Identyfikator obiektu.  
  
 `pcSize`  
 określoną Wskaźnik do rozmiaru obiektu, w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 Różne obiekty tego samego typu często mają ten sam rozmiar. Jednak niektóre typy, takie jak tablice lub ciągi, mogą mieć różne rozmiary dla każdego obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo4, interfejs](icorprofilerinfo4-interface.md)
