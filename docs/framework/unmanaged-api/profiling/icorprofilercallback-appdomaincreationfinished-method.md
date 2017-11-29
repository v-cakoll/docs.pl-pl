---
title: "ICorProfilerCallback::AppDomainCreationFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainCreationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d21198253e10434b37261d34cf12ef60c26f7e71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a>ICorProfilerCallback::AppDomainCreationFinished — Metoda
Powiadamia profilera, czy domena aplikacji została utworzona.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
#### <a name="parameters"></a>Parametry  
 `appDomainId`  
 [in] Określa domenę, która została utworzona.  
  
 `hrStatus`  
 [in] HRESULT, która wskazuje, czy Tworzenie domeny aplikacji została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Identyfikator aplikacji jest nieprawidłowy dla żądania żadnych informacji do `AppDomainCreationFinished` metoda jest wywoływana.  
  
 Niektóre elementy ładowania domeny aplikacji mogą nadal po `AppDomainCreationFinished` wywołania zwrotnego. Błąd HRESULT w `hrStatus` oznacza błąd. Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część tworzenia domeny aplikacji zakończyła się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
