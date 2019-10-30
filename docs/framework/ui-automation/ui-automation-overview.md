---
title: Przegląd automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 6e5501b152c4662f1456786ba51fd3f25923b34c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040543"
---
# <a name="ui-automation-overview"></a>Przegląd automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to nowa platforma dostępności dla systemu Microsoft Windows, dostępna we wszystkich systemach operacyjnych, które obsługują [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zapewnia programistyczny dostęp do większości [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów na pulpicie, włączając w to produkty technologii pomocniczej, takie jak czytniki zawartości ekranu, aby dostarczyć informacje o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] użytkownikom końcowym i manipulowaniu nimi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] przy użyciu metody innej niż standardowa klawiatur. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] również umożliwia automatyczne uruchamianie skryptów testowych w celu współdziałania z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie umożliwia komunikacji między procesami uruchomionymi przez różnych użytkowników za pomocą polecenia **Uruchom jako** .  
  
 Aplikacje klienckie automatyzacji interfejsu użytkownika mogą być zapisywane z gwarancją, że będą działać w wielu strukturach. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podstawowe maskuje wszelkie różnice w strukturach, które podstawą różne fragmenty [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Na przykład właściwość `Content` przycisku [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], właściwość `Caption` przycisku [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] i Właściwość `ALT` obrazu HTML są zamapowane na pojedynczą właściwość, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, w widoku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
Automatyzacja interfejsu użytkownika zapewnia pełną funkcjonalność obsługiwanych systemów operacyjnych Windows, na których działa .NET Framework (zobacz [.NET Framework wymagania systemowe](../get-started/system-requirements.md) lub wersje platformy .NET Core, począwszy od platformy .net Core 3,0.  
  
 Dostawcy automatyzacji interfejsu użytkownika oferują pewne wsparcie dla aplikacji klienckich Microsoft Active Accessibility za pomocą wbudowanej usługi mostkowania.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Dostawcy i klienci  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ma cztery główne składniki, jak pokazano w poniższej tabeli.  
  
|Składnik|Opis|  
|---------------|-----------------|  
|Interfejs API dostawcy (UIAutomationProvider. dll i UIAutomationTypes. dll)|Zestaw definicji interfejsu, które są implementowane przez dostawców automatyzacji interfejsu użytkownika, obiektów, które zawierają informacje o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementach i reagują na wprowadzanie programistyczne.|  
|Interfejs API klienta (UIAutomationClient. dll i UIAutomationTypes. dll)|Zestaw typów dla kodu zarządzanego, który umożliwia aplikacjom klienckim automatyzacji interfejsu użytkownika uzyskiwanie informacji o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] i wysyłanie danych wejściowych do kontrolek.|  
|UiAutomationCore. dll|Kod źródłowy (nazywany czasem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rdzeń), który obsługuje komunikację między dostawcami i klientami.|  
|UIAutomationClientsideProviders. dll|Zestaw dostawców automatyzacji interfejsu użytkownika dla standardowych, starszych kontrolek. (formanty [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] mają natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]). Ta obsługa jest automatycznie dostępna dla aplikacji klienckich.|  
  
 Z punktu widzenia deweloperów oprogramowania istnieją dwa sposoby używania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: Aby utworzyć obsługę niestandardowych kontrolek (przy użyciu interfejsu API dostawcy) i utworzyć aplikacje używające rdzenia [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do komunikowania się z elementami [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] (przy użyciu interfejsu API klienta). W zależności od fokusu należy zapoznać się z różnymi częściami dokumentacji. Możesz dowiedzieć się więcej na temat koncepcji i uzyskać praktyczne informacje o wiedzy w poniższych sekcjach.  
  
|Paragraf|Temat|Odbiorcy|  
|-------------|--------------------|--------------|  
|[Podstawy automatyzacji interfejsu użytkownika](index.md) (w tej sekcji)|Szerokie przeglądy koncepcji.|Wszystkie.|  
|[Dostawcy automatyzacji interfejsu użytkownika do kodu zarządzanego](ui-automation-providers-for-managed-code.md)|Przeglądy i Tematy porad ułatwiające korzystanie z interfejsu API dostawcy.|Kontroluj deweloperów.|  
|[Klienci automatyzacji interfejsu użytkownika do kodu zarządzanego](ui-automation-clients-for-managed-code.md)|Przeglądy i Tematy porad ułatwiające korzystanie z interfejsu API klienta.|Deweloperzy aplikacji klienckich.|  
|[Wzorce kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns.md)|Informacje dotyczące sposobu, w jaki wzorce kontroli powinny być implementowane przez dostawców i jakie funkcje są dostępne dla klientów.|Wszystkie.|  
|[Wzorzec tekstu automatyzacji interfejsu użytkownika](ui-automation-text-pattern.md)|Informacje dotyczące sposobu, w jaki wzorzec kontrolki tekstu powinien być zaimplementowany przez dostawców i jakie funkcje są dostępne dla klientów.|Wszystkie.|  
|[Typy kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-types.md)|Informacje na temat właściwości i wzorców formantów obsługiwanych przez różne typy kontrolek.|Wszystkie.|  
  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przestrzenie nazw, biblioteki DLL, które je zawierają, oraz odbiorców, którzy z nich korzystają.  
  
|Przestrzeń nazw|Przywoływane biblioteki DLL|Odbiorcy|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Deweloperzy klienta automatyzacji interfejsu użytkownika; służy do znajdowania obiektów <xref:System.Windows.Automation.AutomationElement>, rejestrowania dla zdarzeń [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i pracy ze wzorcami kontroli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Deweloperzy dostawcy automatyzacji interfejsu użytkownika dla platform innych niż [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Deweloperzy dostawcy automatyzacji interfejsu użytkownika dla platform innych niż [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; służy do implementowania wzorca kontrolki TextPattern.|  
|<xref:System.Windows.Automation.Peers>|Platformie docelowej|Deweloperzy dostawcy automatyzacji interfejsu użytkownika dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Model automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] uwidacznia każdą część [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] do aplikacji klienckich jako <xref:System.Windows.Automation.AutomationElement>. Elementy są zawarte w strukturze drzewa, z pulpitem jako element główny. Klienci mogą filtrować nieprzetworzony widok drzewa jako widok kontrolki lub widok zawartości. Aplikacje mogą również tworzyć widoki niestandardowe.  
  
 obiekty <xref:System.Windows.Automation.AutomationElement> uwidaczniają typowe właściwości elementów [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], które reprezentują. Jedną z tych właściwości jest typ kontrolki, który definiuje podstawowy wygląd i funkcjonalność jako pojedynczą rozpoznawalną jednostkę: na przykład przycisk lub pole wyboru.  
  
 Ponadto elementy uwidaczniają wzorce kontroli, które udostępniają właściwości specyficzne dla ich typów kontrolek. Wzorce kontroli udostępniają również metody, które umożliwiają klientom uzyskanie dalszych informacji na temat elementu i dostarczenie danych wejściowych.  
  
> [!NOTE]
> Między typami formantów i wzorcami formantów nie istnieje taka sama zgodność. Wzorzec kontrolki może być obsługiwany przez wiele typów formantów, a kontrolka może obsługiwać wiele wzorców kontroli, z których każdy ujawnia różne aspekty jego działania. Na przykład pole kombi ma co najmniej dwa wzorce kontroli: jeden, który reprezentuje jego zdolność do rozwijania i zwijania, i drugi, który reprezentuje mechanizm wyboru. Aby uzyskać szczegółowe informacje, zobacz [typy formantów automatyzacji interfejsu użytkownika](ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] udostępnia również informacje dotyczące aplikacji klienckich za poorednictwem zdarzeń. W przeciwieństwie do [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)]zdarzenia [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie są oparte na mechanizmie emisji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienci rejestrują się do określonych powiadomień o zdarzeniach i mogą żądać, aby określone właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i informacje o wzorcu formantów były przekazywane do ich obsługi zdarzeń. Ponadto zdarzenie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zawiera odwołanie do elementu, który go spowodował. Dostawcy mogą zwiększyć wydajność, wybierając wybiórcze zdarzenia, w zależności od tego, czy klienci nasłuchuje.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Przegląd właściwości automatyzacji interfejsu użytkownika](ui-automation-properties-overview.md)
- [Przegląd zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md)
- [Przegląd zabezpieczeń automatyzacji interfejsu użytkownika](ui-automation-security-overview.md)
