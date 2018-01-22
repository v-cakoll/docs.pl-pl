---
title: "Przegląd automatyzacji interfejsu użytkownika — TextPattern"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
caps.latest.revision: "38"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dbf3e125d911a407be3b07d0ce93d5c17bd8a0b7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ui-automation-textpattern-overview"></a>Przegląd automatyzacji interfejsu użytkownika — TextPattern
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten przegląd zawiera opis sposobu używania [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] na udostępnianie zawartości tekstowej, łącznie z atrybutami styl i format, kontrolek tekstu w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-obsługiwanych platform. Formanty te obejmują, ale nie są ograniczone do, [!INCLUDE[TLA#tla_winfx](../../../includes/tlasharptla-winfx-md.md)] <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox> , a także ich [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] odpowiedniki.  
  
 Udostępnianie zawartości tekstowej formantu odbywa się za pośrednictwem <xref:System.Windows.Automation.TextPattern> wzorcu kontroli reprezentuje zawartość kontenera tekstu jako tekstu strumienia. Z kolei <xref:System.Windows.Automation.TextPattern> wymaga obsługi z <xref:System.Windows.Automation.Text.TextPatternRange> klasy do udostępnienia styl i formatu atrybutów. <xref:System.Windows.Automation.Text.TextPatternRange>obsługuje <xref:System.Windows.Automation.TextPattern> przez reprezentujący ciągły lub wielu rozłączne obejmuje tekst w kontenerze tekstu z kolekcją <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> i <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktów końcowych. <xref:System.Windows.Automation.Text.TextPatternRange>obsługuje funkcje takie jak zaznaczenia, porównanie, pobieranie i przechodzenia.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern> Klasy nie udostępniają sposób wstawiania lub zmodyfikować tekst. Jednak w zależności od tego formantu, to może być dokonane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> lub za pośrednictwem bezpośredniego klawiatury. Zobacz [TextPattern wstawić tekst przykładowy](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16) przykład.  
  
 Funkcje opisane w tym omówieniu jest ułatwianiem dostawców i użytkowników końcowych. Technologie pomocnicze można użyć [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Aby zebrać pełny tekst formatowania informacje o użytkowniku i zapewnić programowe nawigacji i zaznaczonego tekstu przez <xref:System.Windows.Automation.Text.TextUnit> (znak, word, wiersz lub akapitu).  
  
<a name="UI_Automation_TextPattern_vs__Cicero"></a>   
## <a name="ui-automation-textpattern-vs-text-services-framework"></a>TextPattern automatyzacji interfejsu użytkownika programu vs. Tekst usługi Framework  
 [!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)]to platforma systemu proste i skalowalne, która włącza usługi języka naturalnego i zaawansowane tekst na pulpicie i w aplikacjach. Oprócz zapewnienia interfejsów dla aplikacji do udostępnienia ich magazynu tekstu obsługuje ona również metadanych dla tego magazynu tekstu.  
  
 Jednak [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] zostało zaprojektowane na potrzeby aplikacji, które muszą iniekcję danych wejściowych do scenariuszy obsługujący kontekst, podczas gdy <xref:System.Windows.Automation.TextPattern> jest tylko do odczytu rozwiązania (z ograniczoną obejście powyższą) ma zapewnić zoptymalizowane dostępu do magazynu tekstu dla czytników ekranu i Braille'a urządzenia.  
  
 Krótko mówiąc, można użyć dostępne technologie, które wymagają dostępu tylko do odczytu do magazynu tekst <xref:System.Windows.Automation.TextPattern>, ale będzie bardziej złożone funkcje [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] dla obsługujący kontekst danych wejściowych.  
  
<a name="Control_Types"></a>   
## <a name="control-types"></a>Typy formantów  
  
#### <a name="text"></a>Tekst  
 Kontrolka jest podstawowy element reprezentujący fragment tekstu na ekranie.  
  
 Kontrolki tekstu autonomiczny może służyć jako etykieta lub statyczny tekst w formularzu. Kontrolki tekstu również mogą być zawarte w strukturze <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> lub <xref:System.Windows.Automation.ControlType.DataItem>.  
  
> [!NOTE]
>  Kontrolki tekstu mogą nie być wyświetlane w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa (zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)). Jest to spowodowane formantami często są wyświetlane przez właściwość Name innego formantu. Na przykład tekst, który jest używany do etykiety formantu edycyjnego jest uwidaczniany przez właściwość Name kontrolki edycji. Ponieważ w widoku zawartości kontrolki edycji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, nie jest konieczne do tekstu elementu w tym widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Tylko tekst wyświetlany w widoku zawartości jest tekst, który nie jest nadmiarowych. Dzięki temu wszystkie ułatwianiem szybkie filtrowanie tylko informacje potrzebne użytkownikom.  
  
#### <a name="edit"></a>Edytowanie  
 Edytuj Włącz kontrolki użytkownika, aby wyświetlić i edytować pojedynczy wiersz tekstu.  
  
> [!NOTE]
>  W niektórych scenariuszach układu może zawijać się pojedynczy wiersz tekstu.  
  
#### <a name="document"></a>dokument  
 Formanty dokumentu umożliwia użytkownikowi Przejdź i uzyskiwanie informacji z wielu stronach tekstu.  
  
<a name="TextPattern_Client_API_s"></a>   
## <a name="textpattern-client-apis"></a>TextPattern klienta interfejsu API  
  
|||  
|-|-|  
|`System.Windows.Automation.TextPattern Class`|Punkt wejścia dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] modelu tekstu.<br /><br /> Ta klasa zawiera także dwa <xref:System.Windows.Automation.TextPattern> odbiorników zdarzeń <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> i <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|  
|`System.Windows.Automation.Text.TextPatternRange Class`|Reprezentacja fragment tekstu w kontenerze tekst, który obsługuje <xref:System.Windows.Automation.TextPattern>.<br /><br /> Klienci automatyzacji interfejsu użytkownika należy zachować ostrożność ważność bieżącego zakresu tekstu utworzone przy użyciu <xref:System.Windows.Automation.Text.TextPatternRange>. Jeśli oryginalny tekst w formancie tekst całkowicie są zastępowane przez nowy tekst, bieżącego zakresu tekstu staje się nieprawidłowy. Jednak zakres tekstu nadal obowiązują pewne żywotność jeśli tylko część oryginalny tekst został zmieniony, a podstawowej kontrolkę tekstu zarządza jego tekstu "wskaźnik" zakotwiczenia (lub punktów końcowych), a nie z położenia bezwzględne znaków.<br /><br /> Klientów można nasłuchiwać <xref:System.Windows.Automation.TextPattern.TextChangedEvent> powiadomienia o wszelkich zmianach w zawartości tekstowej pracują.|  
|`System.Windows.Automation.AutomationTextAttribute Class`|Używany do identyfikowania atrybuty formatowania zakres tekstu.|  
  
<a name="TextPattern_Provider_API_s"></a>   
## <a name="textpattern-provider-apis"></a>TextPattern dostawcy interfejsu API  
 Elementy interfejsu użytkownika lub kontrolki obsługujące <xref:System.Windows.Automation.TextPattern> zaimplementowanie <xref:System.Windows.Automation.Provider.ITextProvider> i <xref:System.Windows.Automation.Provider.ITextRangeProvider> interfejsy, albo natywnie lub za pomocą [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] serwerów proxy, są w stanie Udostępnianie atrybutu szczegółowe informacje dotyczące tekst zawierają w Oprócz zapewnia niezawodne możliwości nawigacji.  
  
 A <xref:System.Windows.Automation.TextPattern> nie ma dostawcy do obsługi wszystkich atrybutów tekstu, jeśli formant nie ma obsługę żadnych określonych atrybutów.  
  
 A <xref:System.Windows.Automation.TextPattern> dostawca musi obsługiwać <xref:System.Windows.Automation.TextPattern.GetSelection%2A> i <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> działa, jeśli formant obsługuje zaznaczonego tekstu lub położenia kursora tekstu (lub karetkę system) w obszarze tekst. Jeśli formant nie obsługuje tej funkcji następnie go nie muszą obsługiwać żadnej z tych metod. Jednak formant musi ujawniać typ zaznaczenia tekstu obsługuje zaimplementowanie <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> właściwości.  
  
 A <xref:System.Windows.Automation.TextPattern> dostawcy zawsze musi obsługiwać <xref:System.Windows.Automation.Text.TextUnit> stałe <xref:System.Windows.Automation.Text.TextUnit.Character> i <xref:System.Windows.Automation.Text.TextUnit.Document> oraz wszelkie inne <xref:System.Windows.Automation.Text.TextUnit> stałe jest może obsłużyć.  
  
> [!NOTE]
>  Dostawca może pominąć pomocy technicznej dla określonego <xref:System.Windows.Automation.Text.TextUnit> przez odkładanie do następnego największy <xref:System.Windows.Automation.Text.TextUnit> obsługiwane w następującej kolejności: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>, i <xref:System.Windows.Automation.Text.TextUnit.Document> .  
  
|||  
|-|-|  
|`ITextProvider Interface`|Udostępnia metody, właściwości i atrybutów, które obsługują <xref:System.Windows.Automation.TextPattern> w aplikacjach klienckich (zobacz <xref:System.Windows.Automation.Provider.ITextProvider>).|  
|`ITextRangeProvider Interface`|Reprezentuje fragment tekstu w dostawcy tekstu (zobacz <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|  
|`System.Windows.Automation.TextPatternIdentifiers Class`|Zawiera wartości, które są używane jako identyfikatory dla dostawców tekst (zobacz <xref:System.Windows.Automation.TextPatternIdentifiers>).|  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpieczenia  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Architektura została zaprojektowana z myślą o bezpieczeństwie (zobacz [Przegląd zabezpieczeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-security-overview.md)). Opisane w tym omówieniu klasy TextPattern wymaga jednak pewne zagadnienia dotyczące zabezpieczeń.  
  
-   [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]tekst dostawców podać interfejsów tylko do odczytu i nie zapewniają możliwość zmiany istniejącego tekstu w formancie.  
  
-   Klienci automatyzacji interfejsu użytkownika można używać tylko [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jeśli są one w pełni "zaufany". Przykładem tego może być chroniony pulpitu logowania, gdy tylko znane i zaufane aplikacje mogą działać.  
  
-   Deweloperzy dostawców automatyzacji interfejsu użytkownika należy zwrócić uwagę, że wszystkie informacje są widoczne ujawnia w formantach ich za pośrednictwem [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jest zasadniczo publiczna i pełni dostępny przez inny kod. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]sprawia, że próbuje określić wiarygodności dowolnego klienta automatyzacji interfejsu użytkownika i dlatego dostawcy automatyzacji interfejsu użytkownika nie powinny ujawniać chronionych informacji tekstowych zawartości lub poufnych (np. pola hasła).  
  
-   Jedną z najbardziej znaczących zmian w zabezpieczenia dla [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] szeroko jest określana jako "Bezpieczny dane wejściowe" obejmującym technologii, takich jak najmniej uprzywilejowane (lub ograniczone) konta użytkownika (LUA) i interfejsu użytkownika uprawnień poziom izolacji (UIPI).  
  
    -   UIPI zapobiega jeden program z kontrolowanie i/lub innego więcej "uprzywilejowanych" program monitorowania, między procesami w oknie komunikatu ataku sfałszować danych wejściowych użytkownika.  
  
    -   LUA Ustawia limity uprawnienia aplikacje uruchomione przez użytkowników z grupy Administratorzy. Aplikacje nie muszą mieć uprawnienia administratora, ale zamiast tego zostanie uruchomiony z najmniejszymi uprawnieniami niezbędne. W rezultacie może być pewne ograniczenia wymuszane w scenariuszach LUA. Ciąg głównie obcięcie (takie jak TextPattern ciągi), gdzie może być konieczne limit rozmiaru pobieranych z aplikacji na poziomie administratora, nie są one wymuszone można przydzielić pamięci do punktu wyłączenie aplikacji ciągów.  
  
<a name="Performance"></a>   
## <a name="performance"></a>Wydajność  
 Ponieważ TextPattern opiera się na wywołań między procesami w większości jej funkcji, nie zapewnia mechanizm buforowania, aby zwiększyć wydajność podczas przetwarzania zawartości. Jest to w przeciwieństwie do innych wzorców formantu w [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] który można uzyskać dostęp za pomocą <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> metody.  
  
 Jeden działanie dotyczące poprawiania wydajności jest upewniając się, klienci automatyzacji interfejsu użytkownika próba pobrania bloków średnio o rozmiarze przy użyciu tekstu <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Na przykład GetText(1) wywołania będą naliczane międzyprocesowa trafień dla każdego znaku jedno wywołanie GetText(-1) będą naliczane co trafień międzyprocesowa, ale może mieć duże opóźnienie zależnie od wielkości dostawcy tekstu.  
  
<a name="Glossary"></a>   
## <a name="textpattern-terminology"></a>TextPattern — terminologia  
 **Atrybut**  
 Formatowanie cech zakres tekstu (na przykład <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> lub <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).  
  
 **Wymiar degeneracji zakresu**  
 Degeneracji zakres jest zakres tekstu pusty lub znak zero. Na potrzeby TextPattern — wzorzec formantu punkt wstawiania (lub karetkę system) jest uznawany za degeneracji zakresu. Jeśli nie zaznaczono żadnych tekstu, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> zwróci degeneracji zakresu punkt wstawiania tekstu i <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> zwróci degeneracji zakresu jako jego początkowy punkt końcowy. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>i <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> może zwrócić degeneracji zakresów, gdy dostawca tekstu nie może znaleźć żadnych zakresów tekstu, spełniających podane kryteria. Ten zakres degeneracji może służyć jako początkowy punkt końcowy w ramach dostawcy tekstu. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A>i <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> zwraca odwołanie o wartości null (`Nothing` w [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)]) aby uniknąć pomylenia z odnalezionych zakresu i degeneracji zakresu.  
  
 **Osadzonego obiektu**  
 Istnieją dwa typy obiekty osadzone w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] modelu tekstu. Składają się one tekstowych elementów zawartości, takich jak hiperłącza lub tabele i kontroli elementów, takich jak obrazy i przycisków. Aby uzyskać szczegółowe informacje, zobacz [dostępu do osadzonych obiektów przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md).  
  
 **Punkt końcowy**  
 Bezwzględna <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> lub <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktu zakresu tekstu w kontenerze tekstu.  
  
 ![Wartości TextPatternRangeEndpoints &#40; rozpoczęcia i zakończenia &#41;. ] (../../../docs/framework/ui-automation/media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")  
Poniżej przedstawiono zestaw początkowy i końcowy.  
  
 **TextRange**  
 Reprezentacja fragment tekstu z początkowego i końcowego, w tym wszystkie skojarzone atrybutów i funkcjonalność kontenerze tekstu.  
  
 <xref:System.Windows.Automation.Text.TextUnit>  
 Wstępnie zdefiniowane jednostka tekst (znak, word, wiersz lub akapitu) używane do przechodzenia między logicznej segmenty zakres tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Tekst usługi Framework](http://msdn.microsoft.com/library/default.asp?url=/library/tsf/tsf/text_services_framework.asp)
