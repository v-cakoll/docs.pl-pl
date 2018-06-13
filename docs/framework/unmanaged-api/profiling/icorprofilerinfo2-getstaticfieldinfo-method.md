---
title: ICorProfilerInfo2::GetStaticFieldInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2ab0d482366b037f92a55f00dd33df8a312e84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454435"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>ICorProfilerInfo2::GetStaticFieldInfo — Metoda
Pobiera wartość wskazującą, rodzaj statyczną, która ma zastosowanie do określonego pola.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [in] Identyfikator klasy, w którym zdefiniowano pola statycznego.  
  
 `fieldToken`  
 [in] Token metadanych dla pola statycznego.  
  
 `pFieldInfo`  
 [out] Wskaźnik do wartości [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) Wyliczenie wskazujące, czy określone pole jest statyczny, a jeśli tak, rodzaj static dotyczący pola.  
  
## <a name="remarks"></a>Uwagi  
 Te informacje można określić funkcji do wywołania w celu uzyskania adresu pola statycznego.  
  
 Kod profilera należy sprawdzić metadanych dla pola statycznego upewnić się, że faktycznie ma adres. Literały statyczne (to znaczy stałych) istnieje tylko w metadanych i nie ma adresu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
