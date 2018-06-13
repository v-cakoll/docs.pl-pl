---
title: ICorProfilerInfo::GetModuleMetaData — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2491b700e8fac512f0d782a42e30ae3114e93c3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455549"
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
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
