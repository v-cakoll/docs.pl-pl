---
title: ICorProfilerInfo2::GetStringLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b87444165f0504964b6489beb562ca2e8bd4697e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524289"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout — Metoda
Pobiera informacje o układ obiektu ciągu. Ta metoda jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]i są zastępowane [icorprofilerinfo3::getstringlayout2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBufferLengthOffset`  
 [out] Wskaźnik do przesunięcia lokalizacji względem `ObjectID` wskaźnika, który przechowuje długość ciągu. Długość jest przechowywany jako `DWORD`.  
  
> [!NOTE]
>  Ten parametr zwraca długość ciągu, nie długość buforu. Długość buforu nie jest już dostępna.  
  
 `PStringLengthOffset`  
 [out] Wskaźnik do przesunięcia lokalizacji względem `ObjectID` wskaźnika, która przechowuje długość ciągu, sam. Długość jest przechowywany jako `DWORD`.  
  
 `pBufferOffset`  
 [out] Wskaźnik do przesunięcia buforu względem `ObjectID` wskaźnika, który przechowuje ciąg znaków dwubajtowych.  
  
## <a name="remarks"></a>Uwagi  
 `GetStringLayout` Metoda pobiera przesunięcia względem `ObjectID` wskaźnika, lokalizacji, w których przechowywane są następujące:  
  
-   Długość buforu ciągu.  
  
-   Długość ciągu, sam.  
  
-   Bufor, który zawiera rzeczywiste ciąg znaków dwubajtowych.  
  
 Ciągi mogą być zakończony znakiem null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
