---
title: Przegląd automatyzacji interfejsu użytkownika — TextPattern
description: Zapoznaj się z omówieniem wzorca kontrolki TextPattern w automatyzacji interfejsu użytkownika. Ten wzorzec kontrolki uwidacznia zawartość tekstową kontrolki, w tym format i styl.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
ms.openlocfilehash: 986b601bbd212582c09c559a9bb22983ba59fa17
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924672"
---
# <a name="ui-automation-textpattern-overview"></a>Przegląd automatyzacji interfejsu użytkownika — TextPattern

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).

W tym omówieniu opisano sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] programu w celu uwidocznienia zawartości tekstowej, w tym atrybutów formatowania i stylu, formantów tekstowych na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługiwanych platformach. Te kontrolki obejmują, ale nie są ograniczone do, Microsoft .NET Framework, <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> także ich odpowiedników Win32.

Uwidacznianie zawartości tekstowej kontrolki odbywa się za pomocą <xref:System.Windows.Automation.TextPattern> wzorca kontrolki, który reprezentuje zawartość kontenera tekstowego jako strumień tekstowy. Z kolei program <xref:System.Windows.Automation.TextPattern> wymaga obsługi <xref:System.Windows.Automation.Text.TextPatternRange> klasy w celu uwidocznienia atrybutów formatowania i stylu. <xref:System.Windows.Automation.Text.TextPatternRange>obsługuje <xref:System.Windows.Automation.TextPattern> , reprezentując sąsiadujące lub wielokrotne rozłączane rozłączenia tekstu w kontenerze tekstu z kolekcją <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> i <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktami końcowymi. <xref:System.Windows.Automation.Text.TextPatternRange>obsługuje funkcje, takie jak wybór, porównanie, pobieranie i przechodzenie.

> [!NOTE]
> <xref:System.Windows.Automation.TextPattern>Klasy nie zapewniają metody wstawiania ani modyfikowania tekstu. Jednak w zależności od kontrolki może to osiągnąć za pomocą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> lub za pośrednictwem bezpośredniej klawiatury wejściowej. Zapoznaj się z przykładem [Wstaw tekst TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) .

Funkcje opisane w tym omówieniu są niezbędne dla dostawców technologii pomocniczych i ich użytkowników końcowych. Technologie pomocnicze mogą korzystać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] z programu w celu zebrania pełnych informacji o formatowaniu tekstu dla użytkownika i zapewnienia programistycznego nawigowania i wybierania tekstu przez <xref:System.Windows.Automation.Text.TextUnit> (znak, Word, wiersz lub akapit).

<a name="UI_Automation_TextPattern_vs__Cicero"></a>

## <a name="ui-automation-textpattern-vs-text-services-framework"></a>TextPattern Automatyzacja interfejsu użytkownika i struktura usług tekstowych

Usługa Text Services Framework (TSF) to proste i skalowalne środowisko systemowe, które umożliwia usługom języka naturalnego i zaawansowane wprowadzanie tekstu na pulpicie i w aplikacjach. Oprócz udostępniania interfejsów dla aplikacji, które umożliwiają udostępnienie magazynu tekstu, obsługuje również metadane dla tego magazynu tekstu.

Jednak TSF został zaprojektowany z myślą o aplikacjach, które muszą wstrzyknąć dane wejściowe do scenariuszy z obsługą kontekstu <xref:System.Windows.Automation.TextPattern> , a to rozwiązanie tylko do odczytu (z ograniczonym obejściem zanotowanym powyżej) przeznaczone do zapewniania zoptymalizowanego dostępu do magazynu tekstowego na potrzeby czytników ekranu i urządzeń z obsługą języka Braille'a.

W krótkich, dostępnych technologiach, które wymagają dostępu tylko do odczytu do magazynu tekstowego <xref:System.Windows.Automation.TextPattern> , można użyć, ale będzie potrzebna bardziej złożona funkcja TSF dla danych wejściowych z uwzględnieniem kontekstu.

<a name="Control_Types"></a>

## <a name="control-types"></a>Typy formantów

### <a name="text"></a>Tekst

Kontrolka tekst to podstawowy element reprezentujący fragment tekstu na ekranie.

Autonomiczna kontrolka tekstowa może być używana jako etykieta lub statyczny tekst w formularzu. Kontrolki tekstu mogą również znajdować się w strukturze <xref:System.Windows.Automation.ControlType.ListItem> <xref:System.Windows.Automation.ControlType.TreeItem> lub <xref:System.Windows.Automation.ControlType.DataItem> .

> [!NOTE]
> Kontrolki tekstu mogą nie być wyświetlane w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa (zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)). Wynika to z faktu, że kontrolki tekstowe są często wyświetlane za pomocą właściwości Nazwa innej kontrolki. Na przykład tekst, który jest używany do etykiet kontrolki edycji, jest udostępniany przez właściwość Name kontrolki edycji. Ponieważ kontrolka edycji znajduje się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, nie jest konieczne, aby sam element tekstu znajdował się w tym widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Jedynym tekstem, który jest wyświetlany w widoku zawartości jest tekst, który nie jest nadmiarowy. Dzięki temu każda technologia pomocnicza może szybko filtrować tylko te informacje, których potrzebują użytkownicy.

### <a name="edit"></a>Edytuj

Edycja kontrolek umożliwia użytkownikowi wyświetlanie i edytowanie pojedynczego wiersza tekstu.

> [!NOTE]
> Pojedynczy wiersz tekstu może być zawijany w niektórych scenariuszach układu.

### <a name="document"></a>Dokument

Kontrolki dokumentów umożliwiają użytkownikowi nawigację i uzyskiwanie informacji z wielu stron tekstu.

<a name="TextPattern_Client_API_s"></a>

## <a name="textpattern-client-apis"></a>Interfejsy API klienta TextPattern

|||
|-|-|
|`System.Windows.Automation.TextPattern Class`|Punkt wejścia dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] modelu tekstu.<br /><br /> Ta klasa zawiera również dwa <xref:System.Windows.Automation.TextPattern> detektory zdarzeń <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> i <xref:System.Windows.Automation.TextPattern.TextChangedEvent> .|
|`System.Windows.Automation.Text.TextPatternRange Class`|Reprezentacja zakresu tekstu w kontenerze tekstu, który obsługuje <xref:System.Windows.Automation.TextPattern> .<br /><br /> Klientom automatyzacji interfejsu użytkownika należy zachować ostrożność w zakresie aktualnej ważności zakresu tekstu utworzonego przy użyciu <xref:System.Windows.Automation.Text.TextPatternRange> . Jeśli oryginalny tekst w kontrolce tekstowej jest całkowicie zastępowany przez nowy tekst, bieżący zakres tekstu jest nieprawidłowy. Jednak zakres tekstu może nadal mieć pewną żywotność, jeśli tylko część oryginalnego tekstu zostanie zmieniona i formant tekstu podstawowego zarządza tekstem "wskaźnik" przy użyciu kotwic (lub punktów końcowych), a nie bezwzględnie pozycjonowanie znaków.<br /><br /> Klienci mogą nasłuchiwanie <xref:System.Windows.Automation.TextPattern.TextChangedEvent> powiadomień o wszelkich zmianach w zawartości tekstowej, z którą pracują.|
|`System.Windows.Automation.AutomationTextAttribute Class`|Służy do identyfikowania atrybutów formatowania zakresu tekstu.|

<a name="TextPattern_Provider_API_s"></a>

## <a name="textpattern-provider-apis"></a>Interfejsy API dostawcy TextPattern

Elementy interfejsu użytkownika lub kontrolki, które obsługują, <xref:System.Windows.Automation.TextPattern> implementując <xref:System.Windows.Automation.Provider.ITextProvider> <xref:System.Windows.Automation.Provider.ITextRangeProvider> interfejsy i, natywnie lub za pomocą [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] serwerów proxy, mogą uwidaczniać szczegółowe informacje o atrybutach dla dowolnego tekstu, który zawiera, oprócz zapewniania niezawodnych możliwości nawigacyjnych.

<xref:System.Windows.Automation.TextPattern>Dostawca nie musi obsługiwać wszystkich atrybutów tekstu, jeśli formant nie obsługuje żadnych określonych atrybutów.

<xref:System.Windows.Automation.TextPattern>Dostawca musi obsługiwać <xref:System.Windows.Automation.TextPattern.GetSelection%2A> funkcje i, <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> Jeśli kontrolka obsługuje Zaznaczanie tekstu lub umieszczanie kursora tekstu (lub karetki systemowej) w obszarze tekstu. Jeśli formant nie obsługuje tej funkcji, nie trzeba obsługiwać żadnej z tych metod. Jednak kontrolka musi uwidocznić typ zaznaczonego tekstu, który obsługuje, implementując <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> Właściwość.

<xref:System.Windows.Automation.TextPattern>Dostawca musi zawsze obsługiwać stałe, <xref:System.Windows.Automation.Text.TextUnit> <xref:System.Windows.Automation.Text.TextUnit.Character> a <xref:System.Windows.Automation.Text.TextUnit.Document> także wszystkie inne stałe, <xref:System.Windows.Automation.Text.TextUnit> które może obsługiwać.

> [!NOTE]
> Dostawca może pominąć obsługę określonego <xref:System.Windows.Automation.Text.TextUnit> przez odwnioskowanie do następnego największego <xref:System.Windows.Automation.Text.TextUnit> obsługiwanego w następującej kolejności:,,,, <xref:System.Windows.Automation.Text.TextUnit.Character> , <xref:System.Windows.Automation.Text.TextUnit.Format> <xref:System.Windows.Automation.Text.TextUnit.Word> <xref:System.Windows.Automation.Text.TextUnit.Line> <xref:System.Windows.Automation.Text.TextUnit.Paragraph> <xref:System.Windows.Automation.Text.TextUnit.Page> i <xref:System.Windows.Automation.Text.TextUnit.Document> .

|||
|-|-|
|`ITextProvider Interface`|Opisuje metody, właściwości i atrybuty, które obsługują <xref:System.Windows.Automation.TextPattern> aplikacje klienckie (zobacz <xref:System.Windows.Automation.Provider.ITextProvider> ).|
|`ITextRangeProvider Interface`|Reprezentuje zakres tekstu w dostawcy tekstu (zobacz <xref:System.Windows.Automation.Provider.ITextRangeProvider> ).|
|`System.Windows.Automation.TextPatternIdentifiers Class`|Zawiera wartości, które są używane jako identyfikatory dla dostawców tekstu (zobacz <xref:System.Windows.Automation.TextPatternIdentifiers> ).|

<a name="Security"></a>

## <a name="security"></a>Zabezpieczenia

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Architektura została zaprojektowana z myślą o bezpieczeństwie (zobacz [Omówienie zabezpieczeń automatyzacji interfejsu użytkownika](ui-automation-security-overview.md)). Jednak klasy TextPattern opisane w tym omówieniu wymagają pewnych określonych zagadnień dotyczących zabezpieczeń.

- [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]dostawcy tekstu dostarczają interfejsy tylko do odczytu i nie zapewniają możliwości zmiany istniejącego tekstu w kontrolce.

- Klientów automatyzacji interfejsu użytkownika można używać tylko [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] wtedy, gdy są one w pełni zaufane. Przykładem może być chroniony pulpit logowania, w którym można uruchamiać tylko znane i zaufane aplikacje.

- Deweloperzy dostawcy automatyzacji interfejsu użytkownika powinni mieć świadomość, że wszystkie informacje, które chcą uwidocznić w swoich kontrolach, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] są zasadniczo publiczne i w pełni dostępne przez inny kod. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]nie podejmuje żadnych działań w celu określenia wiarygodności dowolnego klienta automatyzacji interfejsu użytkownika i w związku z tym dostawcy automatyzacji interfejsu użytkownika nie mogą ujawniać zawartości chronionej ani poufnych informacji tekstowych (na przykład pól haseł).

- Jedną z najbardziej znaczących zmian w zabezpieczeniach systemu Windows Vista jest ogólnie nazywane "bezpiecznymi danymi wejściowymi", które obejmują technologie takie jak najmniej uprzywilejowane (lub ograniczone) konta użytkowników (LUA) i izolacja poziomu uprawnień interfejsu użytkownika (podsystemu UIPI).

  - PODSYSTEMU UIPI uniemożliwia jednemu programowi kontrolowanie i/lub monitorowanie innego bardziej "uprzywilejowanego" programu, uniemożliwiając ataki między przedziałami komunikatów okien, które fałszuje dane wejściowe użytkownika.

  - LUA ustawia limity uprawnień aplikacji uruchamianych przez użytkowników w grupie Administratorzy. Aplikacje nie muszą mieć uprawnień administratora, ale zamiast tego będą uruchamiane z najniższymi wymaganymi uprawnieniami. W związku z tym niektóre ograniczenia mogą być wymuszane w scenariuszach LUA. W szczególności obcinanie ciągów (w tym ciągów TextPattern), w których może być konieczne ograniczenie rozmiaru ciągów pobieranych z aplikacji na poziomie administratora, aby nie wymusić przydzielenia pamięci do punktu wyłączenia aplikacji.

<a name="Performance"></a>

## <a name="performance"></a>Wydajność

Ponieważ TextPattern polega na wywołaniach międzyprocesowych dla większości funkcji, nie zapewnia mechanizmu buforowania, aby zwiększyć wydajność podczas przetwarzania zawartości. Jest to w przeciwieństwie do innych wzorców formantów w programie [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , do których można uzyskać dostęp przy użyciu <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> metod lub.

Jednym z taktyką w celu zwiększenia wydajności jest zapewnienie, że klienci automatyzacji interfejsu użytkownika próbują pobrać rozmiary bloków tekstu o umiarkowanym rozmiarze przy użyciu <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A> . Na przykład wywołania gettext (1) będą powodować naliczanie wieloprocesowych trafień dla każdego znaku, podczas gdy jedno wywołanie GetText (-1) spowoduje naliczenie jednego wieloprocesowego, ale może mieć duże opóźnienie w zależności od rozmiaru dostawcy tekstu.

<a name="Glossary"></a>

## <a name="textpattern-terminology"></a>Terminologia TextPattern

**Przypisane**\
Charakterystyka formatowania zakresu tekstu (na przykład <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> lub <xref:System.Windows.Automation.TextPattern.FontNameAttribute> ).

**Wygeneruj zakres**\
Zakres degeneracji jest pustym lub zerowym zakresem tekstu. Na potrzeby wzorca kontrolki TextPattern punkt wstawiania tekstu (lub karetka systemowa) jest uznawany za wygenerowanego zakresu. Jeśli żaden tekst nie jest zaznaczony, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> zwróci zakres degeneracji w punkcie wstawiania tekstu i <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> zwróci zakres degeneracji jako początkowy punkt końcowy. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>i <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> mogą zwracać zakresy Wygeneruj, gdy dostawca tekstu nie może znaleźć żadnych zakresów tekstu pasujących do danego warunku. Tego zakresu degeneracji można użyć jako początkowego punktu końcowego w ramach dostawcy tekstu. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A>i <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> Zwróć odwołanie o wartości null ( `Nothing` w programie Microsoft Visual Basic .NET), aby uniknąć nieporozumień z odnalezionym zakresem w przeciwieństwie do wygenerowanego zakresu.

**Osadzony obiekt**\
W modelu tekstu istnieją dwa typy osadzonych obiektów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Składają się one z tekstowych elementów zawartości, takich jak hiperłącza lub tabele, oraz elementów formantów, takich jak obrazy i przyciski. Aby uzyskać bardziej szczegółowe informacje, zobacz [dostęp do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika](access-embedded-objects-using-ui-automation.md).

**Punktu końcowego**\
Bezwzględny <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> lub <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punkt zakresu tekstu w obrębie kontenera tekstu.

![TextPatternRangeEndpoints &#40;początkową i końcową&#41;.](./media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")
Poniższy ilustruje zestaw punktów początkowych i końcowych.

**TextRange**\
Reprezentacja zakresu tekstu oraz punktów początkowych i końcowych w kontenerze tekstu, w tym wszystkich skojarzonych z nim atrybutów i funkcji.

<xref:System.Windows.Automation.Text.TextUnit>\
Wstępnie zdefiniowana jednostka tekstu (Character, Word, line lub Paragraph) służąca do przechodzenia przez logiczne segmenty zakresu tekstu.

## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md)
- [Struktura usług tekstowych](/windows/desktop/api/_tsf/)
