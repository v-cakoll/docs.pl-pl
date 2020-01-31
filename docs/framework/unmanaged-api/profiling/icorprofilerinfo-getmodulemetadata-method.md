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
ms.openlocfilehash: 6e787de6287dc5b3091d3671d3da2f2154b12e88
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869927"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData — Metoda
Pobiera wystąpienie interfejsu metadanych, które mapuje do określonego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 podczas Identyfikator modułu, do którego zostanie zamapowana wystąpienie interfejsu.  
  
 `dwOpenFlags`  
 podczas Wartość wyliczenia [CorOpenFlags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) , która określa tryb otwierania plików manifestu. Tylko `ofRead`, `ofWrite` i `ofNoTransform` BITS są prawidłowe.  
  
 `riid`  
 podczas Identyfikator odwołania (GUID) interfejsu metadanych, którego wystąpienie zostanie pobrane. Zobacz [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) , aby uzyskać listę interfejsów.  
  
 `ppOut`  
 określoną Wskaźnik do adresu wystąpienia interfejsu metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Możesz poproszenie o otwarcie metadanych w trybie odczytu/zapisu, ale spowoduje to wolniejsze wykonanie tego programu, ponieważ nie można zoptymalizować zmian wprowadzonych w metadanych, ponieważ znajdowały się one w kompilatorze.  
  
 Niektóre moduły (takie jak moduły zasobów) nie mają metadanych. W takich przypadkach `GetModuleMetaData` zwróci wartość HRESULT S_FALSE i ma wartość null w`ppOut`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
