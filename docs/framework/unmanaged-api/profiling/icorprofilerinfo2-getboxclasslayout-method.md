---
title: ICorProfilerInfo2::GetBoxClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
ms.openlocfilehash: 500cf74c320438fc1b78f0aac737b418716e1a11
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862831"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a>ICorProfilerInfo2::GetBoxClassLayout — Metoda
Pobiera informacje o miejscu, w którym znajduje się określony typ wartości, gdy jest on opakowany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 podczas Identyfikator klasy opisującej typ wartości, która jest opakowana.  
  
 `pBufferOffset`  
 określoną Liczba całkowita, która jest przesunięciem względem wskaźnika identyfikatora obiektu zapakowanego typu wartości.  
  
## <a name="remarks"></a>Uwagi  
 Wartość `pBufferOffset` jest lokalizacją typu wartości w polu. Po zastosowaniu `pBufferOffset` do obiektu opakowanego układ klasy typu wartości może służyć do interpretowania wartości obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
