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
ms.openlocfilehash: e0663ff122397ba639a0a219e513be2f3f0cbbef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862793"
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
  
 Ogólnie rzecz biorąc użycie `GetClassFromTokenAndTypeArgs` nie jest zalecane. Jeśli zainteresują Cię zdarzenia dotyczące określonego typu, powinny one przechowywać `ModuleID` i `mdTypeDef` tego typu, a następnie użyć [ICorProfilerInfo2:: GetClassIDInfo2 —](icorprofilerinfo2-getclassidinfo2-method.md) , aby sprawdzić, czy dany `ClassID` jest tym żądanym typem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
