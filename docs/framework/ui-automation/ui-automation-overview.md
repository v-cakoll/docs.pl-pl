---
title: Przegląd automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 04abb999ae232d2dd49b1fad8887a596530ea369
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48782119"
---
# <a name="ui-automation-overview"></a>Przegląd automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to nowe środowisko ułatwień dostępu do [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], która jest dostępna we wszystkich systemach operacyjnych, które obsługują [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zapewnia dostęp programistyczny do większości [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów na komputerze stacjonarnym, takich jak włączenie produktów technologii pomocniczej ekranu odbiorcy, aby podać informacje o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] dla użytkowników końcowych i manipulować [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] przez oznacza, że inne niż standardowe dane wejściowe. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Umożliwia także skrypty testów automatycznych do interakcji z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie obsługuje komunikacji między procesy uruchomione przez różnych użytkowników za pośrednictwem **Uruchom jako** polecenia.  
  
 Aplikacje klienckie automatyzacji interfejsu użytkownika mogą być napisane mając pewność, że będą one działać na wielu platformach. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core maskuje żadnych różnic w struktur, które opierają się różnymi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Na przykład `Content` właściwość [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przycisku `Caption` właściwość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] przycisku i `ALT` właściwości obrazu HTML są mapowane na jedną właściwość <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zapewnia pełną funkcjonalność w [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)], i [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)].  
  
 Dostawcy automatyzacji interfejsu użytkownika oferują pewne obsługę [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] aplikacje klienckie, za pomocą wbudowanej usługi mostkowania.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Dostawcami i klientami  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ma cztery główne składniki, jak pokazano w poniższej tabeli.  
  
|Składnik|Opis|  
|---------------|-----------------|  
|Dostawca [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] (UIAutomationProvider.dll i UIAutomationTypes.dll)|Zbiór definicji interfejsów, które są implementowane przez dostawców automatyzacji interfejsu użytkownika, obiekty, które dostarczają informacje na temat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów i reagowanie na wprowadzanie programowe.|  
|Klient interfejsu API (UIAutomationClient.dll i UIAutomationTypes.dll)|Zestaw typów dla kodu zarządzanego, który umożliwia aplikacjom klienta automatyzacji interfejsu użytkownika uzyskać informacje na temat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] i wysłać danych wejściowych do kontrolek.|  
|Bibliotekę UiAutomationCore.dll|Podstawowy kod (nazywane czasem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core) obsługującego komunikację między dostawcami i klientami.|  
|UIAutomationClientsideProviders.dll|Zestaw dostawców automatyzacji interfejsu użytkownika dla standardowych kontrolek starszej wersji. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] formanty mają natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].) Ta funkcja jest automatycznie dostępne dla aplikacji klienckich.|  
  
 Z perspektywy deweloperów oprogramowania, istnieją dwa sposoby korzystania z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: do utworzenia pomocy technicznej w przypadku kontrolek niestandardowych (przy użyciu dostawcy interfejsu API) i tworzenia aplikacji wykorzystujących [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core do komunikowania się z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów (przy użyciu Klient interfejsu API). W zależności od Twojego zespołu należy zapoznać się do różnych części dokumentacji. Można dowiedzieć się więcej na temat pojęć i uzyskiwanie porad wiedzy w poniższych sekcjach.  
  
|Sekcja|Posiadaczem|Odbiorcy|  
|-------------|--------------------|--------------|  
|[Podstawowe założenia automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/index.md) (w tej sekcji)|Szerokiego omówienia pojęć.|Wszystkie.|  
|[Dostawcy automatyzacji interfejsu użytkownika do kodu zarządzanego](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|Omówienie i porad ułatwiających stosowanie interfejs API dostawcy.|Deweloperzy kontroli.|  
|[Klienci automatyzacji interfejsu użytkownika do kodu zarządzanego](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|Omówienie i porad ułatwiających korzystanie z klienta interfejsu API.|Deweloperzy aplikacji klienckich.|  
|[Wzorce kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|Informacje o implementacji wzorców kontrolek przez dostawców i jakie funkcje są dostępne dla klientów.|Wszystkie.|  
|[Wzorzec tekstu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|Informacje o implementacji wzorca kontrolki tekstu przez dostawców i jakie funkcje są dostępne dla klientów.|Wszystkie.|  
|[Typy kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types.md)|Informacje o wzorcach właściwości oraz kontrolki, obsługiwane przez różne typy formantów.|Wszystkie.|  
  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przestrzeni nazw, zawierające je i odbiorców, którzy są one używane przez biblioteki dll.  
  
|Przestrzeń nazw|Powiązane biblioteki dll|Odbiorcy|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Automatyzacja interfejsu użytkownika klienta deweloperom; używana do znajdowania <xref:System.Windows.Automation.AutomationElement> obiektów, zarejestruj się, aby [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń i pracować z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorców.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Deweloperzy dostawców automatyzacji interfejsu użytkownika dla platform innych niż [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Deweloperzy dostawców automatyzacji interfejsu użytkownika dla platform innych niż [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; jest używany do implementowania TextPattern — wzorzec kontrolki.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Deweloperzy dostawców automatyzacji interfejsu użytkownika dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Model automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Każdy element przedstawia [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aplikacjom klienckim jako <xref:System.Windows.Automation.AutomationElement>. Elementy są zawarte w strukturze drzewa w programie desktop jako elementu głównego. Klientów można filtrować nieprzetworzony widok drzewa jako kontrolki widoku lub widok zawartości. Aplikacje można również utworzyć niestandardowe widoki.  
  
 <xref:System.Windows.Automation.AutomationElement> obiekty Udostępnianie wspólnych właściwości [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy reprezentują one. Jedną z tych właściwości jest typ kontroli, który definiuje jego podstawowy wygląd i działanie jako pojedynczy element rozpoznawalnych: na przykład przycisk lub okienka do zaznaczenia.  
  
 Ponadto elementy uwidocznić wzorców kontrolek, udostępniające właściwości specyficzne dla ich typy kontroli. Wzorce kontrolki również ujawniać metod, które umożliwiają klientom uzyskania dalszych informacji na temat elementu i podanie danych wejściowych.  
  
> [!NOTE]
>  Nie ma relację między typami kontroli i wzorce kontrolki. Wzorzec kontrolki mogą być obsługiwane przez wiele typów kontroli, a formant może obsługiwać wiele wzorców kontrolek, z których każdy ujawnia różne aspekty swojego zachowania. Na przykład pole kombi ma co najmniej dwa wzorce kontrolki: jeden, który reprezentuje jej możliwości, aby rozwinąć lub zwinąć i drugiego, który reprezentuje mechanizm zaznaczania. Aby uzyskać szczegółowe informacje, zobacz [typy kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawiera również informacje dla aplikacji klienckich za pomocą zdarzeń. W odróżnieniu od [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)], [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia nie są oparte na mechanizmie emisji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zarejestrowanie powiadomień o zdarzeniach określonych klientów i mogą żądać tego konkretnego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości i wzorzec informacje sterujące przekazania do swoich programów obsługi zdarzeń. Ponadto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenie zawiera odwołanie do elementu, który go spowodował. Dostawców może zwiększyć wydajność przez wywoływanie zdarzeń selektywnie, w zależności od tego, czy wszyscy klienci są nasłuchiwania.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [Przegląd zabezpieczeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
