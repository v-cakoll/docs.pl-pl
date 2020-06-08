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
ms.openlocfilehash: 368b8f270797beb525e0745a29990667913f4071
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497364"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo — Metoda
Pobiera szczegółowe informacje o obiekcie array.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 podczas Identyfikator prawidłowego obiektu tablicy.  
  
 `cDimensions`  
 podczas Ranga (liczba wymiarów) tablicy.  
  
 `pDimensionSizes`  
 określoną Tablica zawierająca liczby całkowite, z których każdy reprezentuje rozmiar wymiaru tablicy.  
  
 `pDimensionLowerBounds`  
 określoną Tablica zawierająca liczby całkowite, z których każda reprezentuje dolną granicę wymiaru tablicy.  
  
 `ppData`  
 określoną Wskaźnik na adres nieprzetworzonego buforu dla tablicy, który jest ustalany zgodnie z Konwencją języka C++.  
  
## <a name="remarks"></a>Uwagi  
 `pDimensionSizes`I `pDimensionLowerBounds` są to tablice równoległe, dlatego elementy znajdujące się w tym samym indeksie w każdej tablicy są cechami tej samej jednostki.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
