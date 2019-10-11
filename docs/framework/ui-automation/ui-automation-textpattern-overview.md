---
title: TextPattern Automatyzacja interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
ms.openlocfilehash: 15638e7da99ef15be58052849bf0675cc21941c9
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180160"
---
# <a name="ui-automation-textpattern-overview"></a>TextPattern Automatyzacja interfejsu użytkownika — omówienie

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperzy, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] można znaleźć w temacie [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).

W tym omówieniu opisano sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] w celu udostępnienia zawartości tekstowej, w tym atrybutów formatowania i stylu, kontrolek tekstowych w @no__t obsługiwanych platformach -1. Te kontrolki obejmują, ale nie są ograniczone do, Microsoft .NET Framework <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox>, a także ich odpowiedników [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)].

Uwidacznianie zawartości tekstowej kontrolki odbywa się za pomocą wzorca kontroli <xref:System.Windows.Automation.TextPattern>, który reprezentuje zawartość kontenera tekstowego jako strumień tekstowy. Z kolei <xref:System.Windows.Automation.TextPattern> wymaga obsługi klasy <xref:System.Windows.Automation.Text.TextPatternRange> do udostępniania atrybutów formatowania i stylu. <xref:System.Windows.Automation.Text.TextPatternRange> obsługuje <xref:System.Windows.Automation.TextPattern> przez reprezentowanie ciągłego lub wielokrotnego, rozłączonych tekstu rozmieszczonych w kontenerze tekstu z kolekcją <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> i <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktów końcowych. <xref:System.Windows.Automation.Text.TextPatternRange> obsługuje funkcje takie jak wybór, porównanie, pobieranie i przechodzenie.

> [!NOTE]
> Klasy <xref:System.Windows.Automation.TextPattern> nie zapewniają metody wstawiania ani modyfikowania tekstu. Jednak w zależności od formantu może to osiągnąć [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> lub za pośrednictwem bezpośredniej klawiatury wejściowej. Zapoznaj się z przykładem [Wstaw tekst TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) .

Funkcje opisane w tym omówieniu są niezbędne dla dostawców technologii pomocniczych i ich użytkowników końcowych. Technologie pomocnicze mogą używać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w celu zebrania pełnych informacji o formatowaniu tekstu dla użytkownika i zapewnienia programistycznego nawigowania i wybierania tekstu przez <xref:System.Windows.Automation.Text.TextUnit> (znak, Word, wiersz lub akapit).

<a name="UI_Automation_TextPattern_vs__Cicero"></a>

## <a name="ui-automation-textpattern-vs-text-services-framework"></a>TextPattern Automatyzacja interfejsu użytkownika i struktura usług tekstowych

Usługa Text Services Framework (TSF) to proste i skalowalne środowisko systemowe, które umożliwia usługom języka naturalnego i zaawansowane wprowadzanie tekstu na pulpicie i w aplikacjach. Oprócz udostępniania interfejsów dla aplikacji, które umożliwiają udostępnienie magazynu tekstu, obsługuje również metadane dla tego magazynu tekstu.

Jednak TSF został zaprojektowany z myślą o aplikacjach, które wymagają wprowadzenia danych wejściowych do scenariuszy z obsługą kontekstu, a <xref:System.Windows.Automation.TextPattern> to rozwiązanie tylko do odczytu (z ograniczonym obejściem zanotowanym powyżej) przeznaczone do zapewniania optymalnego dostępu do magazynu tekstowego dla czytników ekranu i języka Braille'a urządzeniem.

W przypadku krótkich, dostępnych technologii, które wymagają dostępu tylko do odczytu do magazynu tekstowego, można użyć <xref:System.Windows.Automation.TextPattern>, ale będzie potrzebna bardziej złożona funkcja TSF dla danych wejściowych z uwzględnieniem kontekstu.

<a name="Control_Types"></a>

## <a name="control-types"></a>Typy formantów

### <a name="text"></a>Tekst

Kontrolka tekst to podstawowy element reprezentujący fragment tekstu na ekranie.

Autonomiczna kontrolka tekstowa może być używana jako etykieta lub statyczny tekst w formularzu. Kontrolki tekstu mogą również znajdować się w strukturze <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> lub <xref:System.Windows.Automation.ControlType.DataItem>.

> [!NOTE]
> Kontrolki tekstu mogą nie być wyświetlane w widoku zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)). Wynika to z faktu, że kontrolki tekstowe są często wyświetlane za pomocą właściwości Nazwa innej kontrolki. Na przykład tekst, który jest używany do etykiet kontrolki edycji, jest udostępniany przez właściwość Name kontrolki edycji. Ponieważ kontrolka edycji znajduje się w widoku zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], nie jest to konieczne, aby element tekstowy znajdował się w tym widoku drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Jedynym tekstem, który jest wyświetlany w widoku zawartości jest tekst, który nie jest nadmiarowy. Dzięki temu każda technologia pomocnicza może szybko filtrować tylko te informacje, których potrzebują użytkownicy.

### <a name="edit"></a>Edytuj

Edycja kontrolek umożliwia użytkownikowi wyświetlanie i edytowanie pojedynczego wiersza tekstu.

> [!NOTE]
> Pojedynczy wiersz tekstu może być zawijany w niektórych scenariuszach układu.

### <a name="document"></a>Dokumentowa

Kontrolki dokumentów umożliwiają użytkownikowi nawigację i uzyskiwanie informacji z wielu stron tekstu.

<a name="TextPattern_Client_API_s"></a>

## <a name="textpattern-client-apis"></a>Interfejsy API klienta TextPattern

|||
|-|-|
|`System.Windows.Automation.TextPattern Class`|Punkt wejścia dla modelu tekstu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].<br /><br /> Ta klasa zawiera również dwa <xref:System.Windows.Automation.TextPattern> detektory zdarzeń, <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> i <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|
|`System.Windows.Automation.Text.TextPatternRange Class`|Reprezentacja zakresu tekstu w kontenerze tekstu, który obsługuje <xref:System.Windows.Automation.TextPattern>.<br /><br /> Klientom automatyzacji interfejsu użytkownika należy zachować ostrożność w zakresie aktualnej ważności zakresu tekstu utworzonego przy użyciu <xref:System.Windows.Automation.Text.TextPatternRange>. Jeśli oryginalny tekst w kontrolce tekstowej jest całkowicie zastępowany przez nowy tekst, bieżący zakres tekstu jest nieprawidłowy. Jednak zakres tekstu może nadal mieć pewną żywotność, jeśli tylko część oryginalnego tekstu zostanie zmieniona i formant tekstu podstawowego zarządza tekstem "wskaźnik" przy użyciu kotwic (lub punktów końcowych), a nie bezwzględnie pozycjonowanie znaków.<br /><br /> Klienci mogą nasłuchiwać dla <xref:System.Windows.Automation.TextPattern.TextChangedEvent> do powiadomienia o zmianach w zawartości tekstowej, z którą pracują.|
|`System.Windows.Automation.AutomationTextAttribute Class`|Służy do identyfikowania atrybutów formatowania zakresu tekstu.|

<a name="TextPattern_Provider_API_s"></a>

## <a name="textpattern-provider-apis"></a>Interfejsy API dostawcy TextPattern

Elementy interfejsu użytkownika lub formanty, które obsługują <xref:System.Windows.Automation.TextPattern> przez implementację interfejsów <xref:System.Windows.Automation.Provider.ITextProvider> i <xref:System.Windows.Automation.Provider.ITextRangeProvider>, natywnie lub przez [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] proxy, mogą ujawniać szczegółowe informacje o atrybutach, które zawierają, oprócz zapewniania niezawodnego możliwości nawigacyjne.

Dostawca <xref:System.Windows.Automation.TextPattern> nie musi obsługiwać wszystkich atrybutów tekstu, jeśli formant nie obsługuje żadnych określonych atrybutów.

Dostawca <xref:System.Windows.Automation.TextPattern> musi obsługiwać funkcje <xref:System.Windows.Automation.TextPattern.GetSelection%2A> i <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A>, Jeśli kontrolka obsługuje Zaznaczanie tekstu lub umieszczanie kursora tekstu (lub karetki systemowej) w obszarze tekstu. Jeśli formant nie obsługuje tej funkcji, nie trzeba obsługiwać żadnej z tych metod. Jednak kontrolka musi uwidocznić typ zaznaczonego tekstu, który obsługuje, implementując Właściwość <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A>.

Dostawca <xref:System.Windows.Automation.TextPattern> musi zawsze obsługiwać stałe <xref:System.Windows.Automation.Text.TextUnit> <xref:System.Windows.Automation.Text.TextUnit.Character> i <xref:System.Windows.Automation.Text.TextUnit.Document>, a także inne <xref:System.Windows.Automation.Text.TextUnit> stałe, które jest w stanie obsłużyć.

> [!NOTE]
> Dostawca może pominąć obsługę określonego <xref:System.Windows.Automation.Text.TextUnit>, odwołując się do następnego największego <xref:System.Windows.Automation.Text.TextUnit> obsługiwanego w następującej kolejności: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page> i <xref:System.Windows.Automation.Text.TextUnit.Document>.

|||
|-|-|
|`ITextProvider Interface`|Opisuje metody, właściwości i atrybuty, które obsługują <xref:System.Windows.Automation.TextPattern> w aplikacjach klienckich (patrz <xref:System.Windows.Automation.Provider.ITextProvider>).|
|`ITextRangeProvider Interface`|Reprezentuje zakres tekstu w dostawcy tekstu (zobacz <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|
|`System.Windows.Automation.TextPatternIdentifiers Class`|Zawiera wartości, które są używane jako identyfikatory dla dostawców tekstu (zobacz <xref:System.Windows.Automation.TextPatternIdentifiers>).|

<a name="Security"></a>

## <a name="security"></a>Zabezpieczenia

Architektura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] została zaprojektowana z myślą o bezpieczeństwie (zobacz [Omówienie zabezpieczeń automatyzacji interfejsu użytkownika](ui-automation-security-overview.md)). Jednak klasy TextPattern opisane w tym omówieniu wymagają pewnych określonych zagadnień dotyczących zabezpieczeń.

- dostawcy tekstu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dostarczają interfejsy tylko do odczytu i nie zapewniają możliwości zmiany istniejącego tekstu w kontrolce.

- Klienci automatyzacji interfejsu użytkownika mogą używać tylko [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], jeśli są one w pełni zaufane. Przykładem może być chroniony pulpit logowania, w którym można uruchamiać tylko znane i zaufane aplikacje.

- Deweloperzy dostawcy automatyzacji interfejsu użytkownika powinni mieć świadomość, że wszystkie informacje, które chcą uwidocznić w swoich kontrolach za pomocą [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], są zasadniczo publicznie i w pełni dostępne przez inny kod. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] nie podejmuje żadnych działań w celu określenia wiarygodności dowolnego klienta automatyzacji interfejsu użytkownika, w związku z czym dostawca automatyzacji interfejsu użytkownika nie powinien ujawniać zawartości chronionej ani poufnych informacji tekstowych (na przykład pól haseł).

- Jedną z najbardziej znaczących zmian w zabezpieczeniach dla [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] jest szeroko określana jako "Bezpieczna wartość wejściowa", która obejmuje technologie takie jak najwyższe uprzywilejowane (lub ograniczone) konta użytkowników (LUA) i izolacja poziomu uprawnień interfejsu użytkownika (podsystemu UIPI).

  - PODSYSTEMU UIPI uniemożliwia jednemu programowi kontrolowanie i/lub monitorowanie innego bardziej "uprzywilejowanego" programu, uniemożliwiając ataki między przedziałami komunikatów okien, które fałszuje dane wejściowe użytkownika.

  - LUA ustawia limity uprawnień aplikacji uruchamianych przez użytkowników w grupie Administratorzy. Aplikacje nie muszą mieć uprawnień administratora, ale zamiast tego będą uruchamiane z najniższymi wymaganymi uprawnieniami. W związku z tym niektóre ograniczenia mogą być wymuszane w scenariuszach LUA. W szczególności obcinanie ciągów (w tym ciągów TextPattern), w których może być konieczne ograniczenie rozmiaru ciągów pobieranych z aplikacji na poziomie administratora, aby nie wymusić przydzielenia pamięci do punktu wyłączenia aplikacji.

<a name="Performance"></a>

## <a name="performance"></a>Wydajność

Ponieważ TextPattern polega na wywołaniach międzyprocesowych dla większości funkcji, nie zapewnia mechanizmu buforowania, aby zwiększyć wydajność podczas przetwarzania zawartości. Jest to w przeciwieństwie do innych wzorców kontrolek w [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], do których można uzyskać dostęp przy użyciu metod <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>.

Jednym z taktyką w celu zwiększenia wydajności jest zapewnienie, że klienci automatyzacji interfejsu użytkownika próbują pobrać rozmiary bloków tekstu o umiarkowanym rozmiarze przy użyciu <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Na przykład wywołania gettext (1) będą powodować naliczanie wieloprocesowych trafień dla każdego znaku, podczas gdy jedno wywołanie GetText (-1) spowoduje naliczenie jednego wieloprocesowego, ale może mieć duże opóźnienie w zależności od rozmiaru dostawcy tekstu.

<a name="Glossary"></a>

## <a name="textpattern-terminology"></a>Terminologia TextPattern

@No__t **atrybutu**-1
Charakterystyka formatowania zakresu tekstu (na przykład <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> lub <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).

**Wygeneruj zakres**\
Zakres degeneracji jest pustym lub zerowym zakresem tekstu. Na potrzeby wzorca kontrolki TextPattern punkt wstawiania tekstu (lub karetka systemowa) jest uznawany za wygenerowanego zakresu. Jeśli nie zaznaczono żadnego tekstu, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> zwróci zakres degeneracji w punkcie wstawiania tekstu i <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> zwróci zakres wygenerowania jako początkowy punkt końcowy. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> i <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> mogą zwracać zakresy Wygeneruj, gdy dostawca tekstu nie może znaleźć żadnych zakresów tekstu pasujących do danego warunku. Tego zakresu degeneracji można użyć jako początkowego punktu końcowego w ramach dostawcy tekstu. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> i <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> zwracają odwołanie o wartości null (`Nothing` w Microsoft Visual Basic .NET), aby uniknąć nieporozumień z wykrytym zakresem w przeciwieństwie do wygenerowanego zakresu.

**Osadzony obiekt**\
W modelu tekstu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istnieją dwa typy osadzonych obiektów. Składają się one z tekstowych elementów zawartości, takich jak hiperłącza lub tabele, oraz elementów formantów, takich jak obrazy i przyciski. Aby uzyskać bardziej szczegółowe informacje, zobacz [dostęp do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika](access-embedded-objects-using-ui-automation.md).

**Punkt końcowy**\
Bezwzględny <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> lub <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktu tekstu w obrębie kontenera tekstu.

![TextPatternRangeEndpoints &#40;początkowy i końcowy&#41;.](./media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints") Poniższy ilustruje zestaw punktów początkowych i końcowych.

**Textrange**\
Reprezentacja zakresu tekstu oraz punktów początkowych i końcowych w kontenerze tekstu, w tym wszystkich skojarzonych z nim atrybutów i funkcji.

<xref:System.Windows.Automation.Text.TextUnit>\
Wstępnie zdefiniowana jednostka tekstu (Character, Word, line lub Paragraph) służąca do przechodzenia przez logiczne segmenty zakresu tekstu.

## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Obsługa wzorców kontrolek w dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md)
- [Struktura usług tekstowych](/windows/desktop/api/_tsf/)
