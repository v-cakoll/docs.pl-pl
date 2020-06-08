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
ms.openlocfilehash: f5438ddc655f0f6a7c11d978a47b1bf9e2a13059
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497013"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 — Metoda
Pobiera klasę nadrzędną, token metadanych i `ClassID` dla każdego argumentu typu, jeśli istnieje, funkcji.  
  
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
 podczas `COR_PRF_FRAME_INFO`Wartość, która wskazuje na informacje o klatce stosu.  
  
 `pClassId`  
 określoną Wskaźnik do klasy nadrzędnej funkcji.  
  
 `pModuleId`  
 określoną Wskaźnik do modułu, w którym zdefiniowana jest Klasa nadrzędna funkcji.  
  
 `pToken`  
 określoną Wskaźnik do tokenu metadanych dla funkcji.  
  
 `cTypeArgs`  
 podczas Rozmiar `typeArgs` tablicy.  
  
 `pcTypeArgs`  
 określoną Wskaźnik do łącznej liczby `ClassID` wartości.  
  
 `typeArgs`  
 określoną Tablica `ClassID` wartości, z których każdy jest identyfikatorem argumentu typu funkcji. Gdy metoda zwraca, `typeArgs` będzie zawierać niektóre lub wszystkie `ClassID` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Kod profilera może wywołać [ICorProfilerInfo:: GetModuleMetaData —](icorprofilerinfo-getmodulemetadata-method.md) w celu uzyskania interfejsu [metadanych](../metadata/index.md) dla danego modułu. Token metadanych, który jest zwracany do lokalizacji, do której się odwołuje się, `pToken` może następnie zostać użyty w celu uzyskania dostępu do metadanych dla funkcji.  
  
 Identyfikator klasy i argumenty typu, które są zwracane przez `pClassId` Parametry i są `typeArgs` zależne od wartości przekazanej w `frameInfo` parametrze, jak pokazano w poniższej tabeli.  
  
|Wartość `frameInfo` parametru|Wynik|  
|----------------------------------------|------------|  
|`COR_PRF_FRAME_INFO`Wartość uzyskana z `FunctionEnter2` wywołania zwrotnego|`ClassID`, Zwrócone w lokalizacji, do której odwołuje się `pClassId` , i wszystkie argumenty typu zwrócone w `typeArgs` tablicy, będą dokładne.|  
|`COR_PRF_FRAME_INFO`Który został uzyskany ze źródła innego niż `FunctionEnter2` wywołanie zwrotne|Nie można `ClassID` określić argumentów dokładnie i typu. Oznacza to, że `ClassID` może mieć wartość null, a niektóre argumenty typu mogą wrócić jako <xref:System.Object> .|  
|Zero|Nie można `ClassID` określić argumentów dokładnie i typu. Oznacza to, że `ClassID` może mieć wartość null, a niektóre argumenty typu mogą wrócić jako <xref:System.Object> .|  
  
 Po `GetFunctionInfo2` powrocie należy sprawdzić, czy `typeArgs` bufor jest wystarczająco duży, aby można było zawierać wszystkie `ClassID` wartości. W tym celu należy porównać wartość wskazującą wartość `pcTypeArgs` `cTypeArgs` parametru. Jeśli `pcTypeArgs` wskazuje wartość, która jest większa niż `cTypeArgs` podzielona przez rozmiar `ClassID` wartości, Przydziel większy `pcTypeArgs` bufor, Aktualizuj `cTypeArgs` o nowy, większy rozmiar i ponownie wywołaj `GetFunctionInfo2` .  
  
 Alternatywnie, można najpierw wywołać `GetFunctionInfo2` z buforem o zerowej długości, `pcTypeArgs` Aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwracaną w `pcTypeArgs` podzieleniu przez rozmiar `ClassID` wartości i `GetFunctionInfo2` ponownie wywołać.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
