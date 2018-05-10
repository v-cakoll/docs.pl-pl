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
manager: markl
ms.openlocfilehash: ab732ffedfbe05b1b246d8d8eef1c374e223eb39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern i obiekty osadzone — omówienie
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten przegląd zawiera opis sposobu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ujawnia osadzonych obiektów lub elementów podrzędnych w dokumencie tekstowym lub kontenera.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] osadzonego obiektu jest dowolny element, który ma inną niż tekstowa granice; na przykład obrazu, hiperłącza, tabeli lub dokumentu wpisz na przykład [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] arkusz kalkulacyjny lub [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] pliku. To różni się od standardowej definicji, gdzie element został utworzony w jednej aplikacji i osadzony czy połączony w innym. Określa, czy obiekt może być edytowany w oryginalnej aplikacji nie ma znaczenia w kontekście [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Osadzone obiekty i drzewa automatyzacji interfejsu użytkownika  
 Osadzone obiekty są traktowane jako pojedyncze elementy w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Są one widoczne jako elementy podrzędne pola tekstowego, dzięki czemu są one dostępne za pośrednictwem takie same modelu innych formantów w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 ![Osadzony tabeli z obrazu w kontenerze tekstu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Przykład kontenera tekstu z tabeli, obrazu i hiperłącze osadzone obiekty  
  
 ![Widok dla poprzedniego przykładu zawartości](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Przykładowy widok zawartości dla części poprzedniego kontenera tekstu  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Udostępnianie obiektów osadzonych przy użyciu TextPattern i TextPatternRange  
 Używane w połączeniu, <xref:System.Windows.Automation.TextPattern> kontrolować klasy wzorca i <xref:System.Windows.Automation.Text.TextPatternRange> klasy ujawniać metod i właściwości, które ułatwiają nawigacji i badania osadzonych obiektów.  
  
 Zawartość tekstową (lub tekst wewnętrzny) kontenerze tekstu i osadzonego, takich jak komórki hiperłącze lub tabeli jest ujawniona jako strumień jednej, ciągłe tekst w widoku kontrolki i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa; obiekt granice są ignorowane. Jeśli klient automatyzacji interfejsu użytkownika pobiera tekst na potrzeby reciting interpretowanie i analizowanie danych w sposób, zakres tekstu mają być wyszukiwane w szczególnych przypadkach, takich jak tabelę z tekstowej zawartości lub inne obiekty osadzone. Można to osiągnąć poprzez wywołanie <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> uzyskanie <xref:System.Windows.Automation.AutomationElement> dla każdego osadzonego obiektu, a następnie wywołując <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> uzyskanie zakresu tekstu dla każdego elementu. W tym celu rekursywnie do momentu pobrania całej zawartości tekstowej.  
  
 ![Zakresy tekstu, objęte osadzonych obiektów. ] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Przykład strumienia tekstu osadzonych obiektów i ich zakresy zakresu  
  
 Gdy jest konieczne przechodzenie przez zawartość zakres tekstu, serii kroków są zaangażowane w tle, aby <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> metodę, aby zostać pomyślnie uruchomiony.  
  
1.  Zakres tekstu jest znormalizowany; oznacza to, że zakres tekstu jest zwinięty degeneracji zakres na <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> punktu końcowego, co sprawia, że <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> zbędny punktu końcowego. Ten krok jest niezbędny usunąć niejednoznaczności w sytuacjach, gdy zakres tekstu obejmuje <xref:System.Windows.Automation.Text.TextUnit> granice: na przykład "{U} RL [ http://www.microsoft.com ](http://www.microsoft.com) jest osadzony w tekście" gdzie "{" i "}" są punkty końcowe zakresu tekstu.  
  
2.  Wynikowy zakres jest przenoszony do tyłu <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> na początku żądany <xref:System.Windows.Automation.Text.TextUnit> granic.  
  
3.  Zakres zostanie przeniesiona do przodu i do tyłu w <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> przez żądaną liczbę <xref:System.Windows.Automation.Text.TextUnit> granic.  
  
4.  Zakres jest rozszerzana ze stanu degeneracji zakresu przenosząc <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktu końcowego o jeden żądany <xref:System.Windows.Automation.Text.TextUnit> granic.  
  
 ![Zakres dostosowania Przenieś & ExpandToEnclosingUnit](../../../docs/framework/ui-automation/media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Przykłady sposobu zakres tekstu jest uwzględniany Move() i ExpandToEnclosingUnit()  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Typowe scenariusze  
 Poniższe sekcje stanowią przykłady typowych scenariuszy dotyczących osadzonych obiektów.  
  
 Legenda Przykłady pokazano:  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
<a name="Hyperlink"></a>   
### <a name="hyperlink"></a>Hyperlink  
 **Przykład 1 - zakres tekstu, który zawiera hiperłącza osadzone tekstu**  
  
 {Adres URL [ http://www.microsoft.com ](http://www.microsoft.com) jest osadzony w tekście}.  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "adres URL http://www.microsoft.com jest osadzony w tekście".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej wewnętrzną funkcją <xref:System.Windows.Automation.AutomationElement> który umieszcza zakres tekstu; w takim przypadku <xref:System.Windows.Automation.AutomationElement> reprezentujący samego dostawcy tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący kontrolki hiperlinku.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> gdzie <xref:System.Windows.Automation.AutomationElement> jest obiektem zwrócony przez poprzednie `GetChildren` metody.|Zwraca zakres, który reprezentuje "http://www.microsoft.com".|  
  
 **Przykład 2 - zakres tekstu, obejmującej częściowo hyperlink osadzonych tekstu**  
  
 Http://{[www adresu URL]} jest osadzony w tekście.  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej wewnętrzną funkcją <xref:System.Windows.Automation.AutomationElement> który umieszcza zakres tekstu; w takim przypadku kontrolować hiperłącza.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca `null` ponieważ zakres tekstu nie obejmować cały ciąg adresu URL.|  
  
 **Przykład 3 - zakres tekstu, obejmującej częściowo zawartości kontenera tekstowego. Kontener tekst ma hiperłącze osadzone tekstu, które nie jest częścią zakres tekstu.**  
  
 {URL} [ http://www.microsoft.com ](http://www.microsoft.com) jest osadzony w tekście.  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej wewnętrzną funkcją <xref:System.Windows.Automation.AutomationElement> który umieszcza zakres tekstu; w takim przypadku <xref:System.Windows.Automation.AutomationElement> reprezentujący samego dostawcy tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> z parametrami (TextUnit.Word, 1).|Przenosi zakres zakres tekstu do "http", ponieważ tekst hiperłącza składa się z poszczególnych wyrazów. W takim przypadku hiperłącza nie jest traktowana jako pojedynczego obiektu.<br /><br /> Adres URL {[http]} jest osadzony w tekście.|  
  
<a name="Image"></a>   
### <a name="image"></a>Obraz  
 **Przykład 1 - zakres tekstu, który zawiera osadzony obraz**  
  
 {Obraz ![przykład osadzonego obrazu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") jest osadzony w tekście}.  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "jest osadzony w tekście". Tekst alternatywny skojarzony z obrazem nie oczekiwano mają zostać uwzględnione w strumieniu tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej wewnętrzną funkcją <xref:System.Windows.Automation.AutomationElement> który umieszcza zakres tekstu; w takim przypadku <xref:System.Windows.Automation.AutomationElement> reprezentujący samego dostawcy tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący obraz formantu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> gdzie <xref:System.Windows.Automation.AutomationElement> jest obiektem zwrócony przez poprzednie <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> metody.|Zwraca degeneracji zakresu, który reprezentuje "![przykład osadzonego obrazu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Przykład 2 - zakres tekstu, obejmującej częściowo zawartości kontenera tekstowego. Kontener tekst ma osadzonego obrazu, który nie jest częścią zakres tekstu.**  
  
 {Obraz} ![Przykład osadzonego obrazu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") jest osadzony w tekście.  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "Obrazu".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej wewnętrzną funkcją <xref:System.Windows.Automation.AutomationElement> który umieszcza zakres tekstu; w takim przypadku <xref:System.Windows.Automation.AutomationElement> reprezentujący samego dostawcy tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> z parametrami (TextUnit.Word, 1).|Przenosi zakres zakres tekstu do "jest". Ponieważ tylko tekstowy osadzonych obiektów są traktowane jako część strumienia tekstu, obrazów, w tym przykładzie nie wpływa na przenoszenia lub jego wartości zwracanej (1, w tym przypadku).|  
  
<a name="Table"></a>   
### <a name="table"></a>tabela  
  
### <a name="table-used-for-examples"></a>Tabela używana przykłady  
  
|Komórki z obrazem|Komórki z tekstem|  
|---------------------|--------------------|  
|![Osadzony obraz przykład](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Osadzony obraz przykład 2](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|T|  
|![Osadzony obraz przykład 3](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Obraz Z|Z|  
  
 **Przykład 1 — pobieranie kontenera tekst z zawartości komórki.**  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> z parametrami (0,0)|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący zawartość komórki tabeli; w takim przypadku element jest kontrolki tekstu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> gdzie <xref:System.Windows.Automation.AutomationElement> jest obiektem zwrócony przez poprzednie `GetItem` metody.|Zwraca zakresu, który obejmuje obraz ![przykład osadzonego obrazu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> dla obiekt zwrócony przez poprzednie `RangeFromChild` metody.|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący komórki tabeli; w takim przypadku element jest formant tekst, który obsługuje klasy TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> dla obiekt zwrócony przez poprzednie `GetEnclosingElement` metody.|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący tabeli.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> dla obiekt zwrócony przez poprzednie `GetEnclosingElement` metody.|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący samego dostawcy tekstu.|  
  
 **Przykład 2 — pobieranie zawartości tekstowej komórki.**  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> z parametrami (1,1).|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentujący zawartość komórki tabeli; w takim przypadku element jest kontrolki tekstu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> gdzie <xref:System.Windows.Automation.AutomationElement> jest obiektem zwrócony przez poprzednie `GetItem` metody.|Zwraca wartość "Y".|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.TextPattern>  
 <xref:System.Windows.Automation.Text.TextPatternRange>  
 <xref:System.Windows.Automation.Provider.ITextProvider>  
 <xref:System.Windows.Automation.Provider.ITextRangeProvider>  
 [Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)  
 [Udostępnianie zawartości tabel za pomocą automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/expose-the-content-of-a-table-using-ui-automation.md)  
 [Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/traverse-text-using-ui-automation.md)  
 [TextPattern wyszukiwania i przykładowe zaznaczenia](http://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)
