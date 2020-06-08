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
ms.openlocfilehash: 62b34128be99ce7750d45e6c19e26bef7fcc98c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502954"
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
 podczas Wartość wyliczenia [CorOpenFlags —](../metadata/coropenflags-enumeration.md) , która określa tryb otwierania plików manifestu. Tylko `ofRead` `ofWrite` `ofNoTransform` bity i są prawidłowe.  
  
 `riid`  
 podczas Identyfikator odwołania (GUID) interfejsu metadanych, którego wystąpienie zostanie pobrane. Zobacz [interfejsy metadanych](../metadata/metadata-interfaces.md) , aby uzyskać listę interfejsów.  
  
 `ppOut`  
 określoną Wskaźnik do adresu wystąpienia interfejsu metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Możesz poproszenie o otwarcie metadanych w trybie odczytu/zapisu, ale spowoduje to wolniejsze wykonanie tego programu, ponieważ nie można zoptymalizować zmian wprowadzonych w metadanych, ponieważ znajdowały się one w kompilatorze.  
  
 Niektóre moduły (takie jak moduły zasobów) nie mają metadanych. W takich przypadkach zwróci `GetModuleMetaData` wartość HRESULT o wartości S_FALSE i wartość null w * `ppOut` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
