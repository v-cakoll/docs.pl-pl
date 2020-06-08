---
title: ICorProfilerInfo::IsArrayClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 2a3f5bb0c54935e524cc955a5e11aac75b0c0923
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497559"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass — Metoda
Określa, czy określona Klasa jest klasą Array.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 podczas Identyfikator klasy, która ma zostać zbadana.  
  
 `pBaseElemType`  
 określoną Wskaźnik do wartości wyliczenia CorElementType —, który wskazuje typ elementów tablicy.  
  
 `pBaseClassId`  
 określoną Wskaźnik do identyfikatora klasy elementów tablicy, jeśli jest dostępny.  
  
 `pcRank`  
 określoną Wskaźnik do liczby całkowitej, która wskazuje rangę (czyli liczbę wymiarów) tablicy.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określona Klasa jest klasą Array, `IsArrayClass` Metoda zwraca S_OK HRESULT i wartości dla wszystkich parametrów wyjściowych o wartości innej niż null. W przeciwnym razie zwraca S_FALSE.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
