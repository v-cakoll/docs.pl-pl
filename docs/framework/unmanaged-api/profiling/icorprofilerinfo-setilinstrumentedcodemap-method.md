---
title: "ICorProfilerInfo::SetILInstrumentedCodeMap — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 127f6d76e85ed30f1407d16f8d81c93dd2941960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap — Metoda
Ustawia mapę kodu dla funkcji określonej przy użyciu określonego wpisów map język pośredni (MSIL) firmy Microsoft.  
  
> [!NOTE]
>  W programie .NET Framework w wersji 2.0, wywoływania `SetILInstrumentedCodeMap` na `FunctionID` czy reprezentuje ogólnego działać w domenie określonej aplikacji będzie miało wpływ na wszystkie wystąpienia tej funkcji w domenie aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, dla którego mają zostać ustawione mapy kodu.  
  
 `fStartJit`  
 [in] Wartość logiczna, która wskazuje, czy wywołanie `SetILInstrumentedCodeMap` metoda jest pierwszy dla konkretnej `FunctionID`. Ustaw `fStartJit` do `true` w pierwszym wywołaniu `SetILInstrumentedCodeMap` dla danego `FunctionID`, a w `false` później.  
  
 `cILMapEntries`  
 [in] Liczba elementów w `cILMapEntries` tablicy.  
  
 `rgILMapEntries`  
 [in] Tablica struktur COR_IL_MAP, z których każdy określa przesunięcie MSIL.  
  
## <a name="remarks"></a>Uwagi  
 Profiler często wstawia instrukcje w kodzie źródłowym metody w celu agregowania tej metody (na przykład do wysyłania powiadomień o osiągnięciu wiersza danego źródła). `SetILInstrumentedCodeMap`Umożliwia profiler do mapowania oryginalnego instrukcje MSIL do nowej lokalizacji. Można użyć profiler [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metodę, aby pobrać oryginalnego przesunięcie MSIL dla danego przesunięcia macierzystego.  
  
 Debuger przyjmie założenie, że każdy starego przesunięcie odwołuje się do MSIL w oryginalnym niezmodyfikowanego kodu MSIL, i że każdego nowego przesunięcie odwołuje się do przesunięcia MSIL kodem nowy, instrumentowanych. Mapy mają być sortowane w kolejności rosnącej. Wykonywanie krok po kroku, aby działała poprawnie, wykonaj następujące wytyczne:  
  
-   Zmień kolejność nie instrumentowanych kod MSIL.  
  
-   Nie usuwaj oryginalnego kodu MSIL.  
  
-   Zawierać wpisy dla wszystkich punktów sekwencji z pliku programu (PDB) bazy danych na mapie. Mapa nie interpolować Brak wpisów. Tak podane mapy następujące:  
  
     (0 stare, 0 nowy)  
  
     (5 stare, 10 nowych)  
  
     (9 stare, 20 nowy)  
  
    -   Stary przesunięciem równym 0, 1, 2, 3 lub 4 zostaną zmapowane do nowego przesunięciu 0.  
  
    -   Stary przesunięcie 5, 6, 7 lub 8 zostaną zmapowane do nowego przesunięcie 10.  
  
    -   Przesunięcie starego 9 lub nowszą zostaną zmapowane do nowego przesunięcie 20.  
  
    -   Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostaną zmapowane do starego przesunięciu 0.  
  
    -   Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostaną zmapowane do starego przesunięcie 5.  
  
    -   Nowe przesunięcie 20 lub wyższe zostaną zmapowane do starego przesunięcie 9.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
