---
title: ICorProfilerInfo::SetILFunctionBody — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: 296c3973403a5b09332efa24961d7a474d814aab
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863351"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a>ICorProfilerInfo::SetILFunctionBody — Metoda
Zastępuje treść określonej funkcji w określonym module.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 podczas Identyfikator modułu, w którym znajduje się funkcja.  
  
 `methodid`  
 podczas Token funkcji, dla której ma zostać zamieniony treść.  
  
 `pbNewILMethodHeader`  
 podczas Nowy nagłówek dla funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `SetILFunctionBody` zastępuje względny adres wirtualny funkcji w metadanych, tak aby wskazywała nową treść funkcji i dostosowuje wszystkie wewnętrzne struktury danych zgodnie z potrzebami.  
  
 Metodę `SetILFunctionBody` można wywołać tylko w funkcjach, które nigdy nie zostały skompilowane przez kompilator just-in-Time (JIT).  
  
 Użyj metody [ICorProfilerInfo:: GetILFunctionBodyAllocator —](icorprofilerinfo-getilfunctionbodyallocator-method.md) , aby przydzielić miejsce dla nowej metody w celu zapewnienia, że bufor jest zgodny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
