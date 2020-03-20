---
title: TextPattern i obiekty osadzone — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: 635c06a03107b33134b015e2643c5281dd86798b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180016"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern i obiekty osadzone — omówienie
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przeglądzie opisano sposób uwidaczniania osadzonych obiektów lub elementów podrzędnych w dokumencie tekstowym lub kontenerze.  
  
 W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obiekcie osadzonym jest dowolny element, który ma granice nietekstowe; na przykład obraz, hiperłącze, tabela lub typ dokumentu, taki jak arkusz kalkulacyjny programu Microsoft Excel lub plik Microsoft Windows Media. Różni się to od standardowej definicji, gdzie element jest tworzony w jednej aplikacji i osadzone lub połączone w innej. To, czy obiekt może być edytowany w oryginalnej aplikacji, nie ma znaczenia w kontekście pliku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Obiekty osadzone i drzewo automatyzacji interfejsu użytkownika  
 Obiekty osadzone są traktowane jako pojedyncze elementy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w widoku kontrolnym drzewa. Są one widoczne jako elementy podrzędne kontenera tekstu, dzięki czemu można [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]uzyskać do nich dostęp za pośrednictwem tego samego modelu, co inne formanty w programie .  
  
 ![Osadzona tabela z obrazem w kontenerze tekstu](./media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Przykład kontenera tekstu z osadzonymi obiektami tabeli, obrazów i hiperłącza  
  
 ![Widok zawartości dla poprzedniego przykładu](./media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Przykład widoku zawartości dla części poprzedniego kontenera tekstu  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Uwidacznianie obiektów osadzonych za pomocą textpattern i TextPatternRange  
 Używane w połączeniu, klasy wzorca <xref:System.Windows.Automation.TextPattern> kontroli i <xref:System.Windows.Automation.Text.TextPatternRange> klasy uwidaczniają metody i właściwości, które ułatwiają nawigację i wykonywanie zapytań o obiekty osadzone.  
  
 Zawartość tekstowa (lub tekst wewnętrzny) kontenera tekstu i obiektu osadzonego, takiego jak hiperłącze lub komórka tabeli, jest widoczna jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pojedynczy, ciągły strumień tekstu zarówno w widoku formantu, jak i w widoku zawartości drzewa; granice obiektu są ignorowane. Jeśli klient automatyzacji interfejsu użytkownika pobiera tekst w celu recytowania, interpretowania lub analizowania w jakiś sposób, zakres tekstu powinien być sprawdzany pod kątem szczególnych przypadków, takich jak tabela z zawartością tekstową lub innymi osadzonymi obiektami. Można to osiągnąć, <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> wywołując, <xref:System.Windows.Automation.AutomationElement> aby uzyskać dla każdego <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> obiektu osadzonego, a następnie wywołanie, aby uzyskać zakres tekstu dla każdego elementu. Odbywa się to rekursywnie, dopóki nie zostanie pobrana cała zawartość tekstowa.  
  
 ![Zakresy tekstu łączone przez obiekty osadzone.](./media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Przykład strumienia tekstu z osadzonymi obiektami i ich zakresami zakresów  
  
 Gdy jest to konieczne do przechodzenia przez zawartość zakresu tekstu, szereg kroków <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> są zaangażowane w kulisy, aby metoda została pomyślnie wykonana.  
  
1. Zakres tekstu jest znormalizowany; oznacza to, że zakres tekstu jest zwinięty <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> do zdegenerowanych <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> zakres w punkcie końcowym, co sprawia, że punkt końcowy zbędne. Ten krok jest konieczne, aby usunąć niejednoznaczności w <xref:System.Windows.Automation.Text.TextUnit> sytuacjach, gdy zakres `{The URL https://www.microsoft.com is embedded in text` tekstu obejmuje granice: na przykład, gdzie "{" i "}" są punkty końcowe zakresu tekstu.  
  
2. Wynikowy zakres jest przenoszony <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> do tyłu na <xref:System.Windows.Automation.Text.TextUnit> początku żądanej granicy.  
  
3. Zakres jest przesuwany do przodu <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> lub do tyłu <xref:System.Windows.Automation.Text.TextUnit> w żądanej liczbie granic.  
  
4. Zakres jest następnie rozszerzany ze stanu zdegenerowanego zakresu, przesuwając punkt <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> końcowy o jedną żądaną <xref:System.Windows.Automation.Text.TextUnit> granicę.  
  
 ![Regulacja zakresu przez Move & ExpandToEnclosingUnit](./media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Przykłady dostosowywania zakresu tekstu dla Move() i ExpandToEnclosingUnit()  
  
<a name="Common_Scenarios"></a>
## <a name="common-scenarios"></a>Typowe scenariusze  
 W poniższych sekcjach przedstawiono przykłady najbardziej typowych scenariuszy, które obejmują obiekty osadzone.  
  
 Legenda dla pokazanych przykładów:  
  
 { =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Hyperlink  

**Przykład 1 — zakres tekstu zawierający osadzone hiperłącze tekstowe**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Metoda o nazwie|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg `The URL https://www.microsoft.com is embedded in text`.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej <xref:System.Windows.Automation.AutomationElement> wewnętrzny, który otacza zakres tekstu; w tym przypadku, <xref:System.Windows.Automation.AutomationElement> który reprezentuje samego dostawcy tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca <xref:System.Windows.Automation.AutomationElement> kontrolę reprezentującą hiperłącze.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany `GetChildren` przez poprzednią metodę.|Zwraca zakres reprezentującyhttps://www.microsoft.com" ".|  
  
 **Przykład 2 — zakres tekstu, który częściowo obejmuje osadzone hiperłącze tekstowe**  
  
 Adres `https://{[www]}` URL jest osadzony w tekście.  
  
|Metoda o nazwie|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej <xref:System.Windows.Automation.AutomationElement> wewnętrzny, który otacza zakres tekstu; w takim przypadku kontrolka hiperłącza.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca, `null` ponieważ zakres tekstu nie obejmuje całego ciągu adresu URL.|  
  
**Przykład 3 — zakres tekstu, który częściowo obejmuje zawartość kontenera tekstu. Kontener tekstu zawiera osadzone hiperłącze tekstowe, które nie jest częścią zakresu tekstu.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Metoda o nazwie|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "Adres URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej <xref:System.Windows.Automation.AutomationElement> wewnętrzny, który otacza zakres tekstu; w tym przypadku, <xref:System.Windows.Automation.AutomationElement> który reprezentuje samego dostawcy tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>z parametrami (TextUnit.Word, 1).|Przenosi zakres zakresu tekstu na "http", ponieważ tekst hiperłącza składa się z pojedynczych wyrazów. W takim przypadku hiperłącze nie jest traktowane jako pojedynczy obiekt.<br /><br /> Adres URL {[http]} jest osadzony w tekście.|  
  
<a name="Image"></a>
### <a name="image"></a>Image (Obraz)  
 **Przykład 1 — zakres tekstu zawierający osadzony obraz**  
  
 {Przykład ![osadzonego obrazu](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") jest osadzony w tekście}.  
  
|Metoda o nazwie|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "Jest osadzony w tekście". Nie można oczekiwać, że do strumienia tekstowego zostanie dołączony żaden tekst ALT skojarzony z obrazem.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej <xref:System.Windows.Automation.AutomationElement> wewnętrzny, który otacza zakres tekstu; w tym przypadku, <xref:System.Windows.Automation.AutomationElement> który reprezentuje samego dostawcy tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Zwraca <xref:System.Windows.Automation.AutomationElement> kontrolę obrazu reprezentującą.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> przez poprzednią metodę.|Zwraca zdegenerowany zakres reprezentujący "![Przykład osadzonego obrazu](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Przykład 2 — zakres tekstu, który częściowo obejmuje zawartość kontenera tekstu. Kontener tekstu ma osadzony obraz, który nie jest częścią zakresu tekstu.**  
  
 {Obraz} ![Przykład osadzonego obrazu](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") jest osadzony w tekście.  
  
|Metoda o nazwie|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Zwraca ciąg "Obraz".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Zwraca najbardziej <xref:System.Windows.Automation.AutomationElement> wewnętrzny, który otacza zakres tekstu; w tym przypadku, <xref:System.Windows.Automation.AutomationElement> który reprezentuje samego dostawcy tekstu.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>z parametrami (TextUnit.Word, 1).|Przenosi zakres tekstu do "jest ". Ponieważ tylko obiekty osadzone oparte na tekście są uważane za część strumienia tekstu, obraz w tym przykładzie nie wpływa na Move lub jego zwracaną wartość (1 w tym przypadku).|  
  
<a name="Table"></a>
### <a name="table"></a>Tabela  
  
### <a name="table-used-for-examples"></a>Tabela używana do przykładów  
  
|Komórka z obrazem|Komórka z tekstem|  
|---------------------|--------------------|  
|![Przykład obrazu osadzonego](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Przykład osadzony obraz 2](./media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|Tak|  
|![Przykład osadzonego obrazu 3](./media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Obraz dla Z|Z|  
  
 **Przykład 1 — Pobierz kontener tekstu z zawartości komórki.**  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>z parametrami (0,0)|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentującą zawartość komórki tabeli; w tym przypadku element jest formantem tekstu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany `GetItem` przez poprzednią metodę.|Zwraca zakres obejmujący ![obraz Przykład osadzonego obrazu](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>dla obiektu zwróconego `RangeFromChild` przez poprzednią metodę.|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentującą komórkę tabeli; w tym przypadku element jest formantem tekstu, który obsługuje TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>dla obiektu zwróconego `GetEnclosingElement` przez poprzednią metodę.|<xref:System.Windows.Automation.AutomationElement> Zwraca tabelę reprezentującą tabelę.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>dla obiektu zwróconego `GetEnclosingElement` przez poprzednią metodę.|Zwraca <xref:System.Windows.Automation.AutomationElement> ten, który reprezentuje samego dostawcy tekstu.|  
  
 **Przykład 2 — Pobierz zawartość tekstową komórki.**  
  
|Metoda wywoływana|Wynik|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>z parametrami (1,1).|Zwraca <xref:System.Windows.Automation.AutomationElement> reprezentującą zawartość komórki tabeli; w tym przypadku element jest formantem tekstu.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>gdzie <xref:System.Windows.Automation.AutomationElement> jest obiekt zwracany `GetItem` przez poprzednią metodę.|Zwraca wartość "Y".|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika](access-embedded-objects-using-ui-automation.md)
- [Udostępnianie zawartości tabel za pomocą automatyzacji interfejsu użytkownika](expose-the-content-of-a-table-using-ui-automation.md)
- [Przenoszenie tekstu przy użyciu automatyzacji interfejsu użytkownika](traverse-text-using-ui-automation.md)
- [Przykład wyszukiwania i zaznaczenia textpattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
