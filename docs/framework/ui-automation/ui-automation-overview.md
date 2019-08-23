---
title: Przegląd automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: af4abf060e9a8606f69a94f27ecd76487a2ff51c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914593"
---
# <a name="ui-automation-overview"></a>Przegląd automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]to nowa platforma dostępności dla programu [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], dostępna we wszystkich systemach operacyjnych obsługiwanych [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]przez program.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zapewnia programistyczny dostęp do [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] większości elementów na pulpicie, co umożliwia produkty technologii pomocniczej, takie jak czytniki zawartości ekranu, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aby zapewnić [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] użytkownikom końcowym informacje i manipulować nimi w sposób inny niż standardowe dane wejściowe. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umożliwia również automatyczne uruchamianie skryptów testowych w celu współdziałania z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nie umożliwia komunikacji między procesami uruchomionymi przez różnych użytkowników za pomocą polecenia **Uruchom jako** .  
  
 Aplikacje klienckie automatyzacji interfejsu użytkownika mogą być zapisywane z gwarancją, że będą działać w wielu strukturach. Podstawowe maskuje wszelkie różnice w strukturach, które podstawą różne [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]fragmenty. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Na `Content` przykład [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>przycisku `Caption` , właściwość `ALT` przycisku i właściwość obrazu HTML są zamapowane na pojedynczą właściwość, w tym widoku. [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zapewnia pełną funkcjonalność w [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)]i [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)].  
  
 Dostawcy automatyzacji interfejsu użytkownika oferują pewne wsparcie dla aplikacji klienckich Microsoft Active Accessibility przy użyciu wbudowanej usługi mostkowania.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Dostawcy i klienci  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Program ma cztery główne składniki, jak pokazano w poniższej tabeli.  
  
|Składnik|Opis|  
|---------------|-----------------|  
|Interfejs API dostawcy (UIAutomationProvider. dll i UIAutomationTypes. dll)|Zestaw definicji interfejsu, które są implementowane przez dostawców automatyzacji interfejsu użytkownika, obiekty, które dostarczają [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] informacji o elementach i reagują na dane wejściowe programistyczne.|  
|Interfejs API klienta (UIAutomationClient. dll i UIAutomationTypes. dll)|Zestaw typów dla kodu zarządzanego, który umożliwia aplikacjom klienckim automatyzacji interfejsu użytkownika uzyskiwanie informacji na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] temat i wysyłanie danych wejściowych do kontrolek.|  
|UiAutomationCore.dll|Kod źródłowy (nazywany [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] czasem rdzeniem), który obsługuje komunikację między dostawcami i klientami.|  
|UIAutomationClientsideProviders.dll|Zestaw dostawców automatyzacji interfejsu użytkownika dla standardowych, starszych kontrolek. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] formanty mają natywną [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obsługę.) Ta obsługa jest automatycznie dostępna dla aplikacji klienckich.|  
  
 Z punktu widzenia deweloperów oprogramowania istnieją dwa sposoby użycia [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: w celu utworzenia obsługi niestandardowych kontrolek (przy użyciu interfejsu API dostawcy) i tworzenia aplikacji, które [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] używają rdzenia do komunikacji z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementami (za pomocą Interfejs API klienta programu). W zależności od fokusu należy zapoznać się z różnymi częściami dokumentacji. Możesz dowiedzieć się więcej na temat koncepcji i uzyskać praktyczne informacje o wiedzy w poniższych sekcjach.  
  
|`Section`|Temat|Odbiorcy|  
|-------------|--------------------|--------------|  
|[Podstawy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/index.md) (w tej sekcji)|Szerokie przeglądy koncepcji.|Wszystkie.|  
|[Dostawcy automatyzacji interfejsu użytkownika do kodu zarządzanego](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|Przeglądy i Tematy porad ułatwiające korzystanie z interfejsu API dostawcy.|Kontroluj deweloperów.|  
|[Klienci automatyzacji interfejsu użytkownika do kodu zarządzanego](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|Przeglądy i Tematy porad ułatwiające korzystanie z interfejsu API klienta.|Deweloperzy aplikacji klienckich.|  
|[Wzorce kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|Informacje dotyczące sposobu, w jaki wzorce kontroli powinny być implementowane przez dostawców i jakie funkcje są dostępne dla klientów.|Wszystkie.|  
|[Wzorzec tekstu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|Informacje dotyczące sposobu, w jaki wzorzec kontrolki tekstu powinien być zaimplementowany przez dostawców i jakie funkcje są dostępne dla klientów.|Wszystkie.|  
|[Typy kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types.md)|Informacje na temat właściwości i wzorców formantów obsługiwanych przez różne typy kontrolek.|Wszystkie.|  
  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przestrzenie nazw, biblioteki DLL, które je zawierają, oraz odbiorców, którzy z nich korzystają.  
  
|Przestrzeń nazw|Przywoływane biblioteki DLL|Odbiorcy|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Deweloperzy klienta automatyzacji interfejsu użytkownika; służy do znajdowania <xref:System.Windows.Automation.AutomationElement> obiektów, rejestrowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dla zdarzeń i pracy ze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorcami kontrolek.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Deweloperzy dostawcy automatyzacji interfejsu użytkownika dla platform innych niż [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Deweloperzy dostawcy automatyzacji interfejsu użytkownika dla platform innych niż [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; używane do implementowania wzorca kontrolki TextPattern.|  
|<xref:System.Windows.Automation.Peers>|Platformie docelowej|Deweloperzy dostawcy automatyzacji interfejsu użytkownika dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]programu.|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Model automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]uwidacznia każdą część [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aplikacji klienckich <xref:System.Windows.Automation.AutomationElement>jako. Elementy są zawarte w strukturze drzewa, z pulpitem jako element główny. Klienci mogą filtrować nieprzetworzony widok drzewa jako widok kontrolki lub widok zawartości. Aplikacje mogą również tworzyć widoki niestandardowe.  
  
 <xref:System.Windows.Automation.AutomationElement>obiekty uwidaczniają typowe właściwości elementów [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , które reprezentują. Jedną z tych właściwości jest typ kontrolki, który definiuje podstawowy wygląd i funkcjonalność jako pojedynczą rozpoznawalną jednostkę: na przykład przycisk lub pole wyboru.  
  
 Ponadto elementy uwidaczniają wzorce kontroli, które udostępniają właściwości specyficzne dla ich typów kontrolek. Wzorce kontroli udostępniają również metody, które umożliwiają klientom uzyskanie dalszych informacji na temat elementu i dostarczenie danych wejściowych.  
  
> [!NOTE]
> Między typami formantów i wzorcami formantów nie istnieje taka sama zgodność. Wzorzec kontrolki może być obsługiwany przez wiele typów formantów, a kontrolka może obsługiwać wiele wzorców kontroli, z których każdy ujawnia różne aspekty jego działania. Na przykład pole kombi ma co najmniej dwa wzorce kontroli: jeden, który reprezentuje jego zdolność do rozwijania i zwijania, i drugi, który reprezentuje mechanizm wyboru. Aby uzyskać szczegółowe informacje, zobacz [typy formantów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Program udostępnia również informacje dotyczące aplikacji klienckich za poorednictwem zdarzeń. W przeciwieństwie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)], zdarzenia nie są oparte na mechanizmie emisji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Klienci rejestrują się do określonych powiadomień o zdarzeniach i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mogą żądać przekazywania określonych właściwości i informacji o wzorcu kontroli do ich obsługi zdarzeń. Ponadto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenie zawiera odwołanie do elementu, który go spowodował. Dostawcy mogą zwiększyć wydajność, wybierając wybiórcze zdarzenia, w zależności od tego, czy klienci nasłuchuje.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [Przegląd zabezpieczeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
