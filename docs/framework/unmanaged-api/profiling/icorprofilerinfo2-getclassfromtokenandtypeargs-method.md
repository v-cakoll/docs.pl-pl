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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0651609e6d2597336ee42ceae752df7e561cd252
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692655"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs — Metoda
Pobiera `ClassID` typu przy użyciu tokenu określonych metadanych i `ClassID` wartości wszelkich argumentów typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] Identyfikator modułu, w której znajduje się typu.  
  
 `typeDef`  
 [in] `mdTypeDef` Token metadanych, który odwołuje się do typu.  
  
 `cTypeArgs`  
 [in] Liczba parametrów typu dla danego typu. Ta wartość musi mieć wartość zero dla typu nieogólnego.  
  
 `typeArgs`  
 [in] Tablica `ClassID` wartości, z których każdy jest argumentem typu. Wartość `typeArgs` może mieć wartości NULL, jeśli `cTypeArgs` jest równa zero.  
  
 `pClassID`  
 [out] Wskaźnik do `ClassID` określonego typu.  
  
## <a name="remarks"></a>Uwagi  
 Wywoływanie `GetClassFromTokenAndTypeArgs` metody z `mdTypeRef` zamiast `mdTypeDef` token metadanych może przynieść nieprzewidywalne rezultaty; obiekty wywołujące powinna być rozpoznawana `mdTypeRef` do `mdTypeDef` podczas przekazywania go.  
  
 Jeśli typ nie jest już załadowany, wywołanie `GetClassFromTokenAndTypeArgs` wyzwoli załadunku, które jest operacją niebezpiecznych w wielu kontekstach. Na przykład wywołanie tej metody w czasie ładowania modułów lub innych typów może prowadzić do wejścia w nieskończoną pętlę jako środowisko wykonawcze próby rekurencyjnie załadować rzeczy.  
  
 Ogólnie rzecz biorąc, użytkowania `GetClassFromTokenAndTypeArgs` jest niezalecane. Zainteresowani profilery zdarzeń dla określonego typu, należy przechowywać `ModuleID` i `mdTypeDef` tego typu i użyj [icorprofilerinfo2::getclassidinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) Aby sprawdzić, czy dany `ClassID` jest żądany typ.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
