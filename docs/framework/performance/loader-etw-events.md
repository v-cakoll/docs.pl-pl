---
title: Zdarzenia ETW modułu ładującego
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6177bdff873feb75eb15dba53bcdb5197260fa9d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046392"
---
# <a name="loader-etw-events"></a>Zdarzenia ETW modułu ładującego
<a name="top"></a>Te zdarzenia zbierają informacje dotyczące ładowania i zwalniania domen aplikacji, zestawów i modułów.  
  
 Wszystkie zdarzenia modułu ładującego są wywoływane `LoaderKeyword` za pomocą słowa kluczowego (0x8). `LoaderRundownKeyword` `StartRundown` / Zdarzenia i są wywoływane w (0x8) z`EndRundown` włączony. `DCStart` `DCEnd` (Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).  
  
 Zdarzenia modułu ładującego są podzielone na następujące:  
  
- [Zdarzenia domeny aplikacji](#application_domain_events)  
  
- [Zdarzenia zestawu modułu ładującego CLR](#clr_loader_assembly_events)  
  
- [Zdarzenia modułu](#module_events)  
  
- [Zdarzenia modułu CLR Domain](#clr_domain_module_events)  
  
- [Zdarzenia zakresu modułu](#module_range_events)  
  
<a name="application_domain_events"></a>   
## <a name="application-domain-events"></a>Zdarzenia domeny aplikacji  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`0x8|`AppDomainLoad_V1` i `AppDomainUnLoad_V1`|Informacyjny (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Informacyjny (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1`(zarejestrowane dla wszystkich domen aplikacji)|156|Uruchamiany zawsze, gdy domena aplikacji zostanie utworzona w okresie istnienia procesu.|  
|`AppDomainUnLoad_V1`|157|Uruchamiany zawsze, gdy domena aplikacji zostanie zniszczona w okresie istnienia procesu.|  
|`AppDomainDCStart_V1`|157|Wylicza domeny aplikacji podczas początkowego uwalniania.|  
|`AppDomainDCEnd_V1`|158|Wylicza domeny aplikacji podczas końcowego uwalniania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AppDomainID|win: UInt64|Unikatowy identyfikator domeny aplikacji.|  
|AppDomainFlags|win: UInt32|0x1 Domena domyślna.<br /><br /> 0x2: Plik.<br /><br /> 0x4: Domena aplikacji, bit 28-31: Zasady udostępniania tej domeny.<br /><br /> 0: Domena udostępniona.|  
|Element AppDomainname|win: UnicodeString|Przyjazna nazwa domeny aplikacji. Może ulec zmianie w okresie istnienia procesu.|  
|AppDomainIndex|win: UInt32|Indeks domeny aplikacji.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="clr_loader_assembly_events"></a>   
## <a name="clr-loader-assembly-events"></a>Zdarzenia zestawu modułu ładującego CLR  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`0x8|`AssemblyLoad` i `AssemblyUnload`|Informacyjny (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Informacyjny (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Uruchamiany po załadowaniu zestawu.|  
|`AssemblyUnload_V1`|155|Uruchamiany, gdy zestaw zostanie zwolniony.|  
|`AssemblyDCStart_V1`|155|Wylicza zestawy w trakcie początkowego uwalniania.|  
|`AssemblyDCEnd_V1`|156|Wylicza zestawy podczas końcowego uwalniania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AssemblyID|win: UInt64|Unikatowy identyfikator zestawu.|  
|AppDomainID|win: UInt64|Identyfikator domeny tego zestawu.|  
|BindingID|win: UInt64|Identyfikator, który jednoznacznie identyfikuje powiązanie zestawu.|  
|AssemblyFlags —|win: UInt32|0x1 Zestaw neutralny domeny.<br /><br /> 0x2: Zestaw dynamiczny.<br /><br /> 0x4: Zestaw ma obraz natywny.<br /><br /> 0x8 Zestaw kolekcjonowany.|  
|AssemblyName|win: UnicodeString|W pełni kwalifikowana nazwa zestawu.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="module_events"></a>   
## <a name="module-events"></a>Zdarzenia modułu  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`0x8|`ModuleLoad_V2` i `ModuleUnload_V2`|Informacyjny (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Informacyjny (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Informacyjny (4)|  
||||  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Uruchamiany, gdy moduł jest ładowany w okresie istnienia procesu.|  
|`ModuleUnload_V2`|153|Uruchamiany, gdy moduł zostanie zwolniony w okresie istnienia procesu.|  
|`ModuleDCStart_V2`|153|Wylicza moduły podczas uruchamiania.|  
|`ModuleDCEnd_V2`|154|Wylicza moduły podczas końcowego uwalniania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ModuleID|win: UInt64|Unikatowy identyfikator modułu.|  
|AssemblyID|win: UInt64|Identyfikator zestawu, w którym znajduje się ten moduł.|  
|ModuleFlags|win: UInt32|0x1 Moduł neutralny dla domeny.<br /><br /> 0x2: Moduł ma obraz natywny.<br /><br /> 0x4: Moduł dynamiczny.<br /><br /> 0x8 Moduł manifestu.|  
|Reserved1|win: UInt32|Pole zastrzeżone.|  
|ModuleILPath|win: UnicodeString|Ścieżka obrazu języka pośredniego firmy Microsoft (MSIL) dla modułu lub nazwy modułu dynamicznego, jeśli jest to zestaw dynamiczny (zakończony zerem).|  
|ModuleNativePath|win: UnicodeString|Ścieżka do obrazu natywnego modułu, jeśli jest obecny (zakończony zerem).|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
|ManagedPdbSignature|win: identyfikator GUID|Sygnatura identyfikatora GUID programu Managed Database (PDB), która jest zgodna z tym modułem. (Zobacz uwagi).|  
|ManagedPdbAge|win: UInt32|Numer wieku zapisany w zarządzanym pliku PDB, który jest zgodny z tym modułem. (Zobacz uwagi).|  
|ManagedPdbBuildPath|win: UnicodeString|Ścieżka do lokalizacji, w której został skompilowany zarządzany plik PDB zgodny z tym modułem. W niektórych przypadkach może to być nazwa pliku. (Zobacz uwagi).|  
|NativePdbSignature|win: identyfikator GUID|Podpis GUID pliku PDB (Native Image Generator), który jest zgodny z tym modułem, jeśli ma zastosowanie. (Zobacz uwagi).|  
|NativePdbAge|win: UInt32|Numer wieku zapisany w pliku PDB programu NGen, który jest zgodny z tym modułem, jeśli ma zastosowanie. (Zobacz uwagi).|  
|NativePdbBuildPath|win: UnicodeString|Ścieżka do lokalizacji, w której został skompilowany plik PDB programu NGen pasujący do tego modułu, jeśli ma zastosowanie. W niektórych przypadkach może to być nazwa pliku. (Zobacz uwagi).|  
  
### <a name="remarks"></a>Uwagi  
  
- Pola, które mają "pdb" w swoich nazwach, mogą być używane przez narzędzia profilowania do lokalizowania plików PDB, które pasują do modułów, które zostały załadowane podczas sesji profilowania. Wartości tych pól odnoszą się do danych, które są zapisywane w sekcjach IMAGE_DIRECTORY_ENTRY_DEBUG modułu zwykle używanych przez debugery, aby ułatwić znalezienie plików PDB pasujących do załadowanych modułów.  
  
- Nazwy pól zaczynające się od "ManagedPdb" odnoszą się do zarządzanego pliku PDB odpowiadającego modułowi MSIL, który został wygenerowany przez zarządzany kompilator (na C# przykład kompilator lub Visual Basic). Ten plik PDB używa zarządzanego formatu PDB i opisuje sposób, w jaki elementy z oryginalnego zarządzanego kodu źródłowego, takie jak pliki, numery wierszy i nazwy symboli, są mapowane na elementy MSIL, które są kompilowane do modułu MSIL.  
  
- Nazwy pól zaczynające się od ciągu "NativePdb" odnoszą się do pliku PDB programu `NGEN createPDB`NGen wygenerowanego przez wywołanie. Ten plik PDB używa natywnego formatu PDB i opisuje sposób, w jaki elementy z oryginalnego zarządzanego kodu źródłowego, takie jak pliki, numery wierszy i nazwy symboli, są mapowane na elementy natywne, które są kompilowane w module NGen.  
  
 [Powrót do początku](#top)  
  
<a name="clr_domain_module_events"></a>   
## <a name="clr-domain-module-events"></a>Zdarzenia modułu CLR Domain  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`0x8|`DomainModuleLoad_V1`|Informacyjny (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Informacyjny (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Uruchamiany, gdy moduł jest ładowany dla domeny aplikacji.|  
|`DomainModuleDCStart_V1`|151|Wylicza moduły załadowane dla domeny aplikacji podczas początkowego ładowania i rejestrowane dla wszystkich domen aplikacji.|  
|`DomainModuleDCEnd_V1`|152|Wylicza moduły załadowane dla domeny aplikacji podczas końcowego ładowania i rejestrowane dla wszystkich domen aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ModuleID|win: UInt64|Identyfikuje zestaw, do którego należy ten moduł.|  
|AssemblyID|win: UInt64|Identyfikator zestawu, w którym znajduje się ten moduł.|  
|AppDomainID|win: UInt64|Identyfikator domeny aplikacji, w której jest używany ten moduł.|  
|ModuleFlags|win: UInt32|0x1 Moduł neutralny dla domeny.<br /><br /> 0x2: Moduł ma obraz natywny.<br /><br /> 0x4: Moduł dynamiczny.<br /><br /> 0x8 Moduł manifestu.|  
|Reserved1|win: UInt32|Pole zastrzeżone.|  
|ModuleILPath|win: UnicodeString|Ścieżka obrazu MSIL dla modułu lub nazwy modułu dynamicznego, jeśli jest to zestaw dynamiczny (zakończony zerem).|  
|ModuleNativePath|win: UnicodeString|Ścieżka do obrazu natywnego modułu, jeśli jest obecny (zakończony zerem).|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="module_range_events"></a>   
## <a name="module-range-events"></a>Zdarzenia zakresu modułu  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Zdarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Informacyjny (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Informacyjny (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|To zdarzenie jest obecne, jeśli załadowanego obrazu generatora natywnego (NGen) został zoptymalizowany z technologią IBC i zawiera informacje o gorących sekcjach obrazu NGen.|  
|`ModuleRangeDCStart`|160|`ModuleRange` Zdarzenie wywoływane na początku uwalniania.|  
|`ModuleRangeDCEnd`|161|`ModuleRange` Zdarzenie zostało wyzwolone na końcu uwalniania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win: UInt16|Jednoznacznie identyfikuje określone wystąpienie środowiska CLR w procesie w przypadku załadowania wielu wystąpień środowiska CLR.|  
|ModuleID|win: UInt64|Identyfikuje zestaw, do którego należy ten moduł.|  
|RangeBegin|win: UInt32|Przesunięcie w module reprezentujące początek zakresu dla określonego typu zakresu.|  
|RangeSize|win: UInt32|Rozmiar określonego zakresu w bajtach.|  
|Element RangeType|win: UInt32|Pojedyncza wartość, 0x4 do reprezentowania zimnych zakresów IBC. To pole może reprezentować więcej wartości w przyszłości.|  
|RangeSize1|win: UInt32|wartość 0 oznacza złe dane.|  
|RangeBegin2|win: UnicodeString||  
  
### <a name="remarks"></a>Uwagi  
 Jeśli załadowany obraz NGen w procesie .NET Framework został zoptymalizowany pod kątem IBC, `ModuleRange` zdarzenie zawierające zakresy aktywne w obrazie NGEN jest rejestrowane wraz `moduleID` z i `ClrInstanceID`.  Jeśli obraz NGen nie jest zoptymalizowany pod kątem IBC, to zdarzenie nie jest rejestrowane. Aby określić nazwę modułu, to zdarzenie musi być sortowane przy użyciu zdarzeń ETW ładowania modułu.  
  
 Rozmiar ładunku dla tego zdarzenia to zmienna; `Count` pole wskazuje liczbę przesunięć zakresu zawartych w zdarzeniu.  To zdarzenie należy posortować wraz ze zdarzeniem systemu `IStart` Windows, aby określić rzeczywiste zakresy. Zdarzenie ładowania obrazu systemu Windows jest rejestrowane za każdym razem, gdy obraz zostanie załadowany i zawiera adres wirtualny załadowanego obrazu.  
  
 Zdarzenia zakresu modułów są uruchamiane na dowolnym poziomie ETW większym lub równym 4 i są klasyfikowane jako zdarzenia informacyjne.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](clr-etw-events.md)
