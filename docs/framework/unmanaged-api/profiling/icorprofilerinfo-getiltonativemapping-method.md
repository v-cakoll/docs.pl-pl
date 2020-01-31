---
title: ICorProfilerInfo::GetILToNativeMapping — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
ms.openlocfilehash: f9abb3ae9cd3f9c70485e584399a6ed32b32a572
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870636"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a>ICorProfilerInfo::GetILToNativeMapping — Metoda
Pobiera mapę z przesunięcia języka pośredniego firmy Microsoft (MSIL) do natywnych przesunięć dla kodu zawartego w określonej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas Identyfikator funkcji, która zawiera kod.  
  
 `cMap`  
 podczas Maksymalny rozmiar tablicy `map`.  
  
 `pcMap`  
 określoną Łączna liczba dostępnych struktur COR_DEBUG_IL_TO_NATIVE_MAP.  
  
 `map`  
 określoną Tablica struktur `COR_DEBUG_IL_TO_NATIVE_MAP`, z których każdy określa przesunięcia. Po powrocie metody `GetILToNativeMapping`, `map` będzie zawierać niektóre lub wszystkie struktury `COR_DEBUG_IL_TO_NATIVE_MAP`.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetILToNativeMapping` zwraca tablicę struktur `COR_DEBUG_IL_TO_NATIVE_MAP`. Aby przekazać, że niektóre zakresy natywnych instrukcji odpowiadają specjalnym regionom kodu (na przykład prologu), wpis w tablicy może mieć `ilOffset` pole ustawione na wartość wyliczenia [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Po powrocie `GetILToNativeMapping` należy sprawdzić, czy bufor `map` był wystarczająco duży, aby zawierał wszystkie struktury `COR_DEBUG_IL_TO_NATIVE_MAP`. W tym celu należy porównać wartość `cMap` z wartością parametru `pcMap`. Jeśli wartość `pcMap`, gdy zostanie pomnożona przez rozmiar struktury `COR_DEBUG_IL_TO_NATIVE_MAP`, jest większa niż `cMap`, Przydziel większy bufor `map`, zaktualizuj `cMap` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetILToNativeMapping`.  
  
 Alternatywnie można najpierw wywołać `GetILToNativeMapping` z buforem `map` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwróconą w `pcMap` i ponownie wywołać `GetILToNativeMapping`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [GetILToNativeMapping2, metoda](icorprofilerinfo4-getiltonativemapping2-method.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
