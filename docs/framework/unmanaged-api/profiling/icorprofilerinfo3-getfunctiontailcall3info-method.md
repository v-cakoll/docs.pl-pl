---
title: ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: 5346792cb2a1309268cb4ba48625aa559777fbaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176997"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda
Udostępnia ramkę stosu funkcji, która jest zgłaszana do profilera przez [functiontailcall3WithInfo](functiontailcall3withinfo-function.md) funkcji. Tę metodę można wywołać `FunctionTailcall3WithInfo` tylko podczas wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [w] Funkcja, `FunctionID` która powraca.  
  
 `eltInfo`  
 [w] Nieprzezroczysty uchwyt, który reprezentuje informacje o danej ramce stosu. Profiler powinien zapewnić `eltInfo` taki sam, który został `FunctionTailcall3WithInfo` podany do profilera przez funkcję.  
  
 `pFrameInfo`  
 [na zewnątrz] Nieprzezroczysty dojście reprezentujące ogólne informacje o danej ramce stosu. Ten dojście jest `FunctionTailcall3WithInfo` prawidłowy tylko podczas wywołania zwrotnego, w którym profiler o nazwie `GetFunctionTailcall3Info` metody.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Functionenter3withinfo](functionenter3withinfo-function.md)
- [Functionleave3withinfo](functionleave3withinfo-function.md)
- [FunkcjaTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowania](index.md)
