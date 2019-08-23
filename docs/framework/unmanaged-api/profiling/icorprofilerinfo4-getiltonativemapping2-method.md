---
title: ICorProfilerInfo4::GetILToNativeMapping2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8ffdb04bdf3fd2f605e2dffc5065a0d786bbaf7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967917"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2 — Metoda
Pobiera mapę z przesunięcia języka pośredniego firmy Microsoft (MSIL) do natywnych przesunięć dla kodu zawartego w ponownej kompilacji JIT w wersji określonej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas Identyfikator funkcji, która zawiera kod.  
  
 `pReJitId`  
 podczas Tożsamość funkcji ponownie skompilowanej JIT. Tożsamość musi być równa zero w .NET Framework 4,5.  
  
 `cMap`  
 podczas Maksymalny rozmiar `map` tablicy.  
  
 `pcMap`  
 określoną Łączna liczba dostępnych struktur COR_DEBUG_IL_TO_NATIVE_MAP.  
  
 `map`  
 określoną Tablica `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z których każdy określa przesunięcia. Po powrocie `GetILToNativeMapping2` metody `COR_DEBUG_IL_TO_NATIVE_MAP` będzie zawierać niektóre `map` lub wszystkie struktury.  
  
## <a name="remarks"></a>Uwagi  
 `GetILToNativeMapping2`jest podobna do metody [ICorProfilerInfo:: GetILToNativeMapping —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) , z tą różnicą, że umożliwia profilerowi określenie identyfikatora ponownie skompilowanej funkcji w przyszłych wydaniach.  
  
> [!NOTE]
> Metoda [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) nie jest zaimplementowana w .NET Framework 4,5, dlatego funkcje, które zostały ponownie skompilowane w trybie JIT, nie mogą mieć mapowania Il-to-natywnego, które różni się od pierwotnie skompilowanej funkcji. W związku z `GetILToNativeMapping2` tym nie można wywołać z niezerowym identyfikatorem ponownej kompilacji JIT w .NET Framework 4,5.  
  
 Metoda zwraca tablicę `COR_DEBUG_IL_TO_NATIVE_MAP`struktur. `GetILToNativeMapping2` Aby przekazać, że niektóre zakresy natywnych instrukcji odpowiadają specjalnym regionom kodu (na przykład prologu), wpis w tablicy może mieć `ilOffset` ustawione pole jako wartość wyliczenia [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Po `GetILToNativeMapping2` powrocie należy sprawdzić `map` , czy bufor jest `COR_DEBUG_IL_TO_NATIVE_MAP` wystarczająco duży, aby można było zawierać wszystkie struktury. W tym celu należy porównać wartość `cMap` z wartością `pcMap` parametru. `cMap` `COR_DEBUG_IL_TO_NATIVE_MAP` `GetILToNativeMapping2` `map` `cMap`Jeśli wartość, gdy zostanie pomnożona przez rozmiar struktury, jest większa niż, Przydziel większy bufor, Aktualizuj o nowy, większy rozmiar i ponownie wywołaj. `pcMap`  
  
 Alternatywnie, można najpierw wywołać `GetILToNativeMapping2` z buforem o zerowej długości `map` , aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwracaną w `pcMap` i ponownie wywołać. `GetILToNativeMapping2`  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetILToNativeMapping, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
