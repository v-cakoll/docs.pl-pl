---
title: Zdarzenia ETW modułu ładującego
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87ec70b2b27c8886ac9b567498d75f9294437bed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141534"
---
# <a name="loader-etw-events"></a>Zdarzenia ETW modułu ładującego
<a name="top"></a> Te zdarzenia zbierać informacje dotyczące ładowanie i zwalnianie domen aplikacji, zestawów i modułów.  
  
 Wszystkie zdarzenia modułu ładującego są wywoływane w obszarze `LoaderKeyword` — słowo kluczowe (0x8). `DCStart` i `DCEnd` zdarzenia są wywoływane w obszarze `LoaderRundownKeyword` (0x8) za pomocą `StartRundown` / `EndRundown` włączone. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
 Zdarzenia modułu ładującego są podzielone na następujące czynności:  
  
-   [Zdarzenia domeny aplikacji](#application_domain_events)  
  
-   [Zdarzenia zestaw modułu ładującego CLR](#clr_loader_assembly_events)  
  
-   [Zdarzenia modułu](#module_events)  
  
-   [Zdarzenia modułu domeny CLR](#clr_domain_module_events)  
  
-   [Zakres modułu zdarzeń](#module_range_events)  
  
<a name="application_domain_events"></a>   
## <a name="application-domain-events"></a>Zdarzenia domeny aplikacji  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AppDomainLoad_V1` and `AppDomainUnLoad_V1`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1` (rejestrowane dla wszystkich domen aplikacji)|156|Wywoływane, gdy domena aplikacji zostanie utworzony w okresie istnienia procesu.|  
|`AppDomainUnLoad_V1`|157|Wywoływane, gdy domena aplikacji zostanie zniszczony w okresie istnienia procesu.|  
|`AppDomainDCStart_V1`|157|Wylicza domen aplikacji podczas Początek podsumowania.|  
|`AppDomainDCEnd_V1`|158|Wylicza domen aplikacji podczas koniec podsumowania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Unikatowy identyfikator dla domeny aplikacji.|  
|AppDomainFlags|win: UInt32.|0x1: Domyślna domena.<br /><br /> 0x2: Plik wykonywalny.<br /><br /> 0x4: Domeny aplikacji, bit 28 – 31: Udostępnianie zasad tej domeny.<br /><br /> 0: Udostępnione domenie.|  
|AppDomainName|win:UnicodeString|Aplikacja przyjazna nazwa domeny. Mogą ulec zmianie w okresie istnienia procesu.|  
|AppDomainIndex|win: UInt32.|Indeks tej domeny aplikacji.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="clr_loader_assembly_events"></a>   
## <a name="clr-loader-assembly-events"></a>Zdarzenia zestaw modułu ładującego CLR  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AssemblyLoad` and `AssemblyUnload`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Wywoływane, gdy zestaw jest ładowany.|  
|`AssemblyUnload_V1`|155|Wywoływane, gdy zestaw jest zwalniana.|  
|`AssemblyDCStart_V1`|155|Wylicza zestawy podczas Początek podsumowania.|  
|`AssemblyDCEnd_V1`|156|Wylicza zestawy podczas koniec podsumowania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AssemblyID|win:UInt64|Unikatowy identyfikator dla zestawu.|  
|AppDomainID|win:UInt64|Identyfikator domeny tego zestawu.|  
|BindingID|win:UInt64|Identyfikator, który unikatowo identyfikuje powiązań zestawów.|  
|Assemblyflags —|win: UInt32.|0x1: Zestaw neutralnej domeny.<br /><br /> 0x2: Zestaw dynamiczny.<br /><br /> 0x4: Zestaw ma obrazu natywnego.<br /><br /> 0x8: Zestaw kolekcjonowany.|  
|AssemblyName|win:UnicodeString|W pełni kwalifikowanej nazwy zestawu.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="module_events"></a>   
## <a name="module-events"></a>Zdarzenia modułu  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`ModuleLoad_V2` and `ModuleUnload_V2`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Komunikat informacyjny (4)|  
||||  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Wywoływane, gdy moduł jest załadowany w okresie istnienia procesu.|  
|`ModuleUnload_V2`|153|Wywoływane, gdy moduł jest zwalniana w okresie istnienia procesu.|  
|`ModuleDCStart_V2`|153|Wylicza modułów podczas Początek podsumowania.|  
|`ModuleDCEnd_V2`|154|Wylicza modułów podczas koniec podsumowania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt64|Unikatowy identyfikator dla modułu.|  
|AssemblyID|win:UInt64|Identyfikator zestawu, w której znajduje się w tym module.|  
|ModuleFlags|win: UInt32.|0x1: Moduł neutralnej domeny.<br /><br /> 0x2: Moduł ma obrazu natywnego.<br /><br /> 0x4: Modułu dynamicznego.<br /><br /> 0x8: Manifest modułu.|  
|Reserved1|win: UInt32.|Pole zarezerwowane.|  
|ModuleILPath|win:UnicodeString|Ścieżka obrazu Microsoft intermediate language (MSIL) dla modułu lub nazwy modułu dynamicznego, jeśli zestaw dynamiczny (zakończony znakiem null).|  
|ModuleNativePath|win:UnicodeString|Ścieżka modułu obrazu natywnego, jeśli jest obecny (zakończony znakiem null).|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
|ManagedPdbSignature|win: identyfikator GUID|Podpis identyfikator GUID zarządzanej bazy danych programu (PDB), która jest zgodna z ten moduł. (Zobacz Uwagi).|  
|ManagedPdbAge|win: UInt32.|Wiek numer zapisywane do PDB zarządzanego, który pasuje do tego modułu. (Zobacz Uwagi).|  
|ManagedPdbBuildPath|win:UnicodeString|Ścieżka do lokalizacji, w którym zarządzanych pliku PDB, która jest zgodna z ten moduł został skompilowany. W niektórych przypadkach może to być tylko nazwę pliku. (Zobacz Uwagi).|  
|NativePdbSignature|win: identyfikator GUID|Identyfikator GUID podpis Native Image Generator (NGen) PDB zgodną tego modułu, jeśli ma to zastosowanie. (Zobacz Uwagi).|  
|NativePdbAge|win: UInt32.|Wiek numer zapisywane w pliku PDB NGen, która jest zgodna z ten moduł, jeśli ma to zastosowanie. (Zobacz Uwagi).|  
|NativePdbBuildPath|win:UnicodeString|Ścieżka do lokalizacji, w którym PDB NGen, która jest zgodna z ten moduł został skompilowany, jeśli ma to zastosowanie. W niektórych przypadkach może to być tylko nazwę pliku. (Zobacz Uwagi).|  
  
### <a name="remarks"></a>Uwagi  
  
-   Pola, które mają "Pdb" w nazwach może służyć przez narzędzia profilowania, aby zlokalizować pliki PDB, które odpowiadają moduły, które zostały załadowane podczas sesji profilowania. Wartości te pola odpowiadają zapisanych na sekcje IMAGE_DIRECTORY_ENTRY_DEBUG modułu zwykle używane przez debugery do lokalizowania plików PDB, które odpowiadają załadowane moduły danych.  
  
-   Nazwy pól, które zaczynają się od "ManagedPdb" odnoszą się do zarządzanego pliku PDB, odpowiadający moduł MSIL, który został wygenerowany przez kompilator zarządzanych (takie jak C# lub kompilator Visual Basic). Ten plik PDB używa zarządzanego format pliku PDB, a w tym artykule opisano, jak elementy z oryginalnego zarządzanym kodzie źródłowym, takie jak pliki, numery wierszy i nazwy symboli mapują do elementów MSIL, które są kompilowane do moduł MSIL.  
  
-   Nazwy pól, które zaczynają się od "NativePdb" odnoszą się do polecenia NGen pliku PDB, wygenerowanego przez wywołanie metody `NGEN createPDB`. Ten plik PDB używa natywnego formatu pliku PDB i opisuje sposób mapowania elementów od oryginalnego kodu zarządzanego źródła, takich jak pliki, numery wierszy i nazwy symboli do natywnego elementów, które są kompilowane do modułu programu NGen.  
  
 [Powrót do początku](#top)  
  
<a name="clr_domain_module_events"></a>   
## <a name="clr-domain-module-events"></a>Zdarzenia modułu domeny CLR  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Wywoływane, gdy moduł jest ładowany do domeny aplikacji.|  
|`DomainModuleDCStart_V1`|151|Wylicza moduły załadowane dla domeny aplikacji w czasie Początek podsumowania i jest rejestrowane dla wszystkich domen aplikacji.|  
|`DomainModuleDCEnd_V1`|152|Wylicza moduły załadowane dla domeny aplikacji w czasie koniec podsumowania, a jest rejestrowane dla wszystkich domen aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt64|Identyfikuje zestaw, do której należy ten moduł.|  
|AssemblyID|win:UInt64|Identyfikator zestawu, w której znajduje się w tym module.|  
|AppDomainID|win:UInt64|Identyfikator domeny aplikacji, w którym ten moduł jest używany.|  
|ModuleFlags|win: UInt32.|0x1: Moduł neutralnej domeny.<br /><br /> 0x2: Moduł ma obrazu natywnego.<br /><br /> 0x4: Modułu dynamicznego.<br /><br /> 0x8: Manifest modułu.|  
|Reserved1|win: UInt32.|Pole zarezerwowane.|  
|ModuleILPath|win:UnicodeString|Ścieżka obrazu MSIL dla modułu lub nazwy modułu dynamicznego, jeśli zestaw dynamiczny (zakończony znakiem null).|  
|ModuleNativePath|win:UnicodeString|Ścieżka modułu obrazu natywnego, jeśli jest obecny (zakończony znakiem null).|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="module_range_events"></a>   
## <a name="module-range-events"></a>Zakres modułu zdarzeń  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Komunikat informacyjny (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Komunikat informacyjny (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|To zdarzenie jest obecny, jeśli ładowany obraz Native Image Generator (NGen) została zoptymalizowana z IBC i zawiera informacje o gorąca części obrazów NGen.|  
|`ModuleRangeDCStart`|160|A `ModuleRange` Zdarzenie uruchamiane podczas uruchamiania podsumowania.|  
|`ModuleRangeDCEnd`|161|A `ModuleRange` Zdarzenie uruchamiane na koniec podsumowania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win: UInt16.|Jednoznacznie identyfikuje określone wystąpienie CLR w procesie, jeśli wiele wystąpień środowiska CLR są ładowane.|  
|ModuleID|win:UInt64|Identyfikuje zestaw, do której należy ten moduł.|  
|RangeBegin|win: UInt32.|Przesunięcie w module, który reprezentuje początek zakresu dla typu określonego zakresu.|  
|RangeSize|win: UInt32.|Rozmiar określony zakres, w bajtach.|  
|RangeType|win: UInt32.|Pojedyncze wartości 0x4 do reprezentowania zimnych IBC zakresów. To pole może reprezentować więcej wartości w przyszłości.|  
|RangeSize1|win: UInt32.|wartość 0 wskazuje nieprawidłowe dane.|  
|RangeBegin2|win:UnicodeString||  
  
### <a name="remarks"></a>Uwagi  
 Jeśli został zoptymalizowany załadowanych obrazów NGen w procesie .NET Framework za pomocą IBC, `ModuleRange` jest rejestrowane zdarzenie, zawierający gorąca zakresów w obrazów NGen, wraz z jego `moduleID` i `ClrInstanceID`.  Jeśli nie zoptymalizowano obrazów NGen z IBC, to zdarzenie nie jest rejestrowane. Aby określić nazwę modułu, to zdarzenie musi być sortowane przy użyciu zdarzenia ETW modułu obciążenia.  
  
 Rozmiar ładunku dla tego zdarzenia jest zmienna; `Count` pola wskazuje liczbę zakres przesunięcia zawarte w zdarzeniu.  To zdarzenie ma być sortowane przy użyciu Windows `IStart` zdarzenia w celu określenia rzeczywistego zakresów. Ładowanie obrazu Windows zdarzenie jest rejestrowane, zawsze wtedy, gdy obraz jest ładowany i zawiera adres wirtualny załadowanego obrazu.  
  
 Zdarzenia zakresu modułu są uruchamiane w ramach dowolnego poziomu ETW większa lub równa 4 i są klasyfikowane jako zdarzenia informacyjne.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia ETW CLR](../../../docs/framework/performance/clr-etw-events.md)
