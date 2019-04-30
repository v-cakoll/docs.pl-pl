---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e1498ec3ce1e5258546cec8d8f8172739af6d9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756146"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs — Metoda
Pobiera `FunctionID` funkcji przy użyciu tokenu określonych metadanych, klasą, i `ClassID` wartości wszelkich argumentów typu.  
  
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
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] Identyfikator modułu, w której znajduje się funkcja.  
  
 `funcDef`  
 [in] `mdMethodDef` Token metadanych, który odwołuje się do funkcji.  
  
 `classId`  
 [in] Identyfikator klasy funkcji.  
  
 `cTypeArgs`  
 [in] Liczba parametrów typu dla danej funkcji. Ta wartość musi mieć wartość zero dla funkcji nieogólnego.  
  
 `typeArgs`  
 [in] Tablica `ClassID` wartości, z których każdy jest argumentem funkcji. Wartość `typeArgs` może mieć wartości NULL, jeśli `cTypeArgs` jest równa zero.  
  
 `pFunctionID`  
 [out] Wskaźnik do `FunctionID` określonej funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Wywoływanie `GetFunctionFromTokenAndTypeArgs` metody z `mdMethodRef` metadanych zamiast `mdMethodDef` token metadanych może przynieść nieprzewidywalne rezultaty. Obiekty wywołujące powinna być rozpoznawana `mdMethodRef` do `mdMethodDef` podczas przekazywania go.  
  
 Jeśli funkcja nie jest już załadowany, wywołanie `GetFunctionFromTokenAndTypeArgs` spowoduje, że podczas ładowania wystąpią, który jest niebezpieczne operacji w wielu kontekstach. Na przykład wywołanie tej metody podczas ładowania modułów i typów może prowadzić do wejścia w nieskończoną pętlę jako środowisko wykonawcze próby rekurencyjnie załadować rzeczy.  
  
 Ogólnie rzecz biorąc, użytkowania `GetFunctionFromTokenAndTypeArgs` jest niezalecane. Zainteresowani profilery zdarzeń związanych z konkretną funkcję, należy przechowywać `ModuleID` i `mdMethodDef` tej funkcji oraz [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) Aby sprawdzić, czy dany `FunctionID` jest w przypadku odpowiednią funkcję.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
