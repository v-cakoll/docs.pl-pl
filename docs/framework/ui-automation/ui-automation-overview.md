---
title: "Przegląd automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
caps.latest.revision: "35"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d86c70ec4421bc716b12044bac30f8f925c375f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-overview"></a>Przegląd automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]to nowa struktura ułatwień dostępu dla [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], dostępne we wszystkich systemach operacyjnych, które obsługują [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zapewnia dostęp programistyczny do większości [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów na pulpicie, włączanie produktów technologii pomocniczej, takich jak czytniki o podanie informacji o ekranu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] dla użytkowników końcowych i do manipulowania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] znaczy innych niż standardowe dane wejściowe. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Umożliwia również skrypty testów automatycznych do interakcji z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nie umożliwia komunikację między procesy uruchomione przez różnych użytkowników za pomocą **Uruchom jako** polecenia.  
  
 Aplikacje klienckie automatyzacji interfejsu użytkownika mogą być napisane z gwarantują, że będą one działać na wielu platformach. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core maski różnice w platform, które opierają się różnymi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Na przykład `Content` właściwość [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przycisku `Caption` właściwość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] przycisku i `ALT` właściwości obrazu HTML są zamapowane na jedną właściwość <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]oferuje wszystkie funkcje w [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)], i [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)].  
  
 Dostawcy automatyzacji interfejsu użytkownika oferują niektórych obsługę [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] aplikacje klienckie za pośrednictwem wbudowanego mostkowania usługi.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Dostawców i klientów  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ma cztery główne składniki, jak pokazano w poniższej tabeli.  
  
|Składnik|Opis|  
|---------------|-----------------|  
|Dostawca [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] (UIAutomationProvider.dll i UIAutomationTypes.dll)|Zestaw definicji interfejsu, które są implementowane przez dostawców automatyzacji interfejsu użytkownika, obiekty, które dostarczają informacje na temat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów i odpowiadać na programowe danych wejściowych.|  
|Klienta interfejsu API (UIAutomationClient.dll i UIAutomationTypes.dll)|Zestaw typów dla zarządzanego kodu, który umożliwia aplikacjom klienta automatyzacji interfejsu użytkownika uzyskać informacje na temat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] i wysyłanie danych wejściowych do kontrolek.|  
|Bibliotekę UiAutomationCore.dll|Kod źródłowy (nazywane również [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core) obsługującego komunikację między dostawców i klientów.|  
|UIAutomationClientsideProviders.dll|Zestaw dostawców automatyzacji interfejsu użytkownika dla formantów standardowych starszej wersji. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] formanty mają macierzystą obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].) Ta obsługa jest automatycznie dostępny dla aplikacji klienckich.|  
  
 Z perspektywy deweloperów oprogramowania istnieją dwa sposoby używania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: do utworzenia obsługę formanty niestandardowe (przy użyciu interfejsu API dostawcy) i tworzenia aplikacji, które używają [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core do komunikowania się z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów (za pomocą Interfejs API klienta). W zależności od zespół należy zapoznać się do różnych części dokumentacji. Możesz dowiedzieć się więcej o koncepcjach i uzyskania porad wiedzy praktycznej w poniższych sekcjach.  
  
|Sekcja|Ek|Odbiorcy|  
|-------------|--------------------|--------------|  
|[Podstawowe założenia automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/index.md) (tej sekcji)|Szerokie omówienie pojęć.|Wszystkie.|  
|[Dostawcy automatyzacji interfejsu użytkownika do kodu zarządzanego](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|Omówienie i — tematy porad ułatwiających korzystanie z interfejsu API dostawcy.|Deweloperzy formantu.|  
|[Klienci automatyzacji interfejsu użytkownika do kodu zarządzanego](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|Omówienie i — tematy porad ułatwiających korzystanie z klienta interfejsu API.|Deweloperzy aplikacji klienta.|  
|[Wzorce kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|Informacje dotyczące implementowania wzorców formantu przez dostawców i jakie funkcje są dostępne dla klientów.|Wszystkie.|  
|[Wzorzec tekstu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|Informacje dotyczące implementowania wzorzec tekstu formantu przez dostawców i jakie funkcje są dostępne dla klientów.|Wszystkie.|  
|[Typy kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types.md)|Informacje o obsługiwanych przez różne typy formantów wzorce właściwości i kontroli.|Wszystkie.|  
  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przestrzeni nazw, bibliotek DLL, które zawierają i który używa tych odbiorców.  
  
|Przestrzeń nazw|Przywoływane biblioteki dll|Odbiorcy|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Automatyzacja interfejsu użytkownika klienta deweloperzy; Umożliwia znalezienie <xref:System.Windows.Automation.AutomationElement> obiektów, zarejestruj się w celu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń i pracować z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorce.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Deweloperzy dostawców automatyzacji interfejsu użytkownika dla struktur innych niż [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Deweloperzy dostawców automatyzacji interfejsu użytkownika dla struktur innych niż [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; używane do implementowania TextPattern — wzorzec formantu.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Deweloperzy dostawców automatyzacji interfejsu użytkownika dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Model automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]przedstawia każdą [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] dla aplikacji klienckich jako <xref:System.Windows.Automation.AutomationElement>. Elementy są zawarte w strukturze drzewa z pulpitem jako element główny. Klientów można filtrować raw widoku drzewa jako formant widoku lub widok zawartości. Aplikacje można również tworzyć widoki niestandardowe.  
  
 <xref:System.Windows.Automation.AutomationElement>wspólne właściwości uwidacznia obiekty [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy reprezentują. Jedną z tych właściwości jest typ formantu, który definiuje jego podstawowe wygląd i działanie jako pojedynczy element rozpoznawalnych: na przykład przycisk lub pole wyboru.  
  
 Ponadto elementy ujawnia wzorców formantu, udostępniające właściwości specyficzne dla ich typy formantów. Wzorce formantu również ujawniać metod, które umożliwiają klientów, aby uzyskać więcej informacji na temat elementu, a podawanie danych wejściowych.  
  
> [!NOTE]
>  Nie ma odpowiednika między typami kontroli i wzorce formantu. Wzorzec formantu może być obsługiwana przez wiele typów kontroli, a formant może obsługiwać wielu wzorców formantu, z których każdy ujawnia różne aspekty zachowania. Na przykład pole kombi ma co najmniej dwa wzorce kontrolki: odpowiadającą jej możliwość rozwijanie i zwijanie i drugiej, który reprezentuje mechanizm wyboru. Aby uzyskać szczegóły, zobacz [typy formantów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zawiera także informacje dla aplikacji klienckich za pomocą zdarzeń. W odróżnieniu od [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)], [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia nie są oparte na mechanizmie emisji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Klienci zarejestrować odbieranie powiadomień konkretnego zdarzenia i może zażądać tego konkretnego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] przekazywanie informacji wzorzec właściwości i kontroli do swoich programów obsługi zdarzeń. Ponadto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia zawiera odwołanie do elementu, do którego on uruchamiany. Dostawców można zwiększyć wydajność przez wywoływanie zdarzeń selektywnie, w zależności od tego, czy nasłuchują wszystkich klientów.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [Przegląd zabezpieczeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
