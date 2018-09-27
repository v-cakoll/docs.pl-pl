---
title: TextPattern i obiekty osadzone — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: c3904ad60df3d9d7ce2b58d5911e4e19a2ebb7e3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193908"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern i obiekty osadzone — omówienie
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten przegląd zawiera opis sposobu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ujawnia osadzonych obiektów lub elementy podrzędne, w ramach kontenera lub dokument tekstowy.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] osadzonego obiektu jest dowolnego elementu, który ma niż tekstowa granice; na przykład obraz, hiperłącza, tabela lub dokumentu wpisz na przykład [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] arkusz kalkulacyjny lub [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] pliku. To różni się od standardowej rozdzielczości, gdzie element jest utworzone w jednej aplikacji i osadzone lub połączone w innym. Czy obiekt może być edytowana w oryginalnej aplikacji nie ma znaczenia w kontekście [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Osadzone obiekty i drzewa automatyzacji interfejsu użytkownika  
 Osadzone obiekty są traktowane jako pojedyncze elementy w widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Są one widoczne jako elementy podrzędne pola tekstowego, dzięki czemu są one dostępne za pośrednictwem takie same modelu innych formantów w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 ![Osadzone tabeli przy użyciu obrazu w kontenerze tekstu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Przykładowy kontener tekstu z tabeli, obrazów i hiperłączy osadzone obiekty  
  
 ![Widok dla poprzedniego przykładu zawartości](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Przykładowy widok zawartości przez pewną część poprzedniego kontenerze tekstu  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Udostępnianie obiektów osadzonych przy użyciu TextPattern i TextPatternRange  
 Używany w połączeniu, <xref:System.Windows.Automation.TextPattern> kontrolować wzorzec klasy i <xref:System.Windows.Automation.Text.TextPatternRange> ujawnić klas, metod i właściwości, które ułatwiają nawigacji i wysyłania zapytań do obiektów osadzonych.  
  
 Zawartości tekstowej (lub tekst wewnętrzny) kontenerze tekstu i osadzonego obiektu, takie jak hiperłącza lub komórki tabeli, jest widoczna jako strumień pojedynczego, zapewniająca ciągłą tekst w widoku formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa; obiekt granice są ignorowane. Jeśli klient automatyzacji interfejsu użytkownika pobiera tekst na potrzeby reciting interpretowanie i analizowanie danych w sposób, zakres tekstu mają być wyszukiwane w szczególnych przypadkach, takich jak tabelę z tekstowej zawartości lub inne obiekty osadzone. Można to zrobić, wywołując <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> uzyskać <xref:System.Windows.Automation.AutomationElement> dla wersji embedded każdego obiektu, a następnie wywołując <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> uzyskanie zakresu tekstu dla każdego elementu. Jest to realizowane cyklicznie, do momentu pobrania całej zawartości tekstowej.  
  
 ![Zakresy tekstu, objęte z osadzonych obiektów. ](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Przykład strumienia tekstu przy użyciu osadzonych obiektów i ich zakresy zakresu  
  
 Gdy jest to konieczne przechodzenie przez zawartość zakres tekstu, szereg kroków biorących udział w tle, aby <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> pomyślnie wykonać metodę.  
  
1.  Zakres tekstu jest znormalizować; oznacza to, że zakres tekstu jest zwinięte do wymiaru degeneracji zakresu na <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> punktu końcowego, co sprawia, że <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> zbędny punktu końcowego. Ten krok jest niezbędny usunąć niejednoznaczność w sytuacjach, w którym obejmuje zakres tekstu <xref:System.Windows.Automation.Text.TextUnit> granice: na przykład "{N} RL [ http://www.microsoft.com ](https://www.microsoft.com) jest osadzony w tekście" gdzie "{" i "}" są wartościami tekstowymi punkty końcowe zakresu.  
  
2.  Wynikowy zakres zostaje przeniesiony do tyłu <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> na początku żądany <xref:System.Windows.Automation.Text.TextUnit> granic.  
  
3.  Zakres jest przenoszony do przodu lub Wstecz w <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> , żądana liczba <xref:System.Windows.Automation.Text.TextUnit> granic.  
  
4.  Zakres jest rozszerzany ze stanu wymiaru degeneracji zakresu przez przesunięcie <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktu końcowego za pomocą jednej żądane <xref:System.Windows.Automation.Text.TextUnit> granic.  
  
 ![Zakres korekt przez przeniesienie & ExpandToEnclosingUnit](../../../docs/framework/ui-automation/media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Przykłady jak zakres tekstu jest uwzględniany Move() i ExpandToEnclosingUnit()  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Typowe scenariusze  
 Poniższe sekcje zawierają przykłady typowych scenariuszy, które obejmują osadzonych obiektów.  
  
 Legenda przykładów:  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
<a name="Hyperlink"></a>   
### <a name="hyperlink"></a>Hyperlink  
 **Przykład 1 - zakres tekstu, który zawiera hiperłącze osadzonego tekstu**  
  
 {Adres URL [ http://www.microsoft.com ](https://www.microsoft.com) jest osadzony w tekście}.  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "adres URL http://www.microsoft.com jest osadzony w tekście".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej wewnętrzną funkcją <xref:System.Windows.Automation.AutomationElement> który otacza zakres tekstu; w takim przypadku <xref:System.Windows.Automation.AutomationElement> reprezentujący dostawcę tekstu sam.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujące kontrolki hiperlinku.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> gdzie <xref:System.Windows.Automation.AutomationElement> to obiekt zwrócony przez poprzednie `GetChildren` metody.|Zwraca zakres, który reprezentuje "http://www.microsoft.com".|  
  
 **Przykład 2 - zakres tekstu, które częściowo obejmuje hiperłącze osadzonego tekstu**  
  
 Adres URL `http://{[www]}` jest osadzony w tekście.  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej wewnętrzną funkcją <xref:System.Windows.Automation.AutomationElement> który otacza zakres tekstu; w takim przypadku kontrolować hiperłącze.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca `null` ponieważ zakres tekstu nie obejmować cały ciąg adresu URL.|  
  
 **Przykład 3 - zakres tekstu, które częściowo obejmuje zawartość kontenerów tekstu. Kontener tekst ma hiperłącze osadzonego tekstu, który nie jest częścią zakresu tekstu.**  
  
 {URL} [ http://www.microsoft.com ](https://www.microsoft.com) jest osadzony w tekście.  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej wewnętrzną funkcją <xref:System.Windows.Automation.AutomationElement> który otacza zakres tekstu; w takim przypadku <xref:System.Windows.Automation.AutomationElement> reprezentujący dostawcę tekstu sam.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> za pomocą parametrów (TextUnit.Word, 1).|Przenosi zakresu zakres tekstu "http", ponieważ tekstem hiperlinku składa się z poszczególnych wyrazów. W tym przypadku hiperłącza nie jest traktowana jako pojedynczy obiekt.<br /><br /> Adres URL {[http]} jest osadzony w tekście.|  
  
<a name="Image"></a>   
### <a name="image"></a>Obraz  
 **Przykład 1 - zakres tekstu, który zawiera osadzony obraz**  
  
 {Obraz ![przykład osadzonego obrazu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") jest osadzony w tekście}.  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "jest osadzony w tekście". Nie można oczekiwać żadnych tekst alternatywny skojarzony z obrazem do uwzględnienia w strumieniu tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej wewnętrzną funkcją <xref:System.Windows.Automation.AutomationElement> który otacza zakres tekstu; w takim przypadku <xref:System.Windows.Automation.AutomationElement> reprezentujący dostawcę tekstu sam.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący kontrolka obrazu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> gdzie <xref:System.Windows.Automation.AutomationElement> to obiekt zwrócony przez poprzednie <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> metody.|Zwraca wymiaru degeneracji zakres, który reprezentuje "![przykład osadzonego obrazu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Przykład 2 - zakres tekstu, które częściowo obejmuje zawartość kontenerów tekstu. Kontener tekst zawiera osadzony obraz, który nie jest częścią zakresu tekstu.**  
  
 {Obraz} ![Przykład osadzonego obrazu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") jest osadzony w tekście.  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "image".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej wewnętrzną funkcją <xref:System.Windows.Automation.AutomationElement> który otacza zakres tekstu; w takim przypadku <xref:System.Windows.Automation.AutomationElement> reprezentujący dostawcę tekstu sam.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> za pomocą parametrów (TextUnit.Word, 1).|Przenosi zakresu zakres tekstu do "is". Ponieważ tylko oparte na tekście obiekty osadzone, są traktowane jako części strumienia tekstu, obrazów, w tym przykładzie nie ma wpływu na przenoszenia lub jego wartość zwracana (1, w tym przypadku).|  
  
<a name="Table"></a>   
### <a name="table"></a>tabela  
  
### <a name="table-used-for-examples"></a>Tabela używana przykłady  
  
|Komórki z obrazem|Komórki z tekstem|  
|---------------------|--------------------|  
|![Osadzony obraz przykład](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Osadzony obraz przykład 2](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|T|  
|![Osadzony obraz w przykładzie 3](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Obraz Z|Z|  
  
 **Przykład 1 — uzyskiwanie kontenerze tekstu zawartość komórki.**  
  
|Metody o nazwie|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> za pomocą parametrów (0,0)|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący zawartość komórki tabeli; w tym przypadku element jest kontrolki tekstu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> gdzie <xref:System.Windows.Automation.AutomationElement> to obiekt zwrócony przez poprzednie `GetItem` metody.|Zwraca zakres, który obejmuje obraz ![przykład osadzonego obrazu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> dla obiektu zwróconego przez poprzednie `RangeFromChild` metody.|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący komórkę tabeli; w tym przypadku element jest kontrolki tekstu, który obsługuje klasy TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> dla obiektu zwróconego przez poprzednie `GetEnclosingElement` metody.|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący tabelę.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> dla obiektu zwróconego przez poprzednie `GetEnclosingElement` metody.|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący dostawcę tekstu sam.|  
  
 **Przykład 2 — pobieranie zawartości tekstowej komórek.**  
  
|Metody o nazwie|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> za pomocą parametrów (1,1).|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący zawartość komórki tabeli; w tym przypadku element jest kontrolki tekstu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> gdzie <xref:System.Windows.Automation.AutomationElement> to obiekt zwrócony przez poprzednie `GetItem` metody.|Zwraca wartość "Y".|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.TextPattern>  
 <xref:System.Windows.Automation.Text.TextPatternRange>  
 <xref:System.Windows.Automation.Provider.ITextProvider>  
 <xref:System.Windows.Automation.Provider.ITextRangeProvider>  
 [Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)  
 [Udostępnianie zawartości tabel za pomocą automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/expose-the-content-of-a-table-using-ui-automation.md)  
 [Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/traverse-text-using-ui-automation.md)  
 [TextPattern wyszukiwania i wybór próbki](https://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)
