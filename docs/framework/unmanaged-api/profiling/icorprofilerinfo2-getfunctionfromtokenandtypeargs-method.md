---
title: "ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b225b87eab6e65055618c8b6659459637e8a01be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs — Metoda
Pobiera `FunctionID` funkcji przy użyciu tokenu określonych metadanych, klasą, i `ClassID` wartości dowolnego argumentów typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] Identyfikator modułu, w której znajduje się funkcja.  
  
 `funcDef`  
 [in] `mdMethodDef` Token metadanych, który odwołuje się do funkcji.  
  
 `classId`  
 [in] Identyfikator klasy zawierające funkcji.  
  
 `cTypeArgs`  
 [in] Liczba parametrów typu dla danej funkcji. Ta wartość musi wynosić zero dla funkcji nieogólnego.  
  
 `typeArgs`  
 [in] Tablica `ClassID` wartości, z których każdy jest argumentu funkcji. Wartość `typeArgs` może mieć wartości NULL, jeśli `cTypeArgs` jest ustawiony na zero.  
  
 `pFunctionID`  
 [out] Wskaźnik do `FunctionID` określonych funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Wywoływanie `GetFunctionFromTokenAndTypeArgs` metody z `mdMethodRef` metadanych zamiast `mdMethodDef` token metadanych może mieć nieprzewidywalne skutki. Powinna być rozpoznawana przez obiekty wywołujące `mdMethodRef` do `mdMethodDef` podczas przekazywania go.  
  
 Jeśli funkcja nie jest już załadowany, wywoływania `GetFunctionFromTokenAndTypeArgs` spowoduje, że ładowanie było, który jest niebezpieczne operacji w wielu sytuacjach. Na przykład wywołaniem tej metody w czasie ładowania modułów lub typów może spowodować nieskończoną pętlę jako środowisko uruchomieniowe próbuje załadować rekurencyjnie rzeczy.  
  
 Ogólnie rzecz biorąc, użycie `GetFunctionFromTokenAndTypeArgs` jest niezalecane. Zainteresowani profilery zdarzeń dla danej funkcji, należy przechowywać `ModuleID` i `mdMethodDef` tej funkcji i użyj [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) Aby sprawdzić, czy danego `FunctionID` jest z odpowiednią funkcję.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
