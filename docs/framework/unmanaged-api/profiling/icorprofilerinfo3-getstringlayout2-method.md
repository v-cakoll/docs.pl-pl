---
title: ICorProfilerInfo3::GetStringLayout2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: f3727343755d7014202f844be28414d31ce55bc1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862259"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a>ICorProfilerInfo3::GetStringLayout2 — Metoda
Pobiera informacje o układzie obiektu ciągu. Ta metoda zastępuje metodę [ICorProfilerInfo2:: GetStringLayout —](icorprofilerinfo2-getstringlayout-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStringLengthOffset`  
 określoną Wskaźnik do przesunięcia lokalizacji względem wskaźnika `ObjectID`, w którym jest przechowywana długość ciągu. Długość jest przechowywana jako `DWORD`.  
  
 `pBufferOffset`  
 określoną Wskaźnik do przesunięcia buforu względem wskaźnika `ObjectID`, w którym jest przechowywany ciąg znaków dwubajtowych.  
  
## <a name="remarks"></a>Uwagi  
 Ciągi mogą lub nie mogą być zakończone znakiem null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
