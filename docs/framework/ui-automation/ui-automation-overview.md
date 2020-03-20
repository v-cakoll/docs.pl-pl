---
title: Przegląd automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 6f938302967e1b519105769717d326e5042a7bce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179920"
---
# <a name="ui-automation-overview"></a>Przegląd automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]to nowa struktura ułatwień dostępu dla systemu Microsoft [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows, dostępna we wszystkich systemach operacyjnych obsługujących program .  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zapewnia programowy dostęp [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] do większości elementów na pulpicie, umożliwiając produkty technologii [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wspomagających, takie jak [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] czytniki ekranu, dostarczanie informacji o użytkownikach końcowych i manipulowanie nimi za pomocą środków innych niż standardowe dane wejściowe. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umożliwia również automatyczne skrypty testowe do interakcji z . [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nie umożliwia komunikacji między procesami uruchamiane przez różnych użytkowników za pośrednictwem polecenia **Uruchom jako.**  
  
 Aplikacje klienckie automatyzacji interfejsu użytkownika mogą być zapisywane z zapewnieniem, że będą działać na wielu platformach. Rdzeń [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] maskuje wszelkie różnice w ramach, które stanowią [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]podstawę różnych kawałków . Na przykład `Content` właściwość [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przycisku, `Caption` właściwość przycisku Win32 `ALT` i właściwość obrazu HTML są mapowane <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jedną właściwość, w widoku.  
  
Automatyzacja interfejsu użytkownika zapewnia pełną funkcjonalność obsługiwanych systemów operacyjnych Windows z programem .NET Framework (zobacz [.NET Framework wymagania systemowe](../get-started/system-requirements.md) lub wersje programu .NET Core, począwszy od .NET Core 3.0.  
  
 Dostawcy automatyzacji interfejsu użytkownika oferują pewną obsługę aplikacji klienckich microsoft active accessibility za pośrednictwem wbudowanej usługi mostkowania.  
  
<a name="Providers_and_Clients"></a>
## <a name="providers-and-clients"></a>Dostawcy i klienci  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ma cztery główne składniki, jak pokazano w poniższej tabeli.  
  
|Składnik|Opis|  
|---------------|-----------------|  
|Interfejs API dostawcy (UIAutomationProvider.dll i UIAutomationTypes.dll)|Zestaw definicji interfejsu, które są implementowane przez dostawców automatyzacji [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] interfejsu użytkownika, obiekty, które dostarczają informacji o elementach i odpowiadają na dane wejściowe programowe.|  
|Interfejs API klienta (UIAutomationClient.dll i UIAutomationTypes.dll)|Zestaw typów kodu zarządzanego, który umożliwia aplikacjom klienckim automatyzacji interfejsu użytkownika uzyskiwanie informacji o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] i wysyłanie danych wejściowych do formantów.|  
|UiAutomationCore.dll|Kod źródłowy (czasami [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nazywany rdzeniem), który obsługuje komunikację między dostawcami i klientami.|  
|UIAutomationClientsideProviders.dll|Zestaw dostawców automatyzacji interfejsu użytkownika dla standardowych formantów starszych. (formanty[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] mają [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]natywną obsługę dla .) Ta obsługa jest automatycznie dostępna dla aplikacji klienckich.|  
  
 Z punktu widzenia programisty istnieją dwa sposoby używania: [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]do tworzenia obsługi formantów niestandardowych (przy użyciu interfejsu API dostawcy) i tworzenia aplikacji, które używają [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rdzenia do komunikowania się z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementami (przy użyciu interfejsu API klienta). W zależności od ostrości należy zapoznać się z różnymi częściami dokumentacji. Więcej informacji na temat pojęć i praktyczną wiedzę na temat insydów można uzyskać w poniższych sekcjach.  
  
|Sekcja|Przedmiot|Grupy odbiorców|  
|-------------|--------------------|--------------|  
|[Podstawy automatyzacji interfejsu użytkownika](index.md) (ta sekcja)|Szeroki przegląd pojęć.|Wszystkie.|  
|[Dostawcy automatyzacji interfejsu użytkownika do kodu zarządzanego](ui-automation-providers-for-managed-code.md)|Przeglądy i tematy in jakże ułatwiające korzystanie z interfejsu API dostawcy.|Kontroluj deweloperów.|  
|[Klienci automatyzacji interfejsu użytkownika do kodu zarządzanego](ui-automation-clients-for-managed-code.md)|Przeglądy i tematy in jakże ułatwiające korzystanie z interfejsu API klienta.|Deweloperzy aplikacji klienckich.|  
|[Wzorce kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns.md)|Informacje o tym, jak wzorce kontroli powinny być implementowane przez dostawców i jakie funkcje są dostępne dla klientów.|Wszystkie.|  
|[Wzorzec tekstu automatyzacji interfejsu użytkownika](ui-automation-text-pattern.md)|Informacje o tym, jak wzorzec kontroli tekstu powinny być implementowane przez dostawców i jakie funkcje są dostępne dla klientów.|Wszystkie.|  
|[Typy kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-types.md)|Informacje o właściwościach i wzorcach kontroli obsługiwanych przez różne typy formantów.|Wszystkie.|  
  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono obszary nazw, biblioteki DLL, które je zawierają, oraz odbiorców, którzy ich używają.  
  
|Przestrzeń nazw|Biblioteki DLL, do których istnieją odwołania|Grupy odbiorców|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Deweloperzy klienta automatyzacji interfejsu użytkownika; używane do <xref:System.Windows.Automation.AutomationElement> znajdowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obiektów, rejestrowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń i pracy z wzorcami kontroli.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Deweloperzy dostawców automatyzacji interfejsu użytkownika [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]dla platform innych niż .|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Deweloperzy dostawców automatyzacji interfejsu użytkownika [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]dla platform innych niż; służy do implementacji wzorca kontroli TextPattern.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework (Ramwork prezentacji)|Deweloperzy dostawców automatyzacji [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]interfejsu użytkownika dla .|  
  
<a name="UI_Automation_Model"></a>
## <a name="ui-automation-model"></a>Model automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]udostępnia każdy element [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aplikacji klienckich jako . <xref:System.Windows.Automation.AutomationElement> Elementy są zawarte w strukturze drzewa, z pulpitu jako element główny. Klienci mogą filtrować nieprzetworzony widok drzewa jako widok kontrolny lub widok zawartości. Aplikacje mogą również tworzyć widoki niestandardowe.  
  
 <xref:System.Windows.Automation.AutomationElement>obiekty uwidaczniają [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wspólne właściwości elementów, które reprezentują. Jedną z tych właściwości jest typ formantu, który definiuje jego podstawowy wygląd i funkcjonalność jako pojedynczą rozpoznawalną jednostkę: na przykład przycisk lub pole wyboru.  
  
 Ponadto elementy uwidaczniają wzorce kontroli, które zapewniają właściwości specyficzne dla ich typów formantów. Wzorce kontroli również uwidaczniać metody, które umożliwiają klientom, aby uzyskać dalsze informacje na temat elementu i podać dane wejściowe.  
  
> [!NOTE]
> Nie ma korespondencji jeden do jednego między typami kontroli i wzorców kontroli. Wzorzec formantu może być obsługiwany przez wiele typów formantów, a formant może obsługiwać wiele wzorców kontroli, z których każdy udostępnia różne aspekty jego zachowania. Na przykład pole kombi ma co najmniej dwa wzorce kontroli: jeden, który reprezentuje jego zdolność do rozwijania i zwijania, a drugi, który reprezentuje mechanizm wyboru. Aby uzyskać szczegółowe dane, zobacz [Typy sterowania automatyzacją interfejsu użytkownika](ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]również dostarcza informacji do aplikacji klienckich za pośrednictwem zdarzeń. W przeciwieństwie do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] WinEvents, zdarzenia nie są oparte na mechanizmie emisji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]klienci rejestrują się dla powiadomień [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o określonych zdarzeniach i mogą żądać przekazywania określonych właściwości i informacji wzorca kontroli do ich programów obsługi zdarzeń. Ponadto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenie zawiera odwołanie do elementu, który go wywołał. Dostawcy mogą zwiększyć wydajność, podnosząc zdarzenia selektywnie, w zależności od tego, czy klienci nasłuchują.  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Przegląd właściwości automatyzacji interfejsu użytkownika](ui-automation-properties-overview.md)
- [Przegląd zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md)
- [Przegląd zabezpieczeń automatyzacji interfejsu użytkownika](ui-automation-security-overview.md)
