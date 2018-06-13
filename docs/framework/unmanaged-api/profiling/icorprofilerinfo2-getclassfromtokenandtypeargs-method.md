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
ms.openlocfilehash: 04be252092732296354cfec102cf8fe648ed2dd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456641"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs — Metoda
Pobiera `ClassID` typu przy użyciu tokenu określonych metadanych i `ClassID` wartości dowolnego argumentów typu.  
  
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
 [in] Liczba parametrów typu dla danego typu. Ta wartość musi być zero dla typu nieogólnego.  
  
 `typeArgs`  
 [in] Tablica `ClassID` wartości, z których każdy jest argumentem typu. Wartość `typeArgs` może mieć wartości NULL, jeśli `cTypeArgs` jest ustawiony na zero.  
  
 `pClassID`  
 [out] Wskaźnik do `ClassID` określonego typu.  
  
## <a name="remarks"></a>Uwagi  
 Wywoływanie `GetClassFromTokenAndTypeArgs` metody z `mdTypeRef` zamiast `mdTypeDef` token metadanych może mieć nieprzewidziane skutki; powinna być rozpoznawana przez obiekty wywołujące `mdTypeRef` do `mdTypeDef` podczas przekazywania go.  
  
 Jeśli typ nie jest już załadowany, wywoływania `GetClassFromTokenAndTypeArgs` wyzwoli ładowania, który jest niebezpieczne operacji w wielu sytuacjach. Na przykład wywołaniem tej metody w czasie ładowania modułów lub innych typów może spowodować nieskończoną pętlę jako środowisko uruchomieniowe próbuje załadować rekurencyjnie rzeczy.  
  
 Ogólnie rzecz biorąc, użycie `GetClassFromTokenAndTypeArgs` jest niezalecane. Zainteresowani profilery zdarzenia dla określonego typu, należy przechowywać `ModuleID` i `mdTypeDef` typu i użyj [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) Aby sprawdzić, czy danego `ClassID` jest odpowiedniego typu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
