---
title: ICorProfilerFunctionControl::SetILFunctionBody — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: bebc0cf6ac7912ea3a6641e0c729b759e865dac3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864664"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a>ICorProfilerFunctionControl::SetILFunctionBody — Metoda
Zastępuje treść wspólnego języka pośredniego (CIL) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbNewILMethodHeader`  
 [in] Całkowity rozmiar nowego CIL, łącznie z nagłówkiem i wszelkimi strukturami, które pochodzą z treści.  
  
 `pbNewILMethodHeader`  
 [in] Wskaźnik do nowego nagłówka CIL.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Zamiana powiodła się.|  
  
## <a name="remarks"></a>Uwagi  
 W przeciwieństwie do metody [ICorProfilerInfo:: SetILFunctionBody —](icorprofilerinfo-setilfunctionbody-method.md) Metoda `SetILFunctionBody` zarządza pamięcią wymaganą dla nowej treści CIL. Oznacza to, że treści CIL dostarczone przez profiler nie muszą być przydzielone za pomocą interfejsu [IMethodMalloc](imethodmalloc-interface.md) ani przydzielone w ramach określonego zakresu. Może być alokowana na dowolnej stercie. Profiler może zwolnić pamięć używaną dla swojej treści CIL po powrocie `SetILFunctionBody`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerFunctionControl, interfejs](icorprofilerfunctioncontrol-interface.md)
