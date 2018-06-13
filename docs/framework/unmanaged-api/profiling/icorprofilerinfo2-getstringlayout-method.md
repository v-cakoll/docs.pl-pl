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
ms.openlocfilehash: 8d1bd732a82028afe809f4c2141e1d61668eae1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454925"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout — Metoda
Pobiera informacje o układzie z obiektem ciągu. Ta metoda jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]i zostało zastąpione przez [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBufferLengthOffset`  
 [out] Wskaźnik do przesunięcie lokalizacji względem `ObjectID` wskaźnika, która przechowuje długość ciągu. Długość jest przechowywana jako `DWORD`.  
  
> [!NOTE]
>  Ten parametr zwraca długość ciągu, nie długość buforu. Długość buforu nie jest już dostępny.  
  
 `PStringLengthOffset`  
 [out] Wskaźnik do przesunięcie lokalizacji względem `ObjectID` wskaźnika, przechowujący długość sam ciąg. Długość jest przechowywana jako `DWORD`.  
  
 `pBufferOffset`  
 [out] Wskaźnik do przesunięcie buforu względem `ObjectID` wskaźnika, zawierający ciąg znaki dwubajtowe.  
  
## <a name="remarks"></a>Uwagi  
 `GetStringLayout` Metoda pobiera przesunięcia względem `ObjectID` wskaźnik lokalizacji, w których przechowywane są następujące:  
  
-   Długość buforu ciągu.  
  
-   Długość ciągu samej siebie.  
  
-   Bufor, który zawiera ciąg rzeczywiste znaki dwubajtowe.  
  
 Ciągi może być zerem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
