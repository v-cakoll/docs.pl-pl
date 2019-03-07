---
title: ICorProfilerInfo2::GetArrayObjectInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fe86fbe7ee51e5f53eeea74d7d5a56046de5e00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484397"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo — Metoda
Pobiera szczegółowe informacje dotyczące obiektu array.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 [in] Identyfikator obiektu prawidłową tablicą.  
  
 `cDimensions`  
 [in] Ranga (liczba wymiarów) tablicy.  
  
 `pDimensionSizes`  
 [out] Tablica, która zawiera liczby całkowite, każdy reprezentuje rozmiar wymiaru tablicy.  
  
 `pDimensionLowerBounds`  
 [out] Tablica, która zawiera liczby całkowite, każda reprezentująca dolna granica wymiaru tablicy.  
  
 `ppData`  
 [out] Wskaźnik na adres surowy bufor dla tablicy, która jest poukładany zgodnie z konwencją języka C++.  
  
## <a name="remarks"></a>Uwagi  
 `pDimensionSizes` i `pDimensionLowerBounds` są równoległe tablic, więc elementy znajdujące się w ten sam indeks tablic są właściwości tego samego obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
