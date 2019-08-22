---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 9e8e4c7e6c367970100c98dc3dc8237b25f99221
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665602"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9:: GetILToNativeMapping3, Metoda

Przy podanym adresie początkowym kodu natywnego program zwraca informacje mapowania natywnego do IL dla tej trybie JIT wersji kodu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

#### <a name="parameters"></a>Parametry

`pNativeCodeStartAddress` \
podczas Wskaźnik do początku funkcji natywnej.

`cMap` \
podczas Maksymalny rozmiar `map` tablicy.

`pcMap` \
określoną Łączna liczba dostępnych struktur COR_DEBUG_IL_TO_NATIVE_MAP.

`map` \
określoną Tablica struktur [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , z których każdy określa przesunięcia. Po powrocie `GetILToNativeMapping3` metody `COR_DEBUG_IL_TO_NATIVE_MAP` będzie zawierać niektóre `map` lub wszystkie struktury.

## <a name="remarks"></a>Uwagi

Gdy kompilacja warstwowa jest włączona, Metoda może mieć więcej niż jedną treść kodu natywnego. [ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) zwróci adresy startowe dla wszystkich natywnych treści kodu.

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**Nagłówki** CorProf. idl, CorProf. h

**Biblioteki** CorGuids.lib

**.NET Framework wersje:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo9, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
