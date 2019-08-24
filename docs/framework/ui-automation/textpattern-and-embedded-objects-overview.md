---
title: TextPattern i obiekty osadzone — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: b7b94b01f737d10b035d85ee938829e14f3af43b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69987631"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern i obiekty osadzone — omówienie
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 To omówienie zawiera opis [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sposobu uwidaczniania obiektów osadzonych lub elementów podrzędnych w obrębie dokumentu lub kontenera tekstu.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obiekcie osadzonym jest dowolnym elementem, który ma nietekstowe granice, na przykład typ obrazu, hiperłącza, tabeli lub dokumentu, taki [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] jak arkusz kalkulacyjny lub [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] plik. Różni się to od standardowej definicji, w której element jest tworzony w jednej aplikacji, osadzony lub połączony w innej. Czy obiekt może być edytowany w oryginalnej aplikacji jest nieistotny w kontekście [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Obiekty osadzone i drzewo automatyzacji interfejsu użytkownika  
 Obiekty osadzone są traktowane jako pojedyncze elementy w widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontroli drzewa. Są one widoczne jako elementy podrzędne kontenera tekstu, dzięki czemu można uzyskać do nich dostęp za pomocą tego samego modelu co inne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]kontrolki w.  
  
 ![Osadzona tabela z obrazem w kontenerze tekstu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Przykład kontenera tekstowego z osadzonymi obiektami tabeli, obrazu i hiperłącza  
  
 ![Widok zawartości dla poprzedniego przykładu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Przykład widoku zawartości dla części poprzedniego kontenera tekstu  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Uwidacznianie obiektów osadzonych przy użyciu TextPattern i TextPatternRange  
 Używane w połączeniu z <xref:System.Windows.Automation.TextPattern> klasą wzorca kontroli <xref:System.Windows.Automation.Text.TextPatternRange> i klasy uwidaczniają metody i właściwości, które ułatwiają nawigację i wykonywanie zapytań dotyczących osadzonych obiektów.  
  
 Zawartość tekstowa (lub tekst wewnętrzny) kontenera tekstu i osadzonego obiektu, takiego jak hiperłącze lub komórka tabeli, jest udostępniana jako pojedynczy, ciągły strumień tekstowy w widoku kontrolki i widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawartości drzewa; granice obiektów są ignorowane. Jeśli klient automatyzacji interfejsu użytkownika Pobiera tekst służący do przeszukiwania, interpretacji lub analizy w jakiś sposób, zakres tekstu należy sprawdzać pod kątem specjalnych przypadków, takich jak tabela z zawartością tekstową lub innymi osadzonymi obiektami. Można to osiągnąć, wywołując <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> do <xref:System.Windows.Automation.AutomationElement> uzyskania dla każdego osadzonego obiektu, a następnie wywołując <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> do uzyskania zakresu tekstu dla każdego elementu. Jest to wykonywane cyklicznie, dopóki cała zawartość tekstowa nie zostanie pobrana.  
  
 ![Zakresy tekstu łączone przez obiekty osadzone.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Przykładowy strumień tekstowy z obiektami osadzonymi i zakresem ich zakresu  
  
 Gdy konieczne jest przechodzenie zawartości zakresu tekstu, seria kroków jest uwzględniana w <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> tle, aby metoda została pomyślnie wykonana.  
  
1. Zakres tekstu jest znormalizowany; oznacza to, że zakres tekstu jest zwijany do zakresu degeneracji w <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> punkcie końcowym, co <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> sprawia, że punkt końcowy jest zbędny. Ten krok jest niezbędny do usunięcia niejednoznaczności w sytuacjach, gdy zakres tekstu <xref:System.Windows.Automation.Text.TextUnit> rozciąga się na granice: `{The URL https://www.microsoft.com is embedded in text` na przykład, gdzie "{" i "}" to punkty końcowe zakresu tekstu.  
  
2. Zakres wyników jest przenoszony do tyłu <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> na początku żądanej <xref:System.Windows.Automation.Text.TextUnit> granicy.  
  
3. Zakres jest przenoszony do przodu lub do tyłu <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> w kolejności przez żądaną <xref:System.Windows.Automation.Text.TextUnit> liczbę granic.  
  
4. Zakres jest następnie rozwinięty z stanu degeneracji przez przeniesienie <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktu końcowego przez jedną żądaną <xref:System.Windows.Automation.Text.TextUnit> granicę.  
  
 ![Dopasowanie zakresu według przenoszenia & ExpandToEnclosingUnit](../../../docs/framework/ui-automation/media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Przykłady sposobu, w jaki zakres tekstu jest dostosowywany dla operacji Move () i ExpandToEnclosingUnit ()  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Typowe scenariusze  
 W poniższych sekcjach znajdują się przykłady najczęstszych scenariuszy obejmujących obiekty osadzone.  
  
 Legenda dla przedstawionych przykładów:  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Hyperlink  

**Przykład 1 — zakres tekstu, który zawiera osadzony hiperlink tekstowy**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg `The URL https://www.microsoft.com is embedded in text`.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca wewnętrzna <xref:System.Windows.Automation.AutomationElement> , która zawiera zakres tekstu, w tym przypadku <xref:System.Windows.Automation.AutomationElement> , która reprezentuje dostawcę tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|<xref:System.Windows.Automation.AutomationElement> Zwraca reprezentującą kontrolkę Hyperlink.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany przez poprzednią `GetChildren` metodę.|Zwraca zakres reprezentujący "https://www.microsoft.com".|  
  
 **Przykład 2 — zakres tekstu, który częściowo obejmuje osadzone Hiperłącze tekstowe**  
  
 Adres URL `https://{[www]}` jest osadzony w tekście.  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca wewnętrzna <xref:System.Windows.Automation.AutomationElement> , która znajduje się w zakresie tekstu; w tym przypadku kontrolki Hyperlink.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca `null` , ponieważ zakres tekstu nie obejmuje całego ciągu adresu URL.|  
  
**Przykład 3 — zakres tekstu, który częściowo obejmuje zawartość kontenera tekstu. Kontener tekstu ma osadzone Hiperłącze tekstowe, które nie jest częścią zakresu tekstu.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "adres URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca wewnętrzna <xref:System.Windows.Automation.AutomationElement> , która zawiera zakres tekstu, w tym przypadku <xref:System.Windows.Automation.AutomationElement> , która reprezentuje dostawcę tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>z parametrami (TextUnit. Word, 1).|Przenosi zakres tekstu do "http", ponieważ tekst hiperlinku składa się z pojedynczych wyrazów. W takim przypadku hiperlink nie jest traktowany jako pojedynczy obiekt.<br /><br /> Adres URL {[http]} jest osadzony w tekście.|  
  
<a name="Image"></a>   
### <a name="image"></a>Obraz  
 **Przykład 1 — zakres tekstu, który zawiera osadzony obraz**  
  
 {Osadzony ![obraz obrazu przykład](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") jest osadzony w tekście}.  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "element jest osadzony w tekście". W strumieniu tekstowym nie można oczekiwać żadnego tekstu ALTERNATYWNEgo skojarzonego z obrazem.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca wewnętrzna <xref:System.Windows.Automation.AutomationElement> , która zawiera zakres tekstu, w tym przypadku <xref:System.Windows.Automation.AutomationElement> , która reprezentuje dostawcę tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|<xref:System.Windows.Automation.AutomationElement> Zwraca reprezentującą kontrolkę obrazu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany przez poprzednią <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> metodę.|Zwraca zakres degeneracji reprezentujący ciąg "![przykład obrazu osadzonego]"(../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Przykład 2 — zakres tekstu, który częściowo obejmuje zawartość kontenera tekstu. Kontener tekstu ma osadzony obraz, który nie jest częścią zakresu tekstu.**  
  
 {Obraz} ![Przykład osadzonego obrazu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") jest osadzony w tekście.  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "obraz".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca wewnętrzna <xref:System.Windows.Automation.AutomationElement> , która zawiera zakres tekstu, w tym przypadku <xref:System.Windows.Automation.AutomationElement> , która reprezentuje dostawcę tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>z parametrami (TextUnit. Word, 1).|Przenosi zakres tekstu do "is". Ze względu na to, że tylko tekstowe obiekty osadzone są uważane za część strumienia tekstu, obraz w tym przykładzie nie ma wpływu na przeniesienie ani jego wartość zwracaną (1 w tym przypadku).|  
  
<a name="Table"></a>   
### <a name="table"></a>tabela  
  
### <a name="table-used-for-examples"></a>Tabela używana do przykładów  
  
|Komórka z obrazem|Komórka z tekstem|  
|---------------------|--------------------|  
|![Przykład osadzonego obrazu](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Przykład obrazu osadzonego 2](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|T|  
|![Przykład osadzonego obrazu 3](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Obraz Z|Z|  
  
 **Przykład 1 — pobieranie kontenera tekstu z zawartości komórki.**  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>z parametrami (0, 0)|<xref:System.Windows.Automation.AutomationElement> Zwraca reprezentowanie zawartości komórki tabeli. w tym przypadku element jest formantem tekstowym.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany przez poprzednią `GetItem` metodę.|Zwraca zakres, który obejmuje ![przykład]obrazu osadzony obraz(../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>dla obiektu zwróconego przez poprzednią `RangeFromChild` metodę.|Zwraca wartość <xref:System.Windows.Automation.AutomationElement> reprezentującą komórkę tabeli. w tym przypadku element jest formantem tekstowym, który obsługuje TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>dla obiektu zwróconego przez poprzednią `GetEnclosingElement` metodę.|Zwraca wartość <xref:System.Windows.Automation.AutomationElement> reprezentującą tabelę.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>dla obiektu zwróconego przez poprzednią `GetEnclosingElement` metodę.|<xref:System.Windows.Automation.AutomationElement> Zwraca wartość reprezentującą sam dostawcę tekstu.|  
  
 **Przykład 2 — pobieranie zawartości tekstowej komórki.**  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>z parametrami (1, 1).|<xref:System.Windows.Automation.AutomationElement> Zwraca reprezentowanie zawartości komórki tabeli. w tym przypadku element jest formantem tekstowym.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany przez poprzednią `GetItem` metodę.|Zwraca wartość "Y".|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)
- [Udostępnianie zawartości tabel za pomocą automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/expose-the-content-of-a-table-using-ui-automation.md)
- [Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/traverse-text-using-ui-automation.md)
- [Przykład wyszukiwania i wybierania TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
