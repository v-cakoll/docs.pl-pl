---
title: "ICorProfilerInfo::GetModuleMetaData — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleMetaData
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ad52460bcd6eb320e970cd0ce2078f2e93df353
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData — Metoda
Pobiera wystąpienie interfejsu metadanych, który jest mapowany na określony moduł.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, do którego zostanie zamapowane wystąpienie interfejsu.  
  
 `dwOpenFlags`  
 [in] Wartość [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczenia, który określa tryb w celu otwierania plików manifestu. Tylko `ofRead`, `ofWrite` i `ofNoTransform` bity są prawidłowe.  
  
 `riid`  
 [in] Odwołanie Identyfikatora (GUID) interfejsu metadanych, których wystąpienia mają zostać pobrane. Zobacz [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) listę interfejsów.  
  
 `ppOut`  
 [out] Wskaźnik do adresu wystąpienie interfejsu metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Może poprosić o metadanych, które ma zostać otwarty w trybie odczytu i zapisu, ale spowoduje wolniejsze wykonywanie metadanych programu, ponieważ zmiany wprowadzone do metadanych nie można zoptymalizować w porównaniu z kompilatora.  
  
 Niektóre moduły (takie jak moduły zasobów) mają Brak metadanych. W takich przypadkach `GetModuleMetaData` zwróci wartość HRESULT S_FALSE lub wartość null w *`ppOut`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
