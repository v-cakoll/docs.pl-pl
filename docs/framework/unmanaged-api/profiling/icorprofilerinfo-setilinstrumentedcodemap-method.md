---
title: ICorProfilerInfo::SetILInstrumentedCodeMap — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: 99e473268fd0d5bb8ce120b97576277949b86508
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869000"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap — Metoda

Ustawia mapę kodu dla określonej funkcji przy użyciu określonych wpisów mapy języka pośredniego (MSIL) firmy Microsoft.

> [!NOTE]
> W .NET Framework w wersji 2,0 wywoływanie `SetILInstrumentedCodeMap` na `FunctionID`, który reprezentuje funkcję generyczną w określonej domenie aplikacji, wpłynie na wszystkie wystąpienia tej funkcji w domenie aplikacji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>Parametry

`functionId`\
podczas Identyfikator funkcji, dla której ma zostać ustawiona Mapa kodu.

`fStartJit`\
podczas Wartość logiczna wskazująca, czy wywołanie metody `SetILInstrumentedCodeMap` jest pierwszym elementem dla konkretnego `FunctionID`. Ustaw `fStartJit` na `true` w pierwszym wywołaniu `SetILInstrumentedCodeMap` dla danego `FunctionID`i `false`.

`cILMapEntries`\
podczas Liczba elementów w tablicy `cILMapEntries`.

`rgILMapEntries`\
podczas Tablica struktur COR_IL_MAP, z których każdy Określa przesunięcie MSIL.

## <a name="remarks"></a>Uwagi

Profiler często wstawia instrukcje w kodzie źródłowym metody w celu instrumentowania tej metody (na przykład w celu powiadomienia po osiągnięciu podanych linii źródłowej). `SetILInstrumentedCodeMap` umożliwia programowi Profiler zamapowanie oryginalnych instrukcji MSIL na nowe lokalizacje. Profiler może użyć metody [ICorProfilerInfo:: GetILToNativeMapping —](icorprofilerinfo-getiltonativemapping-method.md) , aby uzyskać początkowe przesunięcie MSIL dla danego przesunięcia natywnego.

Debuger przyjmie, że każde Stare przesunięcie odwołuje się do przesunięcia MSIL w oryginalnym, niezmodyfikowanym kodzie MSIL i że każde nowe przesunięcie odwołuje się do przesunięcia MSIL w nowym, przyrządowym kodzie. Mapa powinna być posortowana w kolejności rosnącej. Aby krok po kroku działał prawidłowo, postępuj zgodnie z następującymi wskazówkami:

- Nie zmieniaj kolejności kodu MSIL z instrumentacją.

- Nie usuwaj oryginalnego kodu MSIL.

- Dołącz wpisy dla wszystkich punktów sekwencji z pliku bazy danych programu (PDB) na mapie. Mapa nie wykonuje interpolacji brakujących wpisów. Dlatego, uwzględniając następujące mapowanie:

  (0 stara, 0 New)

  (5 starych, 10 nowych)

  (9 starych, 20 nowych)

  - Stare przesunięcie 0, 1, 2, 3 lub 4 zostanie zmapowane na nowe przesunięcie 0.

  - Stare przesunięcie o wartości 5, 6, 7 lub 8 zostanie zmapowane na nowe przesunięcie 10.

  - Stare przesunięcie w wysokości 9 lub wyższej zostanie zmapowane do nowego przesunięcia 20.

  - Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostanie zmapowane do starego przesunięcia 0.

  - Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie zmapowane do starego przesunięcia 5.

  - Nowe przesunięcie o wartości 20 lub wyższej zostanie zmapowane do starego przesunięcia 9.

W .NET Framework 3,5 i poprzednich wersjach przypisujesz tablicę `rgILMapEntries`, wywołując metodę [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) . Ponieważ środowisko uruchomieniowe przejmuje własność tej pamięci, profiler nie powinien próbować go zwolnić.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorProf. idl, CorProf. h

**Biblioteka:** CorGuids. lib

**Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
