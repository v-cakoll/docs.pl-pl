---
title: "ICorProfilerFunctionEnum::Skip — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Skip Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ddde6069072092cfc0441686ce4d53aa0a4bd534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumskip-method"></a>ICorProfilerFunctionEnum::Skip — Metoda
Przesuwa kursor modułu wyliczającego z jego bieżącym położeniu tak, aby określoną liczbę elementów są pomijane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba elementów do pominięcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`celt`elementy zostały pominięte.|  
|WARTOŚCI S_FALSE|Mniej niż `celt` elementy zostały pominięte, co oznacza, że nie ma żadnych więcej elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Nowa pozycja kursora ten moduł wyliczający jest (bieżące położenie) + `celt`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerFunctionEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
