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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a574a04e5746a8b2c9c32160e82aa503b392729
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154196"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap — Metoda
Ustawia mapę kodu dla określonej funkcji przy użyciu określonego wpisy mapy intermediate language (MSIL) firmy Microsoft.  
  
> [!NOTE]
>  W .NET Framework w wersji 2.0, wywołanie `SetILInstrumentedCodeMap` na `FunctionID` czy reprezentuje ogólnej funkcji w domenie określonej aplikacji będzie miało wpływ na wszystkie wystąpienia tej funkcji w domenie aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, dla którego ma zostać ustawiony na mapie kodu.  
  
 `fStartJit`  
 [in] Wartość logiczna, która wskazuje, czy wywołanie `SetILInstrumentedCodeMap` metody jest to pierwszy określonego `FunctionID`. Ustaw `fStartJit` do `true` w pierwszym wywołaniu `SetILInstrumentedCodeMap` dla danego `FunctionID`, a `false` po tej dacie.  
  
 `cILMapEntries`  
 [in] Liczba elementów w `cILMapEntries` tablicy.  
  
 `rgILMapEntries`  
 [in] Tablica cor_il_map — struktur, z których każdy określa przesunięcie MSIL.  
  
## <a name="remarks"></a>Uwagi  
 Program profilujący często wstawia instrukcji w kodzie źródłowym metodę w celu Instrumentacja tej metody (na przykład do wysyłania powiadomień o osiągnięciu linię danego źródła). `SetILInstrumentedCodeMap` Umożliwia programowi profilującemu mapowania oryginalny instrukcji MSIL ich nowych lokalizacji. Program profilujący może używać [icorprofilerinfo::getiltonativemapping —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metodę, aby uzyskać oryginalnego przesunięcie MSIL po danym przesunięciu macierzystym.  
  
 Debuger założy, że każdy stare przesunięcie odwołuje się do MSIL w kodzie MSIL oryginalne, niezmodyfikowanego i że każdy nowy przesunięcie odwołuje się do przesunięcia MSIL kodem nowe, instrumentowanych. Mapa powinny być sortowane w kolejności rosnącej. Do przechodzenia, aby zapewnić prawidłowe działanie, należy przestrzegać następujących wytycznych:  
  
-   Nie zmieniają kolejności instrumentowanych kod MSIL.  
  
-   Nie usuwaj oryginalnego kodu MSIL.  
  
-   Zawierać wpisy dla wszystkich punktów sekwencji z plik bazy danych (PDB) programu w mapie. Mapa nie interpolacji Brak wpisów. Tak biorąc pod uwagę poniższe mapy:  
  
     (0 stare, 0 nowe)  
  
     (5 stare, 10 nowych)  
  
     (9 stare, 20 nowych)  
  
    -   Stary przesunięcia 0, 1, 2, 3 lub 4 zostanie zamapowane do nowego przesunięciu 0.  
  
    -   Przesunięcie stare 5, 6, 7 lub 8 zostaną odwzorowane na nowe przesunięcie 10.  
  
    -   Stary przesunięcie 9 lub nowszą zostaną odwzorowane na nowe przesunięcie 20.  
  
    -   Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostaną zmapowane do starego przesunięciu 0.  
  
    -   Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie zamapowane do starego przesunięcia 5.  
  
    -   Nowe przesunięcie 20 lub nowszej zostanie zamapowane do starego przesunięcia 9.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
