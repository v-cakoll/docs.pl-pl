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
ms.openlocfilehash: e6e6f4f6bdfba8deecb3661d88a881759da043ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456310"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo — Metoda
Pobiera szczegółowe informacje o tablicy obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
#### <a name="parameters"></a>Parametry  
 `objectId`  
 [in] Identyfikator obiektu prawidłowy tablicy.  
  
 `cDimensions`  
 [in] Ranga (liczba wymiarów) tablicy.  
  
 `pDimensionSizes`  
 [out] Tablica zawiera liczb całkowitych, każdy reprezentuje rozmiaru wymiaru tablicy.  
  
 `pDimensionLowerBounds`  
 [out] Tablica zawiera liczb całkowitych, każdy reprezentuje niższa granica wymiaru tablicy.  
  
 `ppData`  
 [out] Wskaźnik do adresu raw buforu dla tablicy, która jest rozmieszczona zgodnie z Konwencją C++.  
  
## <a name="remarks"></a>Uwagi  
 `pDimensionSizes` i `pDimensionLowerBounds` są równoległych tablic, więc elementy znajdujące się w tym samym indeksie w każdej macierzy właściwości tej samej jednostki.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
