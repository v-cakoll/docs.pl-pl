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
ms.openlocfilehash: 89a2424548bb577e3580d6eaa72f61e5cf9ccc7d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991812"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData — Metoda
Pobiera wystąpienie interfejsu metadanych, który jest mapowany do określonego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, do którego będą mapowane wystąpienia interfejsu.  
  
 `dwOpenFlags`  
 [in] Wartość [coropenflags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczenie, które określa tryb przy otwieraniu plików manifestu. Tylko `ofRead`, `ofWrite` i `ofNoTransform` bity są prawidłowe.  
  
 `riid`  
 [in] Odwołanie Identyfikatora (GUID), którego wystąpienie będzie można pobrać interfejsu metadanych. Zobacz [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) listę interfejsów.  
  
 `ppOut`  
 [out] Wskaźnik na adres metadanych wystąpienia interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Możesz poprosić o metadanych były otwierane w trybie odczytu/zapisu, ale spowoduje wolniejsze wykonywanie metadanych programu, ponieważ zmiany wprowadzone do metadanych nie można zoptymalizować, jakie były z kompilatora.  
  
 Niektóre moduły (np. moduły zasobów) mają Brak metadanych. W takich przypadkach `GetModuleMetaData` zwróci wartość HRESULT S_FALSE lub wartość null w *`ppOut`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
