---
title: "ICorProfilerInfo::IsArrayClass — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.IsArrayClass
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cd07541095158d17b80333b83015d6b1f33a5dcc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass — Metoda
Określa, czy określona klasa jest klasą tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [in] Identyfikator klasy należy zbadać.  
  
 `pBaseElemType`  
 [out] Wskaźnik do wartości wyliczenia CorElementType, który wskazuje na typ elementów tablicy.  
  
 `pBaseClassId`  
 [out] Wskaźnik do Identyfikatora klasy elementów tablicy, jeśli jest dostępna.  
  
 `pcRank`  
 [out] Wskaźnik na liczbę całkowitą, która wskazuje rangą tablicy (to znaczy, że liczba wymiarów).  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określona klasa jest klasą tablicy `IsArrayClass` metoda zwraca wartość S_OK HRESULT i wartości parametrów wyjściowych inną niż null. W przeciwnym wypadku zwraca wartości S_FALSE.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
