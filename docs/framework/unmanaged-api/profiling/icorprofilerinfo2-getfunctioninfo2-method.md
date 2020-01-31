---
title: ICorProfilerInfo2::GetFunctionInfo2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
ms.openlocfilehash: dcd162aec12dc75585f1828cffdd4cdbedcf9988
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868665"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 — Metoda
Pobiera klasę nadrzędną, token metadanych i `ClassID` każdego argumentu typu, jeśli istnieje, funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 podczas Identyfikator funkcji, dla której ma zostać pobrana Klasa nadrzędna i inne informacje.  
  
 `frameInfo`  
 podczas Wartość `COR_PRF_FRAME_INFO`, która wskazuje na informacje o ramce stosu.  
  
 `pClassId`  
 określoną Wskaźnik do klasy nadrzędnej funkcji.  
  
 `pModuleId`  
 określoną Wskaźnik do modułu, w którym zdefiniowana jest Klasa nadrzędna funkcji.  
  
 `pToken`  
 określoną Wskaźnik do tokenu metadanych dla funkcji.  
  
 `cTypeArgs`  
 podczas Rozmiar tablicy `typeArgs`.  
  
 `pcTypeArgs`  
 określoną Wskaźnik do łącznej liczby wartości `ClassID`.  
  
 `typeArgs`  
 określoną Tablica wartości `ClassID`, z których każdy jest IDENTYFIKATORem argumentu typu funkcji. Gdy metoda zwraca, `typeArgs` będzie zawierać niektóre lub wszystkie wartości `ClassID`.  
  
## <a name="remarks"></a>Uwagi  
 Kod profilera może wywołać [ICorProfilerInfo:: GetModuleMetaData —](icorprofilerinfo-getmodulemetadata-method.md) w celu uzyskania interfejsu [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) dla danego modułu. Token metadanych, który jest zwracany do lokalizacji, do której odwołuje się `pToken`, może następnie zostać użyty w celu uzyskania dostępu do metadanych dla funkcji.  
  
 Identyfikatory klasy i argumenty typu, które są zwracane przez parametry `pClassId` i `typeArgs`, zależą od wartości przekazanej w parametrze `frameInfo`, jak pokazano w poniższej tabeli.  
  
|Wartość parametru `frameInfo`|Wynik|  
|----------------------------------------|------------|  
|Wartość `COR_PRF_FRAME_INFO` uzyskana z wywołania zwrotnego `FunctionEnter2`|`ClassID`, zwrócona w lokalizacji, do której odwołuje się `pClassId`, a wszystkie argumenty typu zwrócone w tablicy `typeArgs`, będą dokładne.|  
|`COR_PRF_FRAME_INFO` uzyskany ze źródła innego niż `FunctionEnter2` wywołanie zwrotne|Nie można określić dokładnej `ClassID` i argumentów typu. Oznacza to, że `ClassID` może mieć wartość null, a niektóre argumenty typu mogą wrócić jako <xref:System.Object>.|  
|Zero|Nie można określić dokładnej `ClassID` i argumentów typu. Oznacza to, że `ClassID` może mieć wartość null, a niektóre argumenty typu mogą wrócić jako <xref:System.Object>.|  
  
 Po powrocie `GetFunctionInfo2` należy sprawdzić, czy bufor `typeArgs` był wystarczająco duży, aby zawierał wszystkie wartości `ClassID`. W tym celu należy porównać wartość, która `pcTypeArgs` wskazuje na wartość parametru `cTypeArgs`. Jeśli `pcTypeArgs` wskazuje wartość, która jest większa niż `cTypeArgs` podzielona przez rozmiar `ClassID` wartości, Przydziel większy bufor `pcTypeArgs`, zaktualizuj `cTypeArgs` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetFunctionInfo2`.  
  
 Alternatywnie można najpierw wywołać `GetFunctionInfo2` z buforem `pcTypeArgs` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwróconą przez `pcTypeArgs` podzieloną przez rozmiar `ClassID` wartości i ponownie wywołać `GetFunctionInfo2`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
