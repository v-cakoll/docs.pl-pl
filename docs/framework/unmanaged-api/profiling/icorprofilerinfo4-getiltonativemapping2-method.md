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
ms.openlocfilehash: b625b2962c829e7c0692a61d8f5561818f7ebf1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086692"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>ICorProfilerInfo4::GetILToNativeMapping2 — Metoda
Pobiera mapę od firmy Microsoft intermediate language (MSIL) przesuwa się do macierzystych przesunięciach kod zawarty w wersji ponownie skompilowana JIT określonej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Identyfikator funkcji, która zawiera kod.  
  
 `pReJitId`  
 [in] Tożsamość funkcja ponownie skompilowana JIT. Tożsamość musi mieć wartość zero w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 `cMap`  
 [in] Maksymalny rozmiar `map` tablicy.  
  
 `pcMap`  
 [out] Całkowita liczba dostępnych struktur cor_debug_il_to_native_map —.  
  
 `map`  
 [out] Tablica `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z których każdy określa przesunięcia. Po `GetILToNativeMapping2` metoda zwraca `map` będzie zawierać części lub całości `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.  
  
## <a name="remarks"></a>Uwagi  
 `GetILToNativeMapping2` jest podobny do [icorprofilerinfo::getiltonativemapping —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metody, z tą różnicą, że profiler określić identyfikator funkcji ponownej kompilacji w przyszłości umożliwi wydania.  
  
> [!NOTE]
>  [Icorprofilerfunctioncontrol::setilinstrumentedcodemap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) metoda nie jest zaimplementowana w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], dlatego funkcje, które zostały ponownie skompilowana JIT nie mogą mieć mapowania IL do macierzystego, który różni się od pierwotnie Funkcja skompilowany. W efekcie `GetILToNativeMapping2` nelze volat wartość różną od zera Identyfikatora ponownie skompilowana JIT w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 `GetILToNativeMapping2` Metoda zwraca tablicę `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. W celu przekazania, czy określone zakresy natywne instrukcje odpowiadają specjalne regiony kodu (na przykład prologu), mogą mieć wpisu w tablicy jej `ilOffset` pole jest ustawione na wartość [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) wyliczenie.  
  
 Po `GetILToNativeMapping2` zwróci wartość, należy sprawdzić, czy `map` bufor jest wystarczająco duży, aby zawierała wszystkich `COR_DEBUG_IL_TO_NATIVE_MAP` struktury. Aby to zrobić, porównanie wartości `cMap` z wartością `pcMap` parametru. Jeśli `pcMap` wartości, gdy jest mnożony przez rozmiar `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, jest większy niż `cMap`, Przydziel większego `map` buforu, zaktualizuj `cMap` przy użyciu nowych, większy rozmiar i Wywołaj `GetILToNativeMapping2` ponownie.  
  
 Alternatywnie, można wywołać `GetILToNativeMapping2` o zerowej długości `map` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcMap` i wywołać `GetILToNativeMapping2` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetILToNativeMapping, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
