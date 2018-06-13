---
title: Zdarzenia ETW modułu ładującego
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4746e9e7c8c83caf09ccf51749e9e3cbe69ec52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397432"
---
# <a name="loader-etw-events"></a>Zdarzenia ETW modułu ładującego
<a name="top"></a> Te zdarzenia zbierać informacje dotyczące ładowanie i zwalnianie domen aplikacji, zestawów i modułów.  
  
 Wszystkie zdarzenia modułu ładującego pojawienia się w obszarze `LoaderKeyword` — słowo kluczowe (0x8). `DCStart` i `DCEnd` zdarzenia są generowane w obszarze `LoaderRundownKeyword` (0x8) z `StartRundown` / `EndRundown` włączone. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
 Zdarzenia modułu ładującego są podzielone na następujące czynności:  
  
-   [Zdarzenia domeny aplikacji](#application_domain_events)  
  
-   [Zdarzenia zestawu modułu ładującego CLR](#clr_loader_assembly_events)  
  
-   [Zdarzenia modułu](#module_events)  
  
-   [Zdarzenia modułu domeny CLR](#clr_domain_module_events)  
  
-   [Zakres modułu zdarzeń](#module_range_events)  
  
<a name="application_domain_events"></a>   
## <a name="application-domain-events"></a>Zdarzenia domeny aplikacji  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AppDomainLoad_V1` I `AppDomainUnLoad_V1`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1` (rejestrowane dla wszystkich domen aplikacji)|156|Wywoływane, gdy domena aplikacji jest tworzony przez cały okres istnienia procesu.|  
|`AppDomainUnLoad_V1`|157|Wywoływane, gdy domeny aplikacji zostanie zniszczony przez cały okres istnienia procesu.|  
|`AppDomainDCStart_V1`|157|Wylicza domeny aplikacji podczas uwalniania rozpoczęcia.|  
|`AppDomainDCEnd_V1`|158|Wylicza domeny aplikacji podczas uwalniania zakończenia.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AppDomainID|Windows: UInt64|Unikatowy identyfikator domeny aplikacji.|  
|AppDomainFlags|Windows: UInt32.|0x1: domeny domyślnej.<br /><br /> 0x2: plik wykonywalny.<br /><br /> 0x4: 28-31-bitowy domeny aplikacji: udostępnianie zasad domeny.<br /><br /> 0: udostępnionego domeny.|  
|AppDomainName|Windows: UnicodeString|Aplikacja przyjazną nazwę domeny. Mogą ulec zmianie przez cały okres istnienia procesu.|  
|AppDomainIndex|Windows: UInt32.|Indeks tej domeny aplikacji.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="clr_loader_assembly_events"></a>   
## <a name="clr-loader-assembly-events"></a>Zdarzenia zestawu modułu ładującego CLR  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AssemblyLoad` I `AssemblyUnload`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Wywoływane, gdy zestaw jest ładowany.|  
|`AssemblyUnload_V1`|155|Wywoływane, gdy zestaw jest zwolniony.|  
|`AssemblyDCStart_V1`|155|Wylicza zestawy podczas uwalniania rozpoczęcia.|  
|`AssemblyDCEnd_V1`|156|Wylicza zestawy podczas uwalniania zakończenia.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Właściwość AssemblyID|Windows: UInt64|Unikatowy identyfikator dla zestawu.|  
|AppDomainID|Windows: UInt64|Identyfikator domeny tego zestawu.|  
|Atrybut BindingID|Windows: UInt64|Identyfikator, który unikatowo identyfikuje powiązań zestawów.|  
|AssemblyFlags|Windows: UInt32.|0x1: zestaw niezależnym od domeny.<br /><br /> 0x2: zestawu dynamicznego.<br /><br /> 0x4: zestaw ma obrazu macierzystego.<br /><br /> 0x8: zestawu kolekcjonowanego.|  
|AssemblyName|Windows: UnicodeString|Pełni kwalifikowanej nazwy zestawu.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="module_events"></a>   
## <a name="module-events"></a>Zdarzenia modułu  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`ModuleLoad_V2` I `ModuleUnload_V2`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Komunikat informacyjny (4)|  
||||  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Wywoływane, gdy moduł jest załadowana przez cały okres istnienia procesu.|  
|`ModuleUnload_V2`|153|Wywoływane, gdy moduł jest zwolniony przez cały okres istnienia procesu.|  
|`ModuleDCStart_V2`|153|Wylicza modułów podczas uwalniania rozpoczęcia.|  
|`ModuleDCEnd_V2`|154|Wylicza modułów podczas uwalniania zakończenia.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ModuleID|Windows: UInt64|Unikatowy identyfikator dla modułu.|  
|Właściwość AssemblyID|Windows: UInt64|Identyfikator zestawu, w której znajduje się w tym module.|  
|ModuleFlags|Windows: UInt32.|0x1: moduł niezależnym od domeny.<br /><br /> 0x2: moduł ma obrazu macierzystego.<br /><br /> 0x4: module dynamicznym.<br /><br /> 0x8: moduł manifestu.|  
|Reserved1|Windows: UInt32.|Pole zarezerwowane.|  
|ModuleILPath|Windows: UnicodeString|Ścieżka obrazu język pośredni (MSIL) firmy Microsoft dla modułu lub nazwa modułu dynamicznego, jeśli jest to zestaw dynamiczny (zakończonym znakiem null).|  
|ModuleNativePath|Windows: UnicodeString|Ścieżka modułu obrazu macierzystego, jeśli jest obecny (zakończonym znakiem null).|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
|ManagedPdbSignature|Windows: identyfikator GUID|Identyfikator GUID podpis zarządzanych bazę danych programu (PDB) odpowiadający tego modułu. (Zobacz Uwagi).|  
|ManagedPdbAge|Windows: UInt32.|Wiek numer zapisywane do zarządzanego pliku PDB odpowiadający tego modułu. (Zobacz Uwagi).|  
|ManagedPdbBuildPath|Windows: UnicodeString|Ścieżka do lokalizacji, w której zarządzane pliku PDB odpowiadający ten moduł został skompilowany. W niektórych przypadkach może to być tylko nazwę pliku. (Zobacz Uwagi).|  
|NativePdbSignature|Windows: identyfikator GUID|Identyfikator GUID podpis natywnego Generator obrazu (NGen) PDB odpowiadający ten moduł, jeśli ma to zastosowanie. (Zobacz Uwagi).|  
|NativePdbAge|Windows: UInt32.|Wiek numer zapisane PDB NGen odpowiadający ten moduł, jeśli ma to zastosowanie. (Zobacz Uwagi).|  
|NativePdbBuildPath|Windows: UnicodeString|Ścieżka do lokalizacji, gdzie PDB NGen odpowiadający ten moduł został skompilowany, jeśli ma to zastosowanie. W niektórych przypadkach może to być tylko nazwę pliku. (Zobacz Uwagi).|  
  
### <a name="remarks"></a>Uwagi  
  
-   Pola, które mają w nazwach "Pdb" mogą posłużyć narzędzia profilowania do zlokalizowania plików PDB zgodnych modułów, które zostały załadowane w czasie sesji profilowania. Wartości tych pól odpowiadają zapisanych na sekcje IMAGE_DIRECTORY_ENTRY_DEBUG modułu zwykle używany przez debugery do lokalizowania plików PDB, które odpowiadają załadowanych modułów danych.  
  
-   Nazwy pól, które zaczynają się od "ManagedPdb" odnoszą się do zarządzanych plików PDB odpowiadający moduł MSIL, który został wygenerowany przez kompilator zarządzanych (na przykład kompilatora C# lub Visual Basic). Ten plik PDB w formacie zarządzanych plików PDB i opisano sposób mapowania elementy z oryginalnego kodu źródłowego zarządzane, takie jak pliki, numery wierszy i nazwy symboli dla elementów MSIL, które są łączone w moduł MSIL.  
  
-   Nazwy pól, które zaczynają się od "NativePdb" można znaleźć pliku PDB NGen generowane przez wywołanie metody `NGEN createPDB`. Ten plik PDB używa formatu macierzystego PDB i zawiera opis sposobu mapowania elementy z oryginalnego kodu źródłowego zarządzane, takie jak pliki, numery wierszy i nazwy symboli natywnych elementy, które są łączone w NGen module.  
  
 [Powrót do początku](#top)  
  
<a name="clr_domain_module_events"></a>   
## <a name="clr-domain-module-events"></a>Zdarzenia modułu domeny CLR  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Komunikat informacyjny (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Wywoływane, gdy moduł jest ładowana dla domeny aplikacji.|  
|`DomainModuleDCStart_V1`|151|Wylicza moduły załadowane dla domeny aplikacji w czasie uwalniania start i jest rejestrowane dla wszystkich domen aplikacji.|  
|`DomainModuleDCEnd_V1`|152|Wylicza moduły załadowane dla domeny aplikacji w czasie zakończenia uwalniania i jest rejestrowane dla wszystkich domen aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ModuleID|Windows: UInt64|Określa zestaw, do którego należy ten moduł.|  
|Właściwość AssemblyID|Windows: UInt64|Identyfikator zestawu, w której znajduje się w tym module.|  
|AppDomainID|Windows: UInt64|Identyfikator domeny aplikacji, w którym ten moduł jest używany.|  
|ModuleFlags|Windows: UInt32.|0x1: moduł niezależnym od domeny.<br /><br /> 0x2: moduł ma obrazu macierzystego.<br /><br /> 0x4: module dynamicznym.<br /><br /> 0x8: moduł manifestu.|  
|Reserved1|Windows: UInt32.|Pole zarezerwowane.|  
|ModuleILPath|Windows: UnicodeString|Ścieżka obrazu MSIL modułu lub nazwa modułu dynamicznego, jeśli jest to zestaw dynamiczny (zakończonym znakiem null).|  
|ModuleNativePath|Windows: UnicodeString|Ścieżka modułu obrazu macierzystego, jeśli jest obecny (zakończonym znakiem null).|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="module_range_events"></a>   
## <a name="module-range-events"></a>Zakres modułu zdarzeń  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Komunikat informacyjny (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Komunikat informacyjny (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|To zdarzenie jest obecny, jeśli ładowany obraz Generator obrazu natywnego (NGen) zostały zoptymalizowane z IBC i zawiera informacje o sekcji gorąco obrazu NGen.|  
|`ModuleRangeDCStart`|160|A `ModuleRange` Zdarzenie uruchamiane na początku uwalniania.|  
|`ModuleRangeDCEnd`|161|A `ModuleRange` zdarzenia wywoływane na końcu uwalniania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Windows: UInt16|Unikatowo identyfikuje konkretne wystąpienie środowiska CLR w procesie, jeśli są załadowanych wiele wystąpień środowiska CLR.|  
|ModuleID|Windows: UInt64|Określa zestaw, do którego należy ten moduł.|  
|RangeBegin|Windows: UInt32.|Przesunięcie w module, który reprezentuje początek zakresu dla typu określonego zakresu.|  
|RangeSize|Windows: UInt32.|Rozmiar w bajtach określony zakres.|  
|Właściwość RangeType|Windows: UInt32.|Pojedynczą wartość, 0x4, do reprezentowania zimnych IBC zakresów. To pole może wymagać więcej wartości w przyszłości.|  
|RangeSize1|Windows: UInt32.|wartość 0 wskazuje nieprawidłowe dane.|  
|RangeBegin2|Windows: UnicodeString||  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ładowany obraz NGen w procesie .NET Framework został zoptymalizowany z IBC, `ModuleRange` jest rejestrowane zdarzenie, zawierający gorących zakresów w obrazie NGen, wraz z jego `moduleID` i `ClrInstanceID`.  Jeśli nie zoptymalizowano obrazów NGen z IBC, to zdarzenie nie jest rejestrowane. Aby określić nazwę modułu, to zdarzenie musi być sortowane z zdarzenia ETW modułu obciążenia.  
  
 Rozmiar ładunku dla tego zdarzenia jest zmienna; `Count` pola wskazuje liczbę zakres przesunięcia zawarte w zdarzeniu.  To zdarzenie ma mają być sortowane w systemie Windows `IStart` zdarzenia w celu określenia rzeczywiste zakresy. Zawsze, gdy obraz został załadowany i zawiera wirtualny adres ładowany obraz, jest rejestrowane zdarzenie ładowania obrazu systemu Windows.  
  
 Zdarzenia zakresu modułu są uruchamiane w dowolnym poziomie ETW większa lub równa 4 i sklasyfikowanych jako zdarzenia informacyjne.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
