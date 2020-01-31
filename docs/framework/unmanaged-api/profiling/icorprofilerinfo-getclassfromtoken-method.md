---
title: ICorProfilerInfo::GetClassFromToken — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
ms.openlocfilehash: 841953625235406f013e9f140ad91c7b65680e47
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863956"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a>ICorProfilerInfo::GetClassFromToken — Metoda
Pobiera identyfikator klasy, z uwzględnieniem tokenu metadanych. Ta metoda jest przestarzała w .NET Framework w wersji 2,0. Zamiast tego użyj [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs —](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 podczas Identyfikator modułu, który zawiera klasę.  
  
 `typeDef`  
 podczas `mdTypeDef` token metadanych, który odwołuje się do klasy.  
  
 `cTypeArgs`  
 określoną Wskaźnik do identyfikatora klasy.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest przestarzała; Zamiast tego należy używać `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` dla wszystkich typów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 1,0, 1,1  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
