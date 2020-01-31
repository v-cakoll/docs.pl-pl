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
ms.openlocfilehash: 4fccee3b94efd65312206afb22c87f30609f9e6b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868463"
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
 podczas Maksymalny rozmiar tablicy `map`.  
  
 `pcMap`  
 określoną Łączna liczba dostępnych struktur COR_DEBUG_IL_TO_NATIVE_MAP.  
  
 `map`  
 określoną Tablica struktur `COR_DEBUG_IL_TO_NATIVE_MAP`, z których każdy określa przesunięcia. Po powrocie metody `GetILToNativeMapping2`, `map` będzie zawierać niektóre lub wszystkie struktury `COR_DEBUG_IL_TO_NATIVE_MAP`.  
  
## <a name="remarks"></a>Uwagi  
 `GetILToNativeMapping2` przypomina metodę [ICorProfilerInfo:: GetILToNativeMapping —](icorprofilerinfo-getiltonativemapping-method.md) , z tą różnicą, że umożliwia profilerowi określenie identyfikatora ponownie skompilowanej funkcji w przyszłych wydaniach.  
  
> [!NOTE]
> Metoda [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap —](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) nie jest zaimplementowana w .NET Framework 4,5, dlatego funkcje, które zostały ponownie skompilowane w trybie JIT, nie mogą mieć mapowania Il-to-natywnego, które różni się od pierwotnie skompilowanej funkcji. W związku z tym `GetILToNativeMapping2` nie można wywołać z niezerowym IDENTYFIKATORem ponownej kompilacji JIT w .NET Framework 4,5.  
  
 Metoda `GetILToNativeMapping2` zwraca tablicę struktur `COR_DEBUG_IL_TO_NATIVE_MAP`. Aby przekazać, że niektóre zakresy natywnych instrukcji odpowiadają specjalnym regionom kodu (na przykład prologu), wpis w tablicy może mieć `ilOffset` pole ustawione na wartość wyliczenia [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Po powrocie `GetILToNativeMapping2` należy sprawdzić, czy bufor `map` był wystarczająco duży, aby zawierał wszystkie struktury `COR_DEBUG_IL_TO_NATIVE_MAP`. W tym celu należy porównać wartość `cMap` z wartością parametru `pcMap`. Jeśli wartość `pcMap`, gdy zostanie pomnożona przez rozmiar struktury `COR_DEBUG_IL_TO_NATIVE_MAP`, jest większa niż `cMap`, Przydziel większy bufor `map`, zaktualizuj `cMap` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetILToNativeMapping2`.  
  
 Alternatywnie można najpierw wywołać `GetILToNativeMapping2` z buforem `map` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwróconą w `pcMap` i ponownie wywołać `GetILToNativeMapping2`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetILToNativeMapping, metoda](icorprofilerinfo-getiltonativemapping-method.md)
- [ICorProfilerInfo4, interfejs](icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
