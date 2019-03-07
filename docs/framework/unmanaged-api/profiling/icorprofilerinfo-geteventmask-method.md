---
title: ICorProfilerInfo::GetEventMask — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1051f42788b3c2a63780f43f5784b063ef23027
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483994"
---
# <a name="icorprofilerinfogeteventmask-method"></a>ICorProfilerInfo::GetEventMask — Metoda
Pobiera bieżący kategorie zdarzeń, dla których program profilujący chce otrzymywać powiadomienia o zdarzeniach środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwEvents`  
 [out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń. Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia. Bity są opisane w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Należy wywołać [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metody zamiast tej metody. Mimo że `SetEventMask` metoda może być obsługiwany, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) udostępnia dodatkowe funkcje.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [GetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
