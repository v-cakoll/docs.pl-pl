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
ms.openlocfilehash: e1dd6addd9053ffb6cf2ce23408673d8fca17cb5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496844"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>ICorProfilerInfo2::GetStaticFieldInfo — Metoda
Pobiera wartość wskazującą rodzaj static, który ma zastosowanie do określonego pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 podczas Identyfikator klasy, w której zdefiniowane jest pole statyczne.  
  
 `fieldToken`  
 podczas Token metadanych dla pola statycznego.  
  
 `pFieldInfo`  
 określoną Wskaźnik do wartości wyliczenia [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) , który wskazuje, czy określone pole jest statyczne, i jeśli tak, rodzaj static, który ma zastosowanie do pola.  
  
## <a name="remarks"></a>Uwagi  
 Te informacje mogą służyć do określenia, która funkcja ma zostać wywołana w celu pobrania adresu pola statycznego.  
  
 Kod profilera powinien nadal sprawdzać metadane pola statycznego, aby upewnić się, że faktycznie ma adres. Literały statyczne (czyli stałe) istnieją tylko w metadanych i nie mają adresu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
