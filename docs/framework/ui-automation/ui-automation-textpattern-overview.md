---
title: Przegląd automatyzacji interfejsu użytkownika — TextPattern
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 522caed7e8006157f99e65e99bf52743871444ad
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708520"
---
# <a name="ui-automation-textpattern-overview"></a>Przegląd automatyzacji interfejsu użytkownika — TextPattern
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym omówieniu opisano sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do udostępnienia zawartości tekstowej, łącznie z atrybutami formatowanie i style, kontrolek tekstu w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-obsługiwanych platform. Te kontrolki obejmują, ale nie są ograniczone do programu Microsoft .NET Framework <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.RichTextBox> , a także ich [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] odpowiedniki.  
  
 Udostępnianie zawartości tekstowej kontrolki odbywa się za pośrednictwem <xref:System.Windows.Automation.TextPattern> — wzorzec kontrolki, która reprezentuje zawartość kontenera tekstu jako strumienia tekstu. Z kolei <xref:System.Windows.Automation.TextPattern> wymaga obsługi elementu <xref:System.Windows.Automation.Text.TextPatternRange> klasy w celu udostępnienia styl i formatu atrybutów. <xref:System.Windows.Automation.Text.TextPatternRange> obsługuje <xref:System.Windows.Automation.TextPattern> poprzez reprezentowanie ciągłych lub wielu rozłączne zakresy tekstu w kontenerze tekstu z kolekcją <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> i <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punktów końcowych. <xref:System.Windows.Automation.Text.TextPatternRange> obsługuje funkcje, takie jak wybór, porównanie, pobieranie i przechodzenia.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern> Klasy zapewnia sposób wstawiania lub modyfikowanie tekstu. Jednak w zależności od kontrolki, to może być dokonane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> lub przy użyciu danych wprowadzonych z klawiatury bezpośrednich. Zobacz [TextPattern Wstaw tekst przykładowy](https://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16) przykład.  
  
 Funkcje opisane w tym omówieniu jest niezbędna do dostawców technologii pomocniczych i użytkownikom końcowym. Można użyć technologiami pomocniczymi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do gromadzenia pełny tekst formatowanie informacje dotyczące użytkownika, a następnie podaj Nawigacja programowa i zaznaczonego tekstu przez <xref:System.Windows.Automation.Text.TextUnit> (znak, word, wiersza lub akapitu).  
  
<a name="UI_Automation_TextPattern_vs__Cicero"></a>   
## <a name="ui-automation-textpattern-vs-text-services-framework"></a>TextPattern automatyzacji interfejsu użytkownika programu vs. Tekst usługi Framework  
 [!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)] to struktura systemu proste i skalowalne, która włącza usługi w języka naturalnego i zaawansowane tekstu w danych wejściowych na pulpicie i w aplikacjach. Oprócz interfejsów dla aplikacji do udostępnienia swojego Sklepu tekstu obsługuje ona również metadanych dla tego magazynu tekstu.  
  
 Jednak [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] zaprojektowano dla aplikacji, które należy wstrzyknąć wprowadzania do scenariuszy opartych na kontekście, natomiast <xref:System.Windows.Automation.TextPattern> jest tylko do odczytu rozwiązania (z ograniczoną obejście przedstawionych powyżej) przeznaczone zapewnienie zoptymalizowanego dostępu do magazynu tekstu dla czytniki zawartości ekranu i Braille'a urządzenia.  
  
 Krótko mówiąc, można użyć technologii ułatwień dostępu, które wymagają dostępu tylko do odczytu do magazynu tekstu <xref:System.Windows.Automation.TextPattern>, jednak wymagają bardziej złożone funkcje [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] uwzględniających kontekst danych wejściowych.  
  
<a name="Control_Types"></a>   
## <a name="control-types"></a>Typy formantów  
  
#### <a name="text"></a>Tekst  
 Kontrolka tekstu jest podstawowy element reprezentuje fragment tekstu na ekranie.  
  
 Kontrolki tekstu autonomicznego może służyć jako etykieta lub statyczny tekst w formularzu. Kontrolek tekstu, również mogą być zawarte w strukturze <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> lub <xref:System.Windows.Automation.ControlType.DataItem>.  
  
> [!NOTE]
>  Kontrolki tekstu mogą nie być wyświetlane w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa (zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)). Jest to spowodowane kontrolek tekstu są często wyświetlane za pomocą właściwości nazwy innej kontrolki. Na przykład tekst, który jest używany jako etykieta kontrolki edycji jest uwidaczniany za pomocą właściwości Name obiektu kontrolki edycji. Ponieważ w widoku zawartości kontrolki edycji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, nie jest konieczne dla elementu tekstu, aby być w tym widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa. Tylko tekst, który pojawia się w widoku zawartości to tekst, który nie jest nadmiarowe informacje. Dzięki temu wszystkie ułatwianiem szybkie filtrowanie tylko na informacje, które użytkownicy muszą.  
  
#### <a name="edit"></a>Edytowanie  
 Edytuj Włącz kontrolki użytkownika, aby wyświetlić i edytować pojedynczy wiersz tekstu.  
  
> [!NOTE]
>  Pojedynczy wiersz tekstu może opakować w niektórych scenariuszach układu.  
  
#### <a name="document"></a>dokument  
 Formantów dokumentów umożliwia użytkownikowi Przejdź i uzyskaj informacje od wielu stronach tekstu.  
  
<a name="TextPattern_Client_API_s"></a>   
## <a name="textpattern-client-apis"></a>TextPattern klienta interfejsu API  
  
|||  
|-|-|  
|`System.Windows.Automation.TextPattern Class`|Punkt wejścia dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] modelu tekstu.<br /><br /> Ta klasa zawiera także dwie <xref:System.Windows.Automation.TextPattern> detektorów zdarzeń <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> i <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|  
|`System.Windows.Automation.Text.TextPatternRange Class`|Reprezentacja tekstu w kontenerze tekst, który obsługuje <xref:System.Windows.Automation.TextPattern>.<br /><br /> Klienci automatyzacji interfejsu użytkownika ostrożność przy bieżącej ważności zakres tekstu, utworzony za pomocą <xref:System.Windows.Automation.Text.TextPatternRange>. Jeśli oryginalny tekst w kontrolce tekst został całkowicie zastąpiony przez nowy tekst, bieżący zakres tekstu staje się nieprawidłowy. Jednak zakres tekstu nadal obowiązują pewne żywotności jeśli tylko część oryginalny tekst zostanie zmieniony i zarządza jego tekstu podstawowego kontrolki tekstu "wskaźnik" za pomocą kotwice (lub punktów końcowych), a nie z położenia bezwzględne znaków.<br /><br /> Klienci mogą nasłuchiwać <xref:System.Windows.Automation.TextPattern.TextChangedEvent> powiadomienia o wszelkich zmianach w zawartości tekstowej pracują.|  
|`System.Windows.Automation.AutomationTextAttribute Class`|Używany do identyfikowania atrybutach formatowania tekstu zakresu.|  
  
<a name="TextPattern_Provider_API_s"></a>   
## <a name="textpattern-provider-apis"></a>TextPattern dostawcy interfejsu API  
 Elementy interfejsu użytkownika lub kontrolki obsługujące <xref:System.Windows.Automation.TextPattern> implementując <xref:System.Windows.Automation.Provider.ITextProvider> i <xref:System.Windows.Automation.Provider.ITextRangeProvider> interfejsy, albo natywnie lub za pomocą [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] serwerów proxy, są w stanie ujawnienia atrybut szczegółowe informacje dotyczące dowolny tekst, które zawierają w Dodatek zapewnia niezawodne możliwości nawigacji.  
  
 Element <xref:System.Windows.Automation.TextPattern> nie ma dostawcy do obsługi wszystkich atrybutów tekstu, jeśli kontrolka brakuje obsługi wszelkie określone atrybuty.  
  
 A <xref:System.Windows.Automation.TextPattern> dostawca musi obsługiwać <xref:System.Windows.Automation.TextPattern.GetSelection%2A> i <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> funkcji, jeśli są obsługiwane przez kontrolkę zaznaczonego tekstu lub położenia kursora tekstu (lub daszek system) w ramach obszaru tekstu. Jeśli formant nie obsługuje tej funkcji go nie należy do żadnej z tych metod obsługi. Jednak formant należy ujawnić rodzaj zaznaczenia tekstu obsługuje implementując <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> właściwości.  
  
 A <xref:System.Windows.Automation.TextPattern> dostawcy zawsze musi obsługiwać <xref:System.Windows.Automation.Text.TextUnit> stałe <xref:System.Windows.Automation.Text.TextUnit.Character> i <xref:System.Windows.Automation.Text.TextUnit.Document> oraz wszelkich innych <xref:System.Windows.Automation.Text.TextUnit> stałe będzie w stanie obsłużyć.  
  
> [!NOTE]
>  Dostawca może pominąć pomocy technicznej dla określonego <xref:System.Windows.Automation.Text.TextUnit> przez odkładania do następnej największy <xref:System.Windows.Automation.Text.TextUnit> obsługiwane w następującej kolejności: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>, i <xref:System.Windows.Automation.Text.TextUnit.Document> .  
  
|||  
|-|-|  
|`ITextProvider Interface`|Udostępnia metody, właściwości i atrybutów, które obsługują <xref:System.Windows.Automation.TextPattern> w aplikacjach klienckich (zobacz <xref:System.Windows.Automation.Provider.ITextProvider>).|  
|`ITextRangeProvider Interface`|Reprezentuje fragment tekstu w dostawcy tekstu (zobacz <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|  
|`System.Windows.Automation.TextPatternIdentifiers Class`|Zawiera wartości, które są używane jako identyfikatory dla dostawców tekstu (zobacz <xref:System.Windows.Automation.TextPatternIdentifiers>).|  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpieczenia  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Architektura została zaprojektowana z myślą o bezpieczeństwie (zobacz [Przegląd zabezpieczeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-security-overview.md)). Opisane w tym omówieniu klasy TextPattern wymagają jednak pewne zagadnienia dotyczące zabezpieczeń.  
  
-   [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tekst dostawców podać interfejsach tylko do odczytu i nie są oferowane możliwości zmiany istniejącego tekstu w kontrolce.  
  
-   Klienci automatyzacji interfejsu użytkownika można używać tylko [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jeśli są w pełni "Zaufane". Na przykład będzie chroniony pulpitu logowania, gdzie można uruchomić aplikacje tylko ze znanych i zaufanych.  
  
-   Deweloperzy dostawców automatyzacji interfejsu użytkownika, należy pamiętać, że wszystkie informacje zdecydują się na udostępnianych w ich kontrolami za pośrednictwem [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zasadniczo publiczne i jest w pełni dostępna przez inny kod. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] nie podejmuje żadnych działań w celu określenia stopnia dowolnego klienta automatyzacji interfejsu użytkownika i w związku z tym dostawcy automatyzacji interfejsu użytkownika nie powinny ujawniać chronionych informacji tekstowych treści lub poufnych (na przykład hasło, pola).  
  
-   Jedną z najbardziej znaczących zmian w usłudze security dla [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] szeroko nazywa się "Secure Input" obejmującym technologii, takich jak najmniej uprzywilejowane (lub ograniczony) konta użytkownika (LUA) i izolacji poziom uprawnień podsystemu (UIPI) interfejsu użytkownika.  
  
    -   Podsystemu UIPI zapobiega jeden program z kontroli i/lub innego więcej "uprzywilejowanych" program monitorowania, zapobieganie atakom komunikat okna między procesami, które podszywały się pod dane wejściowe użytkownika.  
  
    -   LUA Ustawia limity uprawnienia aplikacji, które są uruchamiane przez użytkowników w grupie Administratorzy. Aplikacje nie musi mieć uprawnienia administratora, ale zamiast tego zostanie uruchomiony z minimalnych niezbędnych uprawnień. W konsekwencji mogą istnieć pewne ograniczenia wymuszane w scenariuszach LUA. Głównie ciągu obcięcie (takie jak ciągi TextPattern), gdzie może być konieczne limit rozmiaru ciągi pobierane z aplikacji na poziomie administratora, aby nie musieli przydzielić pamięci w punkcie wyłączenia aplikacji.  
  
<a name="Performance"></a>   
## <a name="performance"></a>Wydajność  
 Ponieważ TextPattern opiera się na wywołania między procesami dla większości jej funkcji, nie zapewnia mechanizm buforowania w celu zwiększenia wydajności podczas przetwarzania zawartości. Jest to w przeciwieństwie do innych wzorców kontrolki w [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , można uzyskać dostęp za pomocą <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> metody.  
  
 Jeden taktyką poprawę wydajności energii jest upewnienie się klientów automatyzacji interfejsu użytkownika podejmowane próby pobierania średnio o rozmiarze bloki tekstu przy użyciu języka <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Na przykład GetText(1) wywołania spowoduje naliczenie opłaty za między procesami trafień dla każdego znaku jedno wywołanie GetText(-1) spowoduje naliczenie opłaty za jeden trafień między procesami, ale może mieć duże opóźnienie w zależności od wielkości dostawca tekstu.  
  
<a name="Glossary"></a>   
## <a name="textpattern-terminology"></a>Terminologia TextPattern  
 **Atrybut**  
 Formatowania charakterystyka zakres tekstu (na przykład <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> lub <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).  
  
 **Wymiar degeneracji zakresu**  
 Wymiaru degeneracji zakres to zakres tekstu pusta lub zero znaków. Celów TextPattern — wzorzec kontrolki umieść punkt wstawiania (lub daszek system) są uznawane za wymiaru degeneracji zakresu. Jeśli nie wybrano tekstu, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> zwróci wymiaru degeneracji zakresu w punkcie wstawiania tekstu i <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> zwróci wymiaru degeneracji zakresu jako jego początkowy punkt końcowy. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> i <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> może zwrócić wymiaru degeneracji zakresów, kiedy dostawca tekst nie może odnaleźć żadnych zakresów tekstu, spełniające dany warunek. Ten zakres wymiaru degeneracji służy jako początkowy punkt końcowy przy użyciu dostawcy tekstu. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> i <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> zwrócić odwołanie o wartości null (`Nothing` w Microsoft Visual Basic .NET) aby uniknąć mylenia go z zakresem odnalezionych w stosunku do wymiaru degeneracji zakresu.  
  
 **Obiekt osadzony**  
 Istnieją dwa typy osadzonych obiektów w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] modelu tekstu. Składają się one oparte na tekście elementów zawartości, takie jak hiperłącza lub tabele i kontrolki elementów, takich jak obrazy i przyciski. Aby uzyskać więcej informacji, zobacz [dostępu do osadzonych obiektów przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md).  
  
 **Punkt końcowy**  
 Bezwzględna <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> lub <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> punkt zakresu tekstu w kontenerze tekstu.  
  
 ![Wartości TextPatternRangeEndpoints &#40;początek i koniec&#41;. ](../../../docs/framework/ui-automation/media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")  
Poniżej przedstawiono zestaw punkt początkowy i końcowy.  
  
 **TextRange**  
 Reprezentacja fragment tekstu za pomocą początkowego i punktu końcowego, w kontenerze tekstu, w tym wszystkie skojarzone atrybutów i funkcje.  
  
 <xref:System.Windows.Automation.Text.TextUnit>  
 Wstępnie zdefiniowane jednostka tekst (znak, word, wiersza lub akapitu) używany do przechodzenia między logiczne segmenty zakres tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Tekst usługi Framework](https://msdn.microsoft.com/library/default.asp?url=/library/tsf/tsf/text_services_framework.asp)
