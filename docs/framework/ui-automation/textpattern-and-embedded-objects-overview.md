---
title: TextPattern i obiekty osadzone — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: 7a3338a08d06320acdc2acb0647bc91541448d7d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201066"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern i obiekty osadzone — omówienie
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 To omówienie zawiera opis sposobu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uwidaczniania obiektów osadzonych lub elementów podrzędnych w obrębie dokumentu lub kontenera tekstu.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obiekcie osadzonym jest dowolnym elementem, który ma nietekstowe granice, na przykład typ obrazu, hiperłącza, tabeli lub dokumentu, taki jak arkusz kalkulacyjny programu Microsoft Excel lub plik Microsoft Windows Media. Różni się to od standardowej definicji, w której element jest tworzony w jednej aplikacji, osadzony lub połączony w innej. Czy obiekt może być edytowany w oryginalnej aplikacji jest nieistotny w kontekście [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Obiekty osadzone i drzewo automatyzacji interfejsu użytkownika  
 Obiekty osadzone są traktowane jako pojedyncze elementy w widoku kontroli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Są one widoczne jako elementy podrzędne kontenera tekstu, dzięki czemu można uzyskać do nich dostęp za pomocą tego samego modelu co inne kontrolki w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 ![Osadzona tabela z obrazem w kontenerze tekstu](./media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Przykład kontenera tekstowego z osadzonymi obiektami tabeli, obrazu i hiperłącza  
  
 ![Widok zawartości dla poprzedniego przykładu](./media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Przykład widoku zawartości dla części poprzedniego kontenera tekstu  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Uwidacznianie obiektów osadzonych przy użyciu TextPattern i TextPatternRange  
 Używane w połączeniu z <xref:System.Windows.Automation.TextPattern> klasą wzorca kontroli i <xref:System.Windows.Automation.Text.TextPatternRange> klasy uwidaczniają metody i właściwości, które ułatwiają nawigację i wykonywanie zapytań dotyczących osadzonych obiektów.  
  
 Zawartość tekstowa (lub tekst wewnętrzny) kontenera tekstu i osadzonego obiektu, takiego jak hiperłącze lub komórka tabeli, jest udostępniana jako pojedynczy, ciągły strumień tekstowy w widoku kontrolki i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa; granice obiektów są ignorowane. Jeśli klient automatyzacji interfejsu użytkownika Pobiera tekst służący do przeszukiwania, interpretacji lub analizy w jakiś sposób, zakres tekstu należy sprawdzać pod kątem specjalnych przypadków, takich jak tabela z zawartością tekstową lub innymi osadzonymi obiektami. Można to osiągnąć, wywołując <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> do uzyskania <xref:System.Windows.Automation.AutomationElement> dla każdego osadzonego obiektu, a następnie wywołując <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> do uzyskania zakresu tekstu dla każdego elementu. Jest to wykonywane cyklicznie, dopóki cała zawartość tekstowa nie zostanie pobrana.  
  
 ![Zakresy tekstu łączone przez obiekty osadzone.](./media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Przykładowy strumień tekstowy z obiektami osadzonymi i zakresem ich zakresu  
  
 Gdy konieczne jest przechodzenie zawartości zakresu tekstu, seria kroków jest uwzględniana w tle, aby <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> Metoda została pomyślnie wykonana.  
  
1. Zakres tekstu jest znormalizowany; oznacza to, że zakres tekstu jest zwijany do zakresu degeneracji w <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> punkcie końcowym, co sprawia, że <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punkt końcowy jest zbędny. Ten krok jest niezbędny do usunięcia niejednoznaczności w sytuacjach, gdy zakres tekstu rozciąga się na <xref:System.Windows.Automation.Text.TextUnit> granice: na przykład, `{The URL https://www.microsoft.com is embedded in text` gdzie "{" i "}" to punkty końcowe zakresu tekstu.  
  
2. Zakres wyników jest przenoszony do tyłu na <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> początku żądanej <xref:System.Windows.Automation.Text.TextUnit> granicy.  
  
3. Zakres jest przenoszony do przodu lub do tyłu w kolejności <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> przez żądaną liczbę <xref:System.Windows.Automation.Text.TextUnit> granic.  
  
4. Zakres jest następnie rozwinięty z stanu degeneracji przez przeniesienie <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktu końcowego przez jedną żądaną <xref:System.Windows.Automation.Text.TextUnit> granicę.  
  
 ![Dopasowanie zakresu według przenoszenia & ExpandToEnclosingUnit](./media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Przykłady sposobu, w jaki zakres tekstu jest dostosowywany dla operacji Move () i ExpandToEnclosingUnit ()  
  
<a name="Common_Scenarios"></a>
## <a name="common-scenarios"></a>Typowe scenariusze  
 W poniższych sekcjach znajdują się przykłady najczęstszych scenariuszy obejmujących obiekty osadzone.  
  
 Legenda dla przedstawionych przykładów:  
  
 { =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Hyperlink  

**Przykład 1 — zakres tekstu, który zawiera osadzony hiperlink tekstowy**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg `The URL https://www.microsoft.com is embedded in text` .|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca wewnętrzna <xref:System.Windows.Automation.AutomationElement> , która zawiera zakres tekstu, w tym przypadku, <xref:System.Windows.Automation.AutomationElement> która reprezentuje dostawcę tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentującą kontrolkę Hyperlink.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany przez poprzednią `GetChildren` metodę.|Zwraca zakres, który reprezentuje `https://www.microsoft.com` .|  
  
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
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca wewnętrzna <xref:System.Windows.Automation.AutomationElement> , która zawiera zakres tekstu, w tym przypadku, <xref:System.Windows.Automation.AutomationElement> która reprezentuje dostawcę tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>z parametrami (TextUnit. Word, 1).|Przenosi zakres tekstu do "http", ponieważ tekst hiperlinku składa się z pojedynczych wyrazów. W takim przypadku hiperlink nie jest traktowany jako pojedynczy obiekt.<br /><br /> Adres URL {[http]} jest osadzony w tekście.|  
  
<a name="Image"></a>
### <a name="image"></a>Obraz  
 **Przykład 1 — zakres tekstu, który zawiera osadzony obraz**  
  
 { ![Osadzony obraz](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") obrazu jest osadzony w tekście}.  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "element jest osadzony w tekście". W strumieniu tekstowym nie można oczekiwać żadnego tekstu ALTERNATYWNEgo skojarzonego z obrazem.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca wewnętrzna <xref:System.Windows.Automation.AutomationElement> , która zawiera zakres tekstu, w tym przypadku, <xref:System.Windows.Automation.AutomationElement> która reprezentuje dostawcę tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentującą kontrolkę obrazu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany przez poprzednią <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> metodę.|Zwraca zakres degeneracji reprezentujący "![przykład obrazu osadzonego](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Przykład 2 — zakres tekstu, który częściowo obejmuje zawartość kontenera tekstu. Kontener tekstu ma osadzony obraz, który nie jest częścią zakresu tekstu.**  
  
 {Obraz} ![Przykład osadzonego obrazu](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") jest osadzony w tekście.  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "obraz".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca wewnętrzna <xref:System.Windows.Automation.AutomationElement> , która zawiera zakres tekstu, w tym przypadku, <xref:System.Windows.Automation.AutomationElement> która reprezentuje dostawcę tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>z parametrami (TextUnit. Word, 1).|Przenosi zakres tekstu do "is". Ze względu na to, że tylko tekstowe obiekty osadzone są uważane za część strumienia tekstu, obraz w tym przykładzie nie ma wpływu na przeniesienie ani jego wartość zwracaną (1 w tym przypadku).|  
  
<a name="Table"></a>
### <a name="table"></a>Tabela  
  
### <a name="table-used-for-examples"></a>Tabela używana do przykładów  
  
|Komórka z obrazem|Komórka z tekstem|  
|---------------------|--------------------|  
|![Przykład osadzonego obrazu](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Przykład obrazu osadzonego 2](./media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|Y|  
|![Przykład osadzonego obrazu 3](./media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Obraz Z|Z|  
  
 **Przykład 1 — pobieranie kontenera tekstu z zawartości komórki.**  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>z parametrami (0, 0)|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentowanie zawartości komórki tabeli. w tym przypadku element jest formantem tekstowym.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany przez poprzednią `GetItem` metodę.|Zwraca zakres, który rozciąga się na ![przykład obrazu osadzonego](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")obrazu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>dla obiektu zwróconego przez poprzednią `RangeFromChild` metodę.|Zwraca wartość <xref:System.Windows.Automation.AutomationElement> reprezentującą komórkę tabeli. w tym przypadku element jest formantem tekstowym, który obsługuje TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>dla obiektu zwróconego przez poprzednią `GetEnclosingElement` metodę.|Zwraca wartość <xref:System.Windows.Automation.AutomationElement> reprezentującą tabelę.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>dla obiektu zwróconego przez poprzednią `GetEnclosingElement` metodę.|Zwraca wartość <xref:System.Windows.Automation.AutomationElement> reprezentującą sam dostawcę tekstu.|  
  
 **Przykład 2 — pobieranie zawartości tekstowej komórki.**  
  
|Wywołana metoda|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>z parametrami (1, 1).|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentowanie zawartości komórki tabeli. w tym przypadku element jest formantem tekstowym.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany przez poprzednią `GetItem` metodę.|Zwraca wartość "Y".|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika](access-embedded-objects-using-ui-automation.md)
- [Udostępnianie zawartości tabel za pomocą automatyzacji interfejsu użytkownika](expose-the-content-of-a-table-using-ui-automation.md)
- [Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika](traverse-text-using-ui-automation.md)
- [Przykład wyszukiwania i wybierania TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
