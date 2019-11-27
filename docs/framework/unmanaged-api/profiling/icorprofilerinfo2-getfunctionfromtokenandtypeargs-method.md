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
ms.openlocfilehash: 41021a524142afe34727584265aee578e31a64b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433207"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs — Metoda
Pobiera `FunctionID` funkcji przy użyciu określonego tokenu metadanych, zawierającego klasę i `ClassID` wartości dowolnego argumentu typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Identyfikator modułu, w którym znajduje się funkcja.  
  
 `funcDef`  
 podczas `mdMethodDef` token metadanych, który odwołuje się do funkcji.  
  
 `classId`  
 podczas Identyfikator klasy zawierającej funkcję.  
  
 `cTypeArgs`  
 podczas Liczba parametrów typu dla danej funkcji. Ta wartość musi być równa zero w przypadku funkcji innych niż ogólne.  
  
 `typeArgs`  
 podczas Tablica wartości `ClassID`, z których każdy jest argumentem funkcji. Wartość `typeArgs` może mieć wartość NULL, jeśli `cTypeArgs` jest ustawiona na zero.  
  
 `pFunctionID`  
 określoną Wskaźnik do `FunctionID` określonej funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie metody `GetFunctionFromTokenAndTypeArgs` z metadanymi `mdMethodRef` zamiast `mdMethodDef`ego tokenu metadanych może mieć nieprzewidywalne wyniki. Obiekty wywołujące powinny rozpoznać `mdMethodRef` do `mdMethodDef` podczas ich przekazywania.  
  
 Jeśli funkcja nie jest już załadowana, wywołanie `GetFunctionFromTokenAndTypeArgs` spowoduje wystąpienie załadowania, które jest niebezpieczną operacją w wielu kontekstach. Na przykład wywołanie tej metody podczas ładowania modułów lub typów może prowadzić do nieskończonej pętli, ponieważ środowisko uruchomieniowe próbuje cyklicznie ładować elementy.  
  
 Ogólnie rzecz biorąc użycie `GetFunctionFromTokenAndTypeArgs` nie jest zalecane. Jeśli zainteresują Cię zdarzenia dotyczące konkretnej funkcji, powinny one przechowywać `ModuleID` i `mdMethodDef` tej funkcji, a także używać [ICorProfilerInfo2:: GetFunctionInfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) , aby sprawdzić, czy dana `FunctionID` jest pożądaną funkcją.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
