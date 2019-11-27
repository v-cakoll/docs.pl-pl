---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
ms.openlocfilehash: 5b6c0159b432d2a70f583357bbcf714b27399633
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447172"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs — Metoda
Pobiera `ClassID` typu przy użyciu określonego tokenu metadanych i wartości `ClassID` dowolnego argumentu typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 podczas Identyfikator modułu, w którym znajduje się typ.  
  
 `typeDef`  
 podczas `mdTypeDef` token metadanych, który odwołuje się do typu.  
  
 `cTypeArgs`  
 podczas Liczba parametrów typu dla danego typu. Ta wartość musi być równa zero dla typów innych niż ogólne.  
  
 `typeArgs`  
 podczas Tablica wartości `ClassID`, z których każdy jest argumentem typu. Wartość `typeArgs` może mieć wartość NULL, jeśli `cTypeArgs` jest ustawiona na zero.  
  
 `pClassID`  
 określoną Wskaźnik do `ClassID` określonego typu.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie metody `GetClassFromTokenAndTypeArgs` z `mdTypeRef` zamiast tokenu metadanych `mdTypeDef` może mieć nieprzewidywalne wyniki; obiekty wywołujące powinny rozpoznać `mdTypeRef` do `mdTypeDef` podczas ich przekazywania.  
  
 Jeśli typ nie jest już załadowany, wywołanie `GetClassFromTokenAndTypeArgs` wywoła ładowanie, które jest niebezpieczną operacją w wielu kontekstach. Na przykład wywołanie tej metody podczas ładowania modułów lub innych typów może prowadzić do nieskończonej pętli, ponieważ środowisko uruchomieniowe próbuje cyklicznie ładować elementy.  
  
 Ogólnie rzecz biorąc użycie `GetClassFromTokenAndTypeArgs` nie jest zalecane. Jeśli zainteresują Cię zdarzenia dotyczące określonego typu, powinny one przechowywać `ModuleID` i `mdTypeDef` tego typu, a następnie użyć [ICorProfilerInfo2:: GetClassIDInfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) , aby sprawdzić, czy dany `ClassID` jest tym żądanym typem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
