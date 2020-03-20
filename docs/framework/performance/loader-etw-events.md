---
title: Zdarzenia ETW modułu ładującego
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
ms.openlocfilehash: 0f8f96cf73882ef6556e5b9e64cf9adf389a2318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180553"
---
# <a name="loader-etw-events"></a>Zdarzenia ETW modułu ładującego
Zdarzenia te zbierają informacje dotyczące ładowania i zwalniania domen aplikacji, zestawów i modułów.  
  
 Wszystkie zdarzenia modułu ładującego są wywoływane w ramach słowa kluczowego `LoaderKeyword` (0x8). I `DCStart` `DCEnd` zdarzenia są wywoływane w obszarze `LoaderRundownKeyword` (0x8) z `StartRundown` / `EndRundown` włączoną. (Aby uzyskać więcej informacji, zobacz [CLR ETW Słowa kluczowe i poziomy](clr-etw-keywords-and-levels.md).)  

## <a name="application-domain-events"></a>Zdarzenia domeny aplikacji
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podbijaniu wydarzenia|Wydarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`AppDomainLoad_V1` i `AppDomainUnLoad_V1`|Informacje (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Informacje (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Informacje (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Wydarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1`(rejestrowane dla wszystkich domen aplikacji)|156|Wywoływane za każdym razem, gdy domena aplikacji jest tworzona w okresie istnienia procesu.|  
|`AppDomainUnLoad_V1`|157|Wywoływane za każdym razem, gdy domena aplikacji zostanie zniszczona w okresie istnienia procesu.|  
|`AppDomainDCStart_V1`|157|Wylicza domen aplikacji podczas uruchomienia rundown.|  
|`AppDomainDCEnd_V1`|158|Wylicza domen aplikacji podczas zakończenia rundown.|  
  
 W poniższej tabeli przedstawiono dane zdarzeń.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Domena aplikacji|wygrana:UInt64|Unikatowy identyfikator domeny aplikacji.|  
|Flagi domen aplikacji|wygrana:UInt32|0x1: Domena domyślna.<br /><br /> 0x2: Wykonywalny.<br /><br /> 0x4: Domena aplikacji, bit 28-31: Zasady udostępniania tej domeny.<br /><br /> 0: Domena udostępniona.|  
|Nazwa aplikacji|wygrać:UnicodeString|Przyjazna nazwa domeny aplikacji. Może ulec zmianie w okresie istnienia procesu.|  
|AppDomainIndex|Wygrana:UInt32|Indeks tej domeny aplikacji.|  
|ClrInstanceID (ida)|wygrana:UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  

## <a name="clr-loader-assembly-events"></a>Zdarzenia zestawu modułu ładującego CLR  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podbijaniu wydarzenia|Wydarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`AssemblyLoad` i `AssemblyUnload`|Informacje (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Informacje (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Informacje (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Wydarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Wywoływane po załadowaniu złożenia.|  
|`AssemblyUnload_V1`|155|Wywoływane, gdy zestaw jest zwalniany.|  
|`AssemblyDCStart_V1`|155|Wylicza zestawy podczas uruchomienia.|  
|`AssemblyDCEnd_V1`|156|Wylicza zestawy podczas zakończenia.|  
  
 W poniższej tabeli przedstawiono dane zdarzeń.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ZestawID|wygrana:UInt64|Unikatowy identyfikator dla złożenia.|  
|Domena aplikacji|wygrana:UInt64|Identyfikator domeny tego zestawu.|  
|PowiązanieID|wygrana:UInt64|Identyfikator, który jednoznacznie identyfikuje powiązanie zestawu.|  
|Lagi montażowe|wygrana:UInt32|0x1: Zestaw neutralny dla domeny.<br /><br /> 0x2: Dynamiczny montaż.<br /><br /> 0x4: Montaż ma obraz macierzysty.<br /><br /> 0x8: Montaż kolekcjonerski.|  
|Assemblyname|wygrać:UnicodeString|W pełni kwalifikowana nazwa zestawu.|  
|ClrInstanceID (ida)|wygrana:UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="module-events"></a>Zdarzenia modułu
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podbijaniu wydarzenia|Wydarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`ModuleLoad_V2` i `ModuleUnload_V2`|Informacje (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Informacje (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Informacje (4)|  
||||  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Wydarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Wywoływane, gdy moduł jest ładowany w okresie istnienia procesu.|  
|`ModuleUnload_V2`|153|Wywoływane, gdy moduł jest zwalniany w okresie istnienia procesu.|  
|`ModuleDCStart_V2`|153|Wylicza moduły podczas uruchamiania.|  
|`ModuleDCEnd_V2`|154|Wylicza moduły podczas zakończenia.|  
  
 W poniższej tabeli przedstawiono dane zdarzeń.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Identyfikator modułu|wygrana:UInt64|Unikatowy identyfikator modułu.|  
|ZestawID|wygrana:UInt64|Identyfikator zestawu, w którym znajduje się ten moduł.|  
|ModułYLags|wygrana:UInt32|0x1: Moduł neutralny dla domeny.<br /><br /> 0x2: Moduł ma obraz macierzysty.<br /><br /> 0x4: Moduł dynamiczny.<br /><br /> 0x8: Moduł manifestu.|  
|Zastrzeżone1|wygrana:UInt32|Pole zarezerwowane.|  
|Ścieżka modułuILPath|wygrać:UnicodeString|Ścieżka obrazu języka pośredniego firmy Microsoft (MSIL) dla modułu lub nazwa modułu dynamicznego, jeśli jest to zestaw dynamiczny (zakończone z wartością null).|  
|Ścieżka modułu|wygrać:UnicodeString|Ścieżka obrazu macierzystego modułu, jeśli jest obecny (zakończone z wartością null).|  
|ClrInstanceID (ida)|wygrana:UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
|Podpis ManagedPdb|wygrana:IDENTYFIKATOR GUID|Podpis guid zarządzanej bazy danych programu (PDB), która pasuje do tego modułu. (Zobacz uwagi).|  
|ManagedPdbAge (Hosting zarządzany)|wygrana:UInt32|Numer wiekowy zapisany w zarządzanym pliku PDB, który pasuje do tego modułu. (Zobacz uwagi).|  
|Ścieżka ManagedPdbBuildPath|wygrać:UnicodeString|Ścieżka do lokalizacji, w której został zbudowany zarządzany PDB, który pasuje do tego modułu. W niektórych przypadkach może to być po prostu nazwa pliku. (Zobacz uwagi).|  
|NativePdbSygnatura|wygrana:IDENTYFIKATOR GUID|Podpis guid natywnego generatora obrazów (NGen) PDB, który pasuje do tego modułu, jeśli ma to zastosowanie. (Zobacz uwagi).|  
|NativePdbAge (NativePdbAge)|wygrana:UInt32|Numer wiekowy zapisany w NGen PDB, który pasuje do tego modułu, jeśli dotyczy. (Zobacz uwagi).|  
|NativePdbBuildPath|wygrać:UnicodeString|Ścieżka do lokalizacji, w której został zbudowany NGen PDB, który pasuje do tego modułu, jeśli dotyczy. W niektórych przypadkach może to być po prostu nazwa pliku. (Zobacz uwagi).|  
  
### <a name="remarks"></a>Uwagi  
  
- Pola, które mają "Pdb" w ich nazwach mogą być używane przez narzędzia profilowania do lokalizowania pdb, które pasują do modułów, które zostały załadowane podczas sesji profilowania. Wartości tych pól odpowiadają danym zapisanym w IMAGE_DIRECTORY_ENTRY_DEBUG sekcje modułu zwykle używane przez debugery w celu zlokalizowania plików PDB, które pasują do załadowanych modułów.  
  
- Nazwy pól, które zaczynają się od "ManagedPdb" odnoszą się do zarządzanego bazy danych PDB odpowiadającej modułowi MSIL, który został wygenerowany przez zarządzany kompilator (na przykład kompilator C# lub Visual Basic). Ten plik PDB używa formatu zarządzanego pliku PDB i opisuje sposób mapowania elementów z oryginalnego zarządzanego kodu źródłowego, takich jak pliki, numery wierszy i nazwy symboli, na elementy MSIL, które są kompilowane do modułu MSIL.  
  
- Nazwy pól, które zaczynają się od "NativePdb" odnoszą `NGEN createPDB`się do bazy danych NGen PDB generowanej przez wywołanie . Ten plik PDB używa natywnego formatu PDB i opisuje, jak elementy z oryginalnego zarządzanego kodu źródłowego, takie jak pliki, numery wierszy i nazwy symboli, są mapowane na elementy macierzyste, które są kompilowane do modułu NGen.  

## <a name="clr-domain-module-events"></a>Zdarzenia modułu domeny CLR
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podbijaniu wydarzenia|Wydarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`DomainModuleLoad_V1`|Informacje (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Informacje (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Informacje (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Wydarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Wywoływane, gdy moduł jest ładowany dla domeny aplikacji.|  
|`DomainModuleDCStart_V1`|151|Wylicza moduły załadowane dla domeny aplikacji podczas uruchomienia i jest rejestrowany dla wszystkich domen aplikacji.|  
|`DomainModuleDCEnd_V1`|152|Wylicza moduły ładowane dla domeny aplikacji podczas zakończenia spływu i jest rejestrowany dla wszystkich domen aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzeń.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Identyfikator modułu|wygrana:UInt64|Identyfikuje zestaw, do którego należy ten moduł.|  
|ZestawID|wygrana:UInt64|Identyfikator zestawu, w którym znajduje się ten moduł.|  
|Domena aplikacji|wygrana:UInt64|Identyfikator domeny aplikacji, w której ten moduł jest używany.|  
|ModułYLags|wygrana:UInt32|0x1: Moduł neutralny dla domeny.<br /><br /> 0x2: Moduł ma obraz macierzysty.<br /><br /> 0x4: Moduł dynamiczny.<br /><br /> 0x8: Moduł manifestu.|  
|Zastrzeżone1|wygrana:UInt32|Pole zarezerwowane.|  
|Ścieżka modułuILPath|wygrać:UnicodeString|Ścieżka obrazu MSIL dla modułu lub nazwa modułu dynamicznego, jeśli jest to zestaw dynamiczny (zakończone z wartością null).|  
|Ścieżka modułu|wygrać:UnicodeString|Ścieżka obrazu macierzystego modułu, jeśli jest obecny (zakończone z wartością null).|  
|ClrInstanceID (ida)|wygrana:UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  

## <a name="module-range-events"></a>Zdarzenia zakresu modułów
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podbijaniu wydarzenia|Wydarzenie|Poziom|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Informacje (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Informacje (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Informacje (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Wydarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|To zdarzenie jest obecne, jeśli załadowany obraz generatora obrazów natywnych (NGen) został zoptymalizowany za pomocą funkcji IBC i zawiera informacje o gorących sekcjach obrazu NGen.|  
|`ModuleRangeDCStart`|160|Zdarzenie `ModuleRange` wystrzelone na początku wybiegiem.|  
|`ModuleRangeDCEnd`|161|Zdarzenie `ModuleRange` wystrzelone pod koniec spływu.|  
  
 W poniższej tabeli przedstawiono dane zdarzeń.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID (ida)|wygrana:UInt16|Jednoznacznie identyfikuje określone wystąpienie CLR w procesie, jeśli wiele wystąpień CLR są ładowane.|  
|Identyfikator modułu|wygrana:UInt64|Identyfikuje zestaw, do którego należy ten moduł.|  
|ZakresZaczynać|wygrana:UInt32|Przesunięcie w module, który reprezentuje początek zakresu dla określonego typu zakresu.|  
|Rozmiar zasięgu|wygrana:UInt32|Rozmiar określonego zakresu w bajtach.|  
|Typ zakresu|wygrana:UInt32|Pojedyncza wartość, 0x4, do reprezentowania zakresów Zimny IBC. To pole może reprezentować więcej wartości w przyszłości.|  
|Rozmiar zakresu1|wygrana:UInt32|0 oznacza złe dane.|  
|ZakresPowierzchnie2|wygrać:UnicodeString||  
  
### <a name="remarks"></a>Uwagi  
 Jeśli załadowany obraz NGen w procesie .NET Framework został `ModuleRange` zoptymalizowany za pomocą funkcji IBC, zdarzenie zawierające gorące `moduleID` `ClrInstanceID`zakresy obrazu NGen jest rejestrowane wraz z jego i .  Jeśli obraz NGen nie jest zoptymalizowany za pomocą ibc, to zdarzenie nie jest rejestrowane. Aby określić nazwę modułu, to zdarzenie musi być zestawione ze zdarzeniami ETW obciążenia modułu.  
  
 Rozmiar ładunku dla tego zdarzenia jest zmienny; pole `Count` wskazuje liczbę przesunięć zakresu zawartych w zdarzeniu.  To zdarzenie musi zostać posortowane ze zdarzeniem systemu Windows `IStart` w celu określenia rzeczywistych zakresów. Zdarzenie Obciążenie obrazu systemu Windows jest rejestrowane przy każdym załadowaniu obrazu i zawiera adres wirtualny załadowanego obrazu.  
  
 Zdarzenia zakresu modułu są uruchamiane na dowolnym poziomie ETW większym lub równym 4 i są klasyfikowane jako zdarzenia informacyjne.  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia ETW CLR](clr-etw-events.md)
