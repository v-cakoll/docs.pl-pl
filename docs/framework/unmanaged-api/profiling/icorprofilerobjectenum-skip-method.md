---
title: ICorProfilerObjectEnum::Skip — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bcc837fede7e7db59bdf88a0b5434a7c1924335
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210948"
---
# <a name="icorprofilerobjectenumskip-method"></a>ICorProfilerObjectEnum::Skip — Metoda
Przesuwa kursor tego modułu wyliczającego z jego bieżącej pozycji, dzięki czemu są pomijane przez określoną liczbę elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba elementów, które mają zostać pominięte.  
  
## <a name="remarks"></a>Uwagi  
 Nowe położenie kursora ten moduł wyliczający jest: (bieżącej pozycji) + `celt` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerObjectEnum — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
